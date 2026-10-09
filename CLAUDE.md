# App-Ideen-Labor

> **Zweck:** Hier werden Ideen für Social-/Freundes-Games-Apps gesammelt, ausgearbeitet, bewertet und per Prototyp getestet, bis eine davon gebaut wird. Ziel ist eine Idee, die Spaß macht, sich über Freunde verbreitet und profitabel sein kann.
> **Aktuelle Phase: Ideenfindung.** Es wird noch nicht gebaut (außer Wegwerf-Prototypen in `prototypes/`).

Gemeinsamer Nenner bisher: Spiele mit und gegen Freunde, mobile, kurze Sessions, Gründe zum Wiederkommen.

## Ordner
```
ideas/          Eine Datei pro Idee + Index (README.md) + _TEMPLATE.md
ideas/bausteine/  Ideenübergreifende Features (keine eigene App, in mehrere Ideen einbaubar)
knowledge/      Ideenübergreifendes Wissen: Bewertungsraster, Mechanik-Baukasten, Referenzen, Monetarisierung/Recht
prototypes/     Wegwerf-Prototypen zum Spaß-Testen (meist eine HTML-Datei, kein Backend)
docs/           Technik: DECISIONS.md (alle Entscheidungen), ARCHITECTURE.md (Entwurf für Idee 01)
.claude/        Agent game-designer, Skills (aktuell auf Idee 01 zugeschnitten: new-game, daily-content, db-change)
```

## Arbeitsweise bei Ideen
- **Idee erfassen:** Der User kann Ideen mit `knowledge/app-brief-vorlage.md` ausgefüllt liefern. Offene `?`-Felder gezielt nachfragen, nicht raten.
- **Neue Idee vom User:** neue Datei nach `ideas/_TEMPLATE.md`. Originalidee wörtlich bzw. sinngemäß unter "Originalidee" erhalten, eigene Gedanken unter "Weitergedacht". Index in `ideas/README.md` ergänzen.
- **Ergänzung zu bestehender Idee:** in die passende Datei schreiben, Stand-Datum aktualisieren.
- **Ehrlich sein:** Gegenvorschläge, Risiken (Recht, Glücksspiel, Content-Aufwand, Cheats) und "macht das wirklich Spaß?" offen ansprechen. Kompakt antworten.
- **Wissen wiederverwenden:** Allgemeingültige Erkenntnisse (Mechaniken, Referenzen, Recht) nach `knowledge/` schreiben, nicht nur in die Idee. Vorher dort nachsehen.
- **Bewerten:** ausgearbeitete Ideen nach `knowledge/bewertung.md` punkten, Score in den Index.
- **Spaß testen statt diskutieren:** Wenn eine Idee vielversprechend ist, einen Prototyp in `prototypes/NN-name/` vorschlagen.
- Für Spieldesign-Fragen kann der Agent `game-designer` genutzt werden.
- Produkt- oder Technikentscheidungen kurz in `docs/DECISIONS.md` festhalten.

## Default-Stack (vorläufig, gilt für die Idee, die gebaut wird)
- **App:** Expo (neuestes SDK) + Expo Router + TypeScript (strict), iOS und Android zuerst
- **UI:** React Native, Reanimated, Gesture Handler, `@shopify/react-native-skia`, expo-haptics
- **State/Data:** TanStack Query (Server-State), Zustand (lokaler Game-State)
- **Backend:** Supabase (Auth, Postgres + RLS, Realtime, Storage, Edge Functions, pg_cron)
- **Push:** expo-notifications · **Build:** EAS · **Tests:** Jest + RNTL, Game-Logik als reine TS-Funktionen, E2E später Maestro
- Idee-spezifische Struktur und Datenmodell: siehe `docs/ARCHITECTURE.md` (aktuell Entwurf für Idee 01)

## Harte Regeln (sobald gebaut wird, für jede Idee)
- **Server-authoritative Scoring:** Scores und Run-Ergebnisse nur serverseitig berechnen bzw. nachrechnen. Dem Client nie Scores glauben.
- **RLS auf jeder Tabelle**, ohne Ausnahme.
- Zeit immer in **UTC** speichern, Streak-Logik nur serverseitig.
- Keine Secrets im Code. `.env*` nicht lesen oder committen. Im Client nur `EXPO_PUBLIC_*`.
- UGC braucht von Anfang an Melden und Blockieren. DSGVO: Account-Löschung in der App.
- Kein Pay-to-win, keine bezahlten Zufalls-Packs (siehe `knowledge/monetarisierung-recht.md`).
- UI-Texte auf Deutsch, über i18n-Keys (`src/i18n/`), nicht hardcoded.

## Konventionen (Code)
- Funktionale Komponenten, named exports, keine `any`. Komponenten `PascalCase.tsx`, sonst `kebab-case.ts`
- Game-Logik ohne React und ohne IO (testbar, in Deno-Edge-Functions wiederverwendbar)
- Kleine Commits mit Conventional Commits
- Bei Expo/RN-Fragen zuerst die Expo-Skills nutzen statt aus dem Gedächtnis zu arbeiten
- Vor dem Commit `/code-review`, bei Auth, RLS oder Edge Functions zusätzlich `/security-review`
