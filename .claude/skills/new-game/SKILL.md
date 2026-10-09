---
name: new-game
description: Legt ein neues Minispiel/Rätsel nach dem Game-Contract an (definition, generate, validate, Game.tsx, Result.tsx, Tests, Registry). Nutzen, wenn ein neues Spiel, Rätsel oder Daily-Format hinzugefügt werden soll.
argument-hint: <game-id> [kategorie: score|creative|social|duel]
---

# Neues Spiel anlegen: $ARGUMENTS

Lies zuerst `CLAUDE.md` (Abschnitt Game-Contract), `ideas/01-daily-challenges.md` (Spielkatalog, Scoring) und ein bestehendes Spiel in `src/games/` als Vorlage.

## 1. Design klären (kurz, vor dem Code)
Halte in 5–8 Zeilen fest: Ziel des Spiels, Dauer (Ziel: 1–3 Min.), Kategorie, wie `rawScore` entsteht, wie er auf 0–100 normalisiert wird, warum es gleich fair für alle ist (Seed), und welcher Cheat naheliegt und wie wir ihn verhindern. Bei Unklarheit nachfragen, sonst weitermachen.

## 2. Dateien in `src/games/<id>/`
- `definition.ts`: `GameDefinition` mit `id`, `name` (i18n-Key), `category`, `durationSec`, `scoring`
- `generate.ts`: `generate(seed)` deterministisch, nur mit `src/lib/rng` (seeded), **nie** `Math.random`/`Date`
- `validate.ts`: pure Funktion, keine Imports aus React/Expo/Supabase (muss in Deno laufen)
- `Game.tsx`: UI, ruft `onSubmit(submission)`, keine DB-Zugriffe; Haptics bei Erfolg/Fehler; Komponenten aus `src/ui/`
- `Result.tsx`: eigenes Ergebnis vs. Freunde (bekommt `results[]` als Props)
- `__tests__/generate.test.ts`: gleicher Seed → gleiches Puzzle; verschiedene Seeds → verschieden; Puzzle ist lösbar
- `__tests__/validate.test.ts`: korrekte Lösung, falsche Lösung, manipulierte Submission, Grenzwerte des Scorings

## 3. Registrieren
- In `src/games/registry.ts` eintragen
- i18n-Keys in `src/i18n/de.json` ergänzen
- Falls Inhalte nötig (Wortlisten, Prompts): über Skill `daily-content` in `content/<id>/`

## 4. Prüfen
`npm run typecheck && npm run lint && npm test -- src/games/<id>` und das Spiel einmal im Simulator spielen (Expo-Skill nutzen). Kurz berichten: Design-Zusammenfassung, Dateien, Testergebnis.
