# Entscheidungen (ADR-light)

Format: `## YYYY-MM-DD: Titel` · Kontext · Entscheidung · Konsequenz. Neue Einträge oben.

## 2026-10-09: Ordner wird zum Ideen-Labor
- **Kontext:** Idee 01 wirkt noch nicht spaßig genug, weitere Ideen (02, 03) kommen dazu. Der Ordner war auf eine einzige App zugeschnitten.
- **Entscheidung:** Ordner = Ideensammlung + Wissensbasis (`knowledge/`) + Wegwerf-Prototypen (`prototypes/`). Stack und harte Regeln gelten als Default für die Idee, die später gewählt wird. Das Daily-Spezifische steht in `docs/ARCHITECTURE.md`.
- **Konsequenz:** Ideen werden mit einem gemeinsamen Raster bewertet und per Prototyp getestet, bevor gebaut wird.

## 2026-10-09: Stack Expo + Supabase
- **Kontext:** Solo bzw. kleines Team, iOS und Android gleichzeitig, braucht Realtime, Auth und Push. Schnell iterieren ist wichtiger als native Perfektion.
- **Entscheidung:** Expo (Router, EAS) + Supabase (Postgres/RLS, Edge Functions, Realtime). Skia für Zeichnen und Spiele.
- **Konsequenz:** Ein TS-Codebase für App und Game-Logik, offizielle Claude-Skills und MCP für beides verfügbar. Lock-in bei Supabase ist akzeptabel (Postgres bleibt portabel).

## 2026-10-09: Server-authoritative Scoring
- **Kontext:** Ranglisten und Streaks sind sinnlos, wenn Cheaten leicht ist.
- **Entscheidung:** Validierung und Score nur in Edge Functions, Zeitmessung über Server-Timestamps.
- **Konsequenz:** Game-Logik muss als pures TS geschrieben werden, damit sie geteilt werden kann.
