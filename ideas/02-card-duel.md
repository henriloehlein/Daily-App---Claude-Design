# Idee 02: Kategorie-Kartenduell (Arbeitstitel "Deckduell")

> Status: 💡 Rohidee, wird ausgearbeitet · Stand 2026-10-09

## Pitch in einem Satz
**Autoquartett trifft Pokémon TCG Pocket als Daily-Duell:** Man wählt Lieblingskategorien (Panzer, Supersportwagen, Haie, Dinos, Kampfjets …), öffnet jeden Tag ein Gratis-Pack, füllt sein Sammelalbum und schlägt Freunde in kurzen Stat-Duellen.

## Originalidee (Henri)
- Täglicher Duell-Rhythmus wie bei Idee 01
- Kategorien frei wählbar: Fahrzeuge, Tiere, bestimmte Fahrzeuge (z. B. Panzer) …
- Trading-Card-Game innerhalb dieser Kategorien mit sehr einfachen Stats
- Karten gegeneinander antreten lassen und sich gegenseitig besiegen
- Gleichzeitig ein **Sammelalbum** für alle Karten

## Weitergedacht

### Daily Loop (ca. 3 Min.)
1. **Pack öffnen:** 1 Gratis-Pack pro Tag (5 Karten), mit schöner Öffnungs-Animation und Haptik. Das ist der stärkste tägliche Hook (Beleg: TCG Pocket).
2. **Daily-Duell:** gegen einen Freund oder die "Duell-Gruppe". Async, beide spielen, wann sie wollen.
3. **Album:** Neue Karten einkleben und Set-Fortschritt sehen ("Haie 23/40").
4. **Reveal:** Duell-Ergebnis, Flamme 🔥 für den Freundes-Streak.

### Duell-Mechanik: Vorschläge
Klassisches Quartett ist reines Glück. Es braucht eine kleine, aber echte Entscheidung.
- **A) Blind-Pick, Best of 5 (Favorit):** Das Daily legt 5 Stat-Runden fest (Seed, z. B. "Tempo, Gewicht, Alter, Seltenheit, Tempo"). Man sieht die Reihenfolge und verteilt 5 Karten aus seinem Deck auf die Runden. Der Gegner tut dasselbe blind. Danach animiertes Aufdecken Runde für Runde. Taktik: Wo setze ich meine Ass-Karte ein?
- **B) Quartett klassisch async:** Wer am Zug ist, wählt den Stat, 1 Zug pro Tag. Läuft über mehrere Tage, eher wie ein Brieffreund-Duell.
- **C) Draft:** Beide ziehen aus einem gemeinsamen Daily-Pool. Fair auch für Neulinge ohne große Sammlung.

### Kategorien und Stats
- **Echte Dinge mit echten Daten** (Höchstgeschwindigkeit, Gewicht, PS, Baujahr, Länge, Lebenserwartung). Man lernt nebenbei etwas, und der Stammtisch-Effekt ("Wusstest du, dass …") ist stark.
- **Stat-Quellen:** Wikidata (CC0, gut für Fahrzeuge und Tiere) plus Kuratierung
- **Kategorie-übergreifende Duelle** ("Hai vs. Panzer"): Jede Kategorie bekommt 4–5 **Universal-Stats** (Tempo, Kraft, Größe, Ausdauer, Seltenheit) als 1–100-Wert, abgeleitet aus den echten Daten. Auf der Karte stehen beide (echter Wert plus Balken).
  → Absurde Matchups sind lustig und teilbar. Klären: Ist das zu unfair oder gerade der Spaß?

### Sammeln
- Seltenheiten: Common / Rare / Epic / Legendary sowie **Holo-/Shiny-Varianten** (Gyro-Tilt-Effekt mit Skia)
- **Sets** innerhalb von Kategorien ("WW2-Panzer", "90er-Supercars", "Tiefsee"). Belohnung für ein komplettes Set (Album-Seite in Gold, Titel, Profil-Badge)
- Duplikate werden zu Upgrade-Material (Karte leveln, Stats +) oder Tauschware
- **Tauschen mit Freunden:** sehr social, braucht aber Regeln gegen Ausnutzen (z. B. nur gleiche Seltenheit)

### Verknüpfung mit Idee 01 (optional)
Ein Daily-Mini-Quiz zur Kategorie ("Höher oder tiefer: Wer ist schneller?") bringt Bonus-Packs. Das nutzt dieselben Kartendaten.

## Risiken / offene Punkte
- ⚠️ **Lootboxen:** Bezahlte Zufalls-Packs sind rechtlich heikel (Belgien verboten, in DE wirkt es auf die USK-Einstufung, EU-Regulierung kommt). → Packs nur verdienen, Monetarisierung über Kosmetik, Album-Themes oder Abo.
- ⚠️ **Marken/IP:** Echte Automarken, Modellnamen und Logos können Lizenzfragen auslösen. Tiere, Dinos und historische Militärfahrzeuge sind unkritischer. **Bilder:** einheitlicher eigener Illustrationsstil (z. B. KI plus Nachbearbeitung) statt Fotos. Das sorgt für einen erkennbaren Look und vermeidet Lizenzprobleme.
- **Content-Menge:** Pro Kategorie werden mindestens ca. 60–100 Karten zum Start gebraucht. Pipeline: Wikidata → Stats → Universal-Stats → Bild → Review
- **Neulinge vs. Veteranen:** Große Sammlungen dominieren → Matchmaking, Deck-Limits oder Draft-Modus (C)
- **Kategorie-Wahl:** Darf jeder alles wählen, oder schaltet man Kategorien frei?

## MVP-Skizze
1 Kategorie (Vorschlag: **Tiere**, weil breit, IP-frei und kindgerecht, oder **Supercars**, falls Marken lösbar) · ca. 80 Karten · Daily-Pack · Album · Duell-Modus A gegen Freunde · Freundes-Streak

## Erste Einschätzung
Mehr "Ich will morgen wiederkommen" als Idee 01: Sammeln plus Pack-Öffnen plus Besitz sind starke Motivatoren. Dazu ein klares Alleinstellungsmerkmal (eigene Nische wählen) und gute Teilbarkeit (Karten-Screenshots, absurde Duelle). Größte Arbeit: Content-Pipeline und Balancing.

## Passende Bausteine
- [Duell-Intro](bausteine/duell-intro.md): Charakter am Tisch mit Face-off-Emote vor dem Duell
