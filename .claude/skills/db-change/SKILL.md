---
name: db-change
description: Sicherer Ablauf für Datenbankänderungen in Supabase - neue Migration, RLS-Policies, Indizes, Types neu generieren, testen. Nutzen bei jeder Schema-, Policy- oder Funktionsänderung in Postgres.
argument-hint: <beschreibung der änderung>
---

# DB-Änderung: $ARGUMENTS

1. Lies `docs/ARCHITECTURE.md` (Datenmodell, RLS-Kernregel) und die letzten Migrationen in `supabase/migrations/`.
2. `npx supabase migration new <snake_case_name>` und **nur** in diese neue Datei schreiben. Bestehende Migrationen werden nie geändert.
3. Pflicht in jeder Migration:
   - `alter table ... enable row level security;` + explizite Policies für select/insert/update/delete
   - Policies mit `(select auth.uid())` statt `auth.uid()` (Performance)
   - Indizes auf Foreign Keys und Spalten, die in Policies verwendet werden
   - `security definer`-Funktionen nur mit `set search_path = ''`
   - Streak- und Score-Updates nur in Funktionen/Edge Functions, nicht per Client-Policy erlauben
4. Nutze den Skill `supabase-postgres-best-practices` bzw. das Supabase-Plugin für Review.
5. `npx supabase db reset`, danach Types regenerieren (`npx supabase gen types typescript --local > src/lib/database.types.ts`)
6. RLS testen: als User A, als Freund B und als Fremder C. Prüfen, ob "play to see" gilt (siehe ARCHITECTURE.md). Tests in `supabase/tests/` (pgTAP) ergänzen.
7. Bei Remote-Deploy (`db push`) **immer** vorher fragen.
