# Daily App (Arbeitstitel)

> **Aktuelle Phase: Ideenfindung.** Es wird noch nicht gebaut. Ideen stehen in [ideas/](ideas/README.md), eine Datei pro Idee, mit dem Index in `ideas/README.md`.
> Neue Ideen oder Ergänzungen vom User: in die passende Idee-Datei schreiben (Originalidee wörtlich erhalten, eigene Gedanken unter "Weitergedacht") und den Index aktualisieren. Kompakt antworten, Gegenvorschläge und Risiken offen nennen.
> Alles ab "Stack" ist ein vorläufiger Entwurf aus Idee 01. Er gilt erst, wenn eine Idee ausgewählt ist.

Gemeinsamer Nenner aller Ideen: Social-App mit täglichem Rhythmus, Duellen gegen Freunde und 🔥-Streaks.
Technik-Entwurf: [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) · Entscheidungen: [docs/DECISIONS.md](docs/DECISIONS.md)

## Stack
- **App:** Expo (neuestes SDK) + Expo Router + TypeScript (strict), iOS und Android zuerst, Web optional
- **UI:** React Native, Reanimated, Gesture Handler, `@shopify/react-native-skia` (Zeichnen und Game-Rendering), expo-haptics
- **State/Data:** TanStack Query (Server-State), Zustand (lokaler Game-State)
- **Backend:** Supabase (Auth, Postgres + RLS, Realtime, Storage für Zeichnungen, Edge Functions, pg_cron für den Daily-Drop)
- **Push:** expo-notifications
- **Tests:** Jest + React Native Testing Library; Game-Logik als reine TS-Funktionen mit Unit-Tests; E2E später mit Maestro
- **Build/Release:** EAS Build / Submit / Update

## Befehle
(Werden nach dem Scaffold angelegt; neue Befehle hier eintragen.)
- `npx expo start`: Dev-Server
- `npm run typecheck` / `npm run lint` / `npm test`: vor jedem "fertig" ausführen
- `npx supabase start` / `npx supabase db reset`: lokales Backend
- `npx supabase gen types typescript --local > src/lib/database.types.ts`: nach jeder Migration

## Struktur
```
app/                 Expo Router Screens: (auth)/, (tabs)/today, friends, profile
src/games/<id>/      Ein Ordner pro Spiel (siehe Game-Contract unten)
src/games/registry.ts  Liste aller Spiele, einzige Stelle zum Registrieren
src/features/        streaks/, scoring/, friends/, feed/, notifications/
src/lib/             supabase client, database.types.ts, seed/rng utils
src/ui/              Design-System (Tokens, Komponenten)
supabase/migrations/ SQL-Migrationen (nie bestehende ändern, nur neue anlegen)
supabase/functions/  Edge Functions (submit-result, daily-drop, ...)
content/             Kuratierte Inhalte (Prompts, Fragen) als JSON
```

## Game-Contract (wichtigste Architekturregel)
Jedes Spiel ist ein Modul `src/games/<id>/` mit:
- `definition.ts`: `id`, `name`, `category` (`score` | `creative` | `social` | `duel`), `durationSec`, `scoring`
- `generate.ts`: `generate(seed: string) => Puzzle`. **Deterministisch.** Gleicher Seed bedeutet gleiches Rätsel für alle.
- `validate.ts`: `validate(puzzle, submission) => { valid, rawScore }`. Pure Funktion, läuft auch in der Edge Function.
- `Game.tsx`: die UI. Sie bekommt `puzzle` und gibt über `onSubmit(submission)` das Ergebnis zurück. Sie schreibt nie selbst in die DB.
- `Result.tsx`: Vergleichsansicht (eigenes Ergebnis neben denen der Freunde)
- `__tests__/`: Tests für generate (Determinismus) und validate
Neue Spiele immer mit dem Skill `/new-game` anlegen.

## Harte Regeln
- **Server-authoritative Scoring:** Scores werden nur in der Edge Function `submit-result` berechnet (`validate` + Zeit aus Server-Timestamps). Dem Client nie Scores glauben.
- **RLS auf jeder Tabelle**, ohne Ausnahme. Ergebnisse von Freunden sind erst lesbar, wenn der eigene Eintrag für dieses Daily existiert.
- Normalisierte Scores liegen bei 0–100, damit man Spiele vergleichen kann (siehe ideas/01-daily-challenges.md → Scoring).
- Zeit und Tage immer in **UTC** speichern. Der Daily-Tag kommt aus der Zeitzone des Users (`daily_date`), und Streak-Logik läuft nur serverseitig.
- Keine Secrets im Code. `.env*` nicht lesen oder committen. Im Client nur `EXPO_PUBLIC_*`.
- UGC (Zeichnungen, Texte) braucht von Anfang an Melden und Blockieren (App-Store-Pflicht). Dazu kommt DSGVO: Account-Löschung in der App.
- UI-Texte auf Deutsch, aber über i18n-Keys (`src/i18n/`), nicht hardcoded.

## Konventionen
- Funktionale Komponenten, named exports, keine `any`. Dateinamen: Komponenten `PascalCase.tsx`, sonst `kebab-case.ts`
- Game-Logik ohne React und ohne IO, damit sie testbar und in Deno (Edge Functions) wiederverwendbar ist
- Komponenten aus `src/ui/` verwenden, Farben und Abstände nur über Tokens
- Kleine, fokussierte Commits mit Conventional Commits (`feat(games/sudoku): ...`)

## Workflow
1. Größere Features: erst **Plan Mode**, Plan gegen die gewählte Idee in ideas/ und ARCHITECTURE.md prüfen
2. Implementieren, dann `typecheck`, `lint`, `test`
3. DB-Änderungen über den Skill `/db-change` (Migration, RLS, Types, Test)
4. Vor dem Commit: `/code-review`. Bei Auth, RLS oder Edge Functions zusätzlich `/security-review`
5. Neue Architektur- oder Produktentscheidung: kurzer Eintrag in `docs/DECISIONS.md`
6. Bei Expo/RN-Fragen zuerst die Expo-Skills nutzen (`expo-router`, `expo-native-ui`, `expo-animation`, …) statt aus dem Gedächtnis zu arbeiten
