# Idee 03: Duo-Roguelite / Incremental (Arbeitstitel "Rubbel-Rivalen")

> Status: 💡 Rohidee, ausgearbeitet · Stand 2026-10-09

## Pitch in einem Satz
**Luck be a Landlord / Balatro trifft Coin Master, aber fair unter Freunden:** Kurze Runs, in denen man Lose rubbelt oder Automaten zieht, zwischendurch Upgrades kauft und die Zahlen explodieren lässt. Freunde spielen **denselben Seed** und vergleichen sich, und zwischen den Runs wächst eine dauerhafte Sammlung an Freischaltungen.

## Originalidee (Henri)
- Weg vom Daily-Konzept, aber weiterhin eine Freundes-Games-App
- Vom Gefühl her wie Cookie Clicker oder die vielen Roguelites, in denen man Rubbellose macht oder an Spielautomaten zieht, dann die Chance oder den Wert upgradet und zum nächsten Los oder Automaten geht
- Immer Upgrades kaufen, immer mehr bekommen, coolere Sachen freischalten
- Das Ganze in **Duo-Form**
- Kernproblem: Als Freundes-Duell gewinnt bei Cookie Clicker einfach, wer länger spielt. Rundenbasiert macht es dagegen keinen Spaß, weil man nicht grinden und süchtig werden kann.
- Frage: Welche Mechanik macht Duell-Roguelites als Duo mobile-tauglich?

## Weitergedacht

### Das Kernproblem genauer
Ein Duell ist nur fair, wenn es **Entscheidungen** vergleicht und nicht **Spielzeit**. Grind macht aber nur Spaß, wenn Spielzeit sich lohnt. Beides geht zusammen, wenn man die zwei Ebenen trennt:

| Ebene | Was wächst | Wie lange | Fair? |
|---|---|---|---|
| **Run** (Roguelite) | Zahlen explodieren innerhalb eines Runs, alles startet bei 0 | 3–8 Min. | Ja: gleicher Seed, gleiche Startbedingungen |
| **Meta** (Incremental) | Freischaltungen, neue Automaten/Lose, Kosmetik, Sammlung | unbegrenzt grindbar | Ja, solange Meta **Breite** gibt (mehr Optionen), nicht **Höhe** (mehr Startkapital) |

So machen es Balatro und Luck be a Landlord: Wer viel spielt, wird besser und hat mehr Optionen, startet aber jeden Run bei null.

### Mechanik-Baukasten gegen "Wer länger spielt, gewinnt"
1. **Seed-Duell (Effizienz statt Menge):** Beide spielen exakt denselben Run (gleiche Lose, gleiche Shop-Angebote). Gewertet wird das Ergebnis nach einer festen Anzahl Züge ("50 Lose") oder wie weit man kommt. Mehr Spielzeit hilft nur indirekt über Skill.
2. **Loadout-Limit:** Man darf nur 3–5 seiner Freischaltungen in einen Duell-Run mitnehmen. Grind gibt Auswahl, keine rohe Stärke. Alternativ: Ranked-Modus, in dem beide nur den gemeinsamen Basis-Pool haben.
3. **Quota-Druck (Roguelite-Spannung):** Wie die Miete in Luck be a Landlord oder der Blind in Balatro: Nach jeder Runde muss man eine steigende Summe erreichen, sonst ist der Run vorbei. Das erzeugt echte Entscheidungen ("Upgrade jetzt oder Geld für die Quote sparen?").
4. **Ghost-Replay:** Nach dem eigenen Run sieht man den Run des Freundes als Kurve neben der eigenen ("Bei Los 31 hat Lisa den Multiplikator gekauft und dich überholt"). Das liefert Gesprächsstoff und Revanche-Lust.
5. **Co-op-Duo statt 1v1:** Zwei Freunde spielen als Team mit gemeinsamer Kasse und gemeinsamer Quote. Jeder hat eigene Züge und kann dem anderen Upgrades zuschieben. Hier ist Grind kein Problem, denn wer mehr spielt, hilft dem Team. Duos treten dann gegen andere Duos an (Freundeskreis-Liga).
6. **Sabotage und Geschenke (async):** Starke Runs erzeugen "Fluch-Lose" oder "Glücks-Lose", die im nächsten Run des Freundes auftauchen. Gedeckelt pro Tag, damit Vielspieler nicht dominieren.
7. **Energie/Tickets (Coin-Master-Modell):** Runs kosten Tickets, die sich über Zeit aufladen. Bewährt und sehr profitabel, begrenzt den Vorsprung von Vielspielern, fühlt sich aber schnell nach Pay-to-play an. Nur als Notlösung.
8. **Saison-Rennen mit Deckel:** Wöchentliches Rennen auf ein Ziel (z. B. "Erster bei 1 Mrd."), aber mit abnehmendem Ertrag pro Tag oder Catch-up-Bonus für den Zurückliegenden.

### Vorschlag: Kombination
- **Solo-Grind (das Suchtteil):** Endlos Runs spielen, Meta-Währung sammeln, neue Automaten-Typen, Los-Sorten, Symbole und Upgrade-Karten freischalten. Prestige-Gefühl über immer verrücktere Synergien, nicht über größere Startzahlen.
- **Freundes-Duell (das Social-Teil):** "Fordere Max heraus": Man spielt einen Seed-Run, der Freund bekommt denselben. Ergebnis mit Ghost-Kurve und Share-Karte. Async, kein Termin nötig. Loadout-Limit hält es fair.
- **Duo-Run (die Duo-Form):** Wöchentlicher Co-op-Run zu zweit mit gemeinsamer Quote. Bindung wie ein Freundes-Streak, aber mit gemeinsamem Ziel.
- **Optional live:** 3-Minuten-Speed-Duell in Echtzeit, beide sehen den Zähler des anderen steigen. Erst später, weil man dafür beide gleichzeitig online braucht.

### Run-Skizze (Rubbellos-Variante)
1. Start mit 10 Münzen und 1 einfachem Los-Stapel
2. Jedes Los kostet und zeigt beim Rubbeln Symbole. Symbole haben Werte und Synergien ("Kleeblatt verdoppelt benachbarte Münzen").
3. Nach je 10 Losen kommt der Shop: neue Los-Sorten, Symbol-Upgrades, "Glücks-Chance +5 %", Multiplikatoren
4. Danach eine Quote zahlen (steigt: 50 → 200 → 1.000 → …). Wer sie nicht schafft, beendet den Run.
5. Score = erreichte Runde plus Endsumme. Die Zahlen sollen absurd groß werden (Incremental-Gefühl).

Die Automaten-Variante (Luck be a Landlord / CloverPit) funktioniert genauso, nur mit Walzen statt Rubbelfeldern. Beide als Modi in einer App sind denkbar ("neue Automaten freischalten").

## Referenzen
- **Luck be a Landlord**, **CloverPit**: Slot-Roguelites mit Miete/Quote, sehr nah am Kern
- **Balatro**: Seeded Runs, Meta-Freischaltungen als Breite, gigantische Zahlen
- **Cookie Clicker**, Idle-Games: Incremental-Gefühl, Prestige
- **Coin Master**, **Monopoly Go**: Slot/Würfel plus Freunde angreifen und Geschenke senden. Belegen, dass dieses Genre mit Freunden riesige Umsätze macht. Monetarisieren aber über Energie und Glücksspielnähe.

## Risiken / offene Punkte
- ⚠️ **Simuliertes Glücksspiel:** Casino-Optik (Slots, Rubbellose) kann zu einer hohen Altersfreigabe führen (App Store 17+, USK-Bewertung von glücksspielähnlichen Elementen) und Werbung einschränken. Echtes Geld gegen Spins wäre faktisch Social Casino. → **Theme-Alternative prüfen:** gleiches Gefühl (Hebel ziehen, aufdecken, Zahlen explodieren), aber ohne Casino-Look, z. B. Schatzkisten, Kaugummiautomat, Angeln, Mine, Zauber-Kessel. Breitere Zielgruppe, weniger Regulierung.
- **Cheat-Risiko:** Seed-Runs lassen sich mit einem Bot oder Solver optimieren. → Run serverseitig nachrechnen (Replay der Entscheidungen, wie das Scoring in Idee 01), Seed erst beim Start ausliefern.
- **Balancing-Aufwand:** Synergien sind das Herz des Genres und brauchen viel Iteration. Gut: Alles ist pure Logik und lässt sich simulieren (Bots, die tausend Runs spielen).
- **Session-Länge:** Echte Roguelite-Runs dauern oft 20+ Min. Für Mobile auf 3–8 Min. kürzen, Pause und Fortsetzen jederzeit.
- **Unterscheidung vom Markt:** Solo-Slot-Roguelites gibt es schon. Das Alleinstellungsmerkmal muss klar der Freundes-Teil sein (Seed-Duell, Ghost, Duo-Run).

## Monetarisierung (ohne Glücksspiel-Falle)
- Rewarded Ads für einen zweiten Versuch oder ein Extra-Shop-Reroll (im Genre sehr akzeptiert)
- Kosmetik: Automaten-Skins, Rubbel-Effekte, Sounds, Profilrahmen
- Season-/Battle-Pass mit Kosmetik und neuen Freischaltungen (früher, nicht exklusiv)
- **Nicht:** bezahlte Spins oder Energie gegen Echtgeld

## MVP-Skizze
1 Run-Typ (Rubbellos **oder** Automat) · ca. 20 Symbole/Upgrades · Quota-System · Meta mit 10–15 Freischaltungen · Seed-Duell gegen Freunde mit Ghost-Kurve · Share-Karte. Duo-Co-op erst in v0.2.

**Vorher:** Spaß-Prototyp als Web-Prototyp (eine HTML-Datei, nur der Run, ohne Backend), um zu testen, ob 5 Minuten Rubbeln und Upgraden süchtig machen.

## Erste Einschätzung
Stärkstes "Ich will noch einen Run"-Gefühl aller bisherigen Ideen, und das Genre ist nachweislich profitabel. Die Kernfrage ist gelöst, wenn Runs bei null starten und Meta nur Breite gibt. Größte Risiken: Glücksspiel-Optik und dass man sich klar von Solo-Spielen abhebt. Die Logik ist rein und testbar, technisch also gut machbar.

## Passende Bausteine
- [Duell-Intro](bausteine/duell-intro.md): Charakter am Tisch mit Face-off-Emote vor dem Duell
