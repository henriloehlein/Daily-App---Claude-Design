---
name: daily-content
description: Erzeugt und prüft Content-Batches für Dailies (Zeichen-Prompts, Schätzfragen, Wortlisten, "Gleich gedacht"-Fragen, Impostor-Wörter) als JSON in content/. Nutzen, wenn neue Inhalte für Spiele gebraucht werden.
argument-hint: <game-id> <anzahl>
---

# Content generieren: $ARGUMENTS

1. Lies `content/<game-id>/schema.json` (falls nicht vorhanden: Schema zuerst vorschlagen und anlegen) und die bestehenden Einträge, um Duplikate zu vermeiden.
2. Erzeuge die gewünschte Anzahl Einträge. Qualitätsregeln:
   - Deutsch, jugendfrei, inklusiv, keine Marken oder realen Personen, nichts Politisches oder Religiöses
   - Schwierigkeit 1–3 als Feld setzen und gemischt verteilen
   - Schätzfragen: nur Fakten mit **verlässlicher Quelle** (Feld `source`); unsicher → weglassen
   - Zeichen-Prompts: in 30 s zeichenbar und für Freunde erratbar
   - Impostor-Wörter: Wort plus 2–3 verwandte Tarnbegriffe
3. In eine **neue** Datei `content/<game-id>/batch-YYYY-MM-DD.json` schreiben, bestehende Dateien nicht anfassen.
4. Gegen das Schema validieren (`npm run content:validate`, sobald vorhanden) und auf Duplikate prüfen (normalisierter Text).
5. Am Ende eine Stichprobe von 5 Einträgen zeigen, damit der Mensch sie reviewen kann.
