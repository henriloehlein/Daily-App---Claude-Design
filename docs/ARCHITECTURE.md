# Architektur

## Datenmodell (Entwurf)
```
profiles        (id = auth.uid, username unique, display_name, avatar_url, timezone, created_at)
friendships     (user_a, user_b, status: pending|accepted|blocked, created_at)  -- user_a < user_b
groups / group_members
dailies         (id, daily_date, game_id, seed, drop_at, content_ref)           -- 1 Zeile pro Tag (+ Bonus)
results         (id, daily_id, user_id, submission jsonb, raw_score, score, started_at, submitted_at, on_time)
                -- unique (daily_id, user_id)
attempts        (id, daily_id, user_id, started_at)                             -- Server-Startzeit, gegen Zeit-Cheats
votes           (result_id, voter_id, value)                                    -- creative games
streaks         (user_id, current, longest, last_daily_date, freezes)
friend_streaks  (user_a, user_b, current, last_daily_date)
reactions, reports, push_tokens
duels           (id, game_id, challenger, opponent, state jsonb, turn, status)
```

## RLS-Kernregel "play to see"
`results` von Freunden sind nur lesbar, wenn gilt:
`exists(select 1 from results r where r.daily_id = results.daily_id and r.user_id = auth.uid())` **und** eine Freundschaft besteht.

## Flows
**Daily-Drop:** `pg_cron` legt jeden Tag um 00:00 UTC die `dailies` für die nächsten Tage an (Seed = HMAC(secret, date+game)). Die Edge Function `daily-drop` verschickt die Pushes zu `drop_at` pro Zeitzone.

**Spielen:**
1. Client ruft `start-attempt` auf. Der Server speichert `started_at` und gibt das Puzzle zurück (der Seed bleibt serverseitig, solange es Lösungs-Leaks geben kann).
2. Client spielt lokal (`Game.tsx`).
3. Der Aufruf von `submit-result` startet `validate()` (geteilter TS-Code), berechnet Zeit und Score, schreibt `results` und aktualisiert Streaks transaktional.
4. Realtime-Subscription auf `results` der Freunde, damit der Feed live aktualisiert wird.

**Geteilter Code:** `src/games/*/generate.ts` und `validate.ts` sind reines TS ohne Dependencies. Edge Functions (Deno) importieren sie über einen Shared-Pfad bzw. ein Build-Script, damit es nur eine Quelle der Wahrheit gibt.

## Zeichnen
Skia-Canvas zeichnet Pfade als Vektoren (JSON: Punkte + Stroke). Das ist kleiner als PNG und man kann die Zeichnung als Replay animieren. Ein PNG-Thumbnail für Share und Feed liegt in Storage.

## Schach
`chess.js` für Regeln und Validierung, eigenes Board in Skia oder RN. Puzzles kommen aus der Lichess-Puzzle-DB (CC0), gefiltert nach Rating und vorab in `content/` importiert.

## Offline / Performance
- Puzzle beim Start lokal cachen. Submit wird bei Offline in eine Queue gelegt (Server-Zeit gilt ab `start-attempt`).
- Listen mit FlashList, Animationen mit Reanimated im UI-Thread.
