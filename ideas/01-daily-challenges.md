# Produkt: Daily Duel

## Kern-Idee
Ein kurzes tägliches Ritual (2–5 Minuten), das man mit Freunden teilt. Es kombiniert **Wordle** (ein gemeinsames Rätsel für alle, gut vergleichbar), **BeReal** (Drop zu einer überraschenden Uhrzeit, Ergebnisse der Freunde erst nach dem eigenen Spiel) und **Snapchat** (🔥-Streaks pro Freund).

## Core Loop
1. **Drop:** Täglich zu einer zufälligen Uhrzeit (zwischen 10 und 21 Uhr, gleich für alle in einer Zeitzone) kommt die Push-Nachricht "⚡ Daily ist da".
2. **Spielen:** 1 Haupt-Daily plus optional 1 Bonus-Spiel. Wer innerhalb von 60 Minuten spielt, bekommt den Bonus "On Time ⚡".
3. **Reveal:** Erst nach dem eigenen Spiel sieht man die Ergebnisse der Freunde (Feed, Vergleichsansicht, Reaktionen).
4. **Score + Streak:** Tagesrang unter Freunden, Wochen-Liga, Flammen.
5. **Hook für morgen:** "Max hat dich heute geschlagen. Revanche morgen?" sowie die Streak-Warnung am Abend.

## Spielkatalog (nach Vergleichsart)
| Kategorie | Wie verglichen | Beispiele |
|---|---|---|
| `score`: deterministisch | Gleicher Seed, Zeit/Fehler ergeben den Score | Mini-Sudoku 6×6, Wortgitter, Nonogramm, Mathe-Blitz, Memory, Reaktionstest, Schach-Puzzle ("Matt in 2", Lichess-Puzzle-DB, CC0) |
| `creative`: Peer-Voting | Freunde bewerten oder raten | Zeichnen nach Prompt (30 s), "Was ist das?" (Freunde raten die Zeichnung, beide bekommen Punkte), Meme-Caption |
| `social`: Gruppen-Spiel | Übereinstimmung oder Abstimmung | Impostor async (alle bis auf einen bekommen das Wort und geben einen Hinweis, dann wird abgestimmt), "Gleich gedacht" (Punkte, wenn man dasselbe antwortet wie Freunde), Schätzfrage (Nähe zum echten Wert), "Wer von uns …?" |
| `duel`: 1v1, selbst gewählt | Direkt gegeneinander | Beide wählen Schach (async, 1 Zug pro Tag oder Blitz-Puzzle), Sudoku-Race, Wort-Duell |

**Auswahl:** Das Haupt-Daily wird kuratiert und rotiert über die Woche (Mo: Logik, Di: Zeichnen, Mi: Wort, …), damit es abwechslungsreich bleibt. Duelle wählen beide Spieler gemeinsam aus dem Katalog.

## Scoring
- Jedes Spiel liefert einen `rawScore` und wird auf **0–100** normalisiert (z. B. Zeit-Perzentil über alle Spieler des Tages plus Fehlerabzug).
- Creative-Spiele werden über Votes (Ø Sterne oder Rate-Treffer) normalisiert.
- Tagespunkte = normalisierter Score + Boni (On Time +10, Streak-Multiplikator max. ×1.5).
- **Wochen-Liga** innerhalb der Freundesgruppe. Montags Reset und Badge für Platz 1.

## Streaks 🔥
- **Eigener Streak:** jeden Tag das Daily gespielt.
- **Freundes-Streak (Snap-Style):** beide haben am selben Tag gespielt. Die Flamme mit Zahl steht neben dem Freund, ⏳-Warnung, wenn er heute noch fehlt.
- **Streak-Freeze:** 1 pro Woche verdienbar, nicht kaufbar (damit es fair bleibt).
- Meilensteine: 7 / 30 / 100 / 365 Tage, mit Animation und teilbarer Karte.

## Social
- Freunde über Username, Invite-Link oder Kontakte (opt-in). Gruppen von bis zu 20 Personen (Friend Groups) für Liga und Social-Games.
- Reaktionen (Emoji) und kurze Kommentare auf Ergebnisse
- **Share-Karte** wie bei Wordle (Emoji-Grid / Bild) für Instagram und WhatsApp. Das ist der wichtigste Wachstumskanal.

## MVP (v0.1): klein und testbar
1. Auth (Apple, Google, E-Mail-OTP), Username, Profil
2. Freunde hinzufügen (Username + Invite-Link)
3. Daily-Drop + Push
4. **3 Spiele:** Mini-Sudoku (`score`), Zeichnen + Raten (`creative`), Schätzfrage (`social`, einfach)
5. Reveal-Feed + Vergleichsansicht
6. Eigener Streak + Freundes-Streak
7. Melden/Blockieren, Account löschen

**Später:** Schach-Duelle, Impostor async, Wochen-Liga, Share-Karten, Widgets (iOS Live Activity / Home-Widget mit Streak), Premium (Archiv, Extra-Spiele, Themes) über RevenueCat.

## Offene Fragen
- Name und Branding
- Drop global synchron oder pro Zeitzone? (Tendenz: pro Zeitzone, gleicher Seed pro `daily_date`)
- Altersfreigabe / Mindestalter (UGC-Moderation)

## Passende Bausteine
- [Duell-Intro](bausteine/duell-intro.md): nur im `duel`-Modus sinnvoll
