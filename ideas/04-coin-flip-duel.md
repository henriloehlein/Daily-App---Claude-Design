# Idee 04: Münzwurf-Duell (Arbeitstitel "Kopf oder Zahl")

> Status: 💡 Rohidee · Stand 2026-10-09

## Pitch in einem Satz
**Snapchat-Flammen trifft Münzwurf:** Mit jedem Freund läuft ein ewiges Duell. Jeden Tag wird eine Münze geworfen, und der Gesamtstand ("Max 14 : 11 Du") wird für immer mitgezählt.

## Originalidee (Henri)
- Eine Duell-App, in der man sich mit einem Freund duelliert
- Ganz simple Mechanik: Man wirft eine Münze
- Ähnlich wie die Snapchat-Flammen, nur dass man eine Münze wirft. Der Score wird gespeichert.
- Ab da kann man überlegen, ob man es ausbaut oder weitere Mechaniken einbaut
- Erst einmal als grundlegendes Gerüst

## Weitergedacht

### Core Loop (Annahme, siehe offene Fragen)
1. Pro Freund gibt es eine **Rivalität** mit Gesamtstand und 🔥-Streak.
2. **1 Wurf pro Tag und Freund.** Wer dran ist, ruft Kopf oder Zahl und wirft (Wisch-Geste nach oben oder Handy schnippen, mit Haptik und Sound).
3. Der Freund bekommt eine Push-Nachricht ("Max hat geworfen: Du verlierst, 14 : 11"). Am nächsten Tag ist er dran.
4. **Streak:** Die Flamme wächst, solange täglich geworfen wird. Wird ein Tag verpasst, gibt es ⏳ und danach ist die Flamme weg.

### Warum das funktionieren kann
- **Kein Skill = kein Frust:** Jeder kann gegen jeden gewinnen. Es geht um das Ritual und die Verbindung, wie bei Snapchat-Flammen. Der Gesamtstand liefert Sticheleien ("Ich führe seit 200 Tagen").
- **Extrem schnell:** 3 Sekunden pro Tag, niedrigste Einstiegshürde aller Ideen.
- **Wachstum eingebaut:** Ohne Freund kein Spiel, also lädt jeder ein.
- **Sehr schnell gebaut:** Gut als erstes Launch-Projekt, um Store-Release, Push, Streaks und Freundes-System zu lernen. Diese Teile lassen sich später für 01–03 wiederverwenden.

### Ausbau-Optionen (später, nach Test)
- **Home-Widget** (wie Locket): Zeigt "Max 14 : 11 · du bist dran 🔥 37" und lässt sich direkt vom Homescreen werfen. Wahrscheinlich der stärkste Hebel.
- **Einsätze ohne Geld:** Vor dem Wurf eine Wette festlegen ("Verlierer zahlt den Kaffee", "Verlierer muss ein Foto posten"). Erzeugt Geschichten und Gesprächsstoff. Die App verwaltet nur den Text, kein Geld.
- **Double or Nothing:** Der Verlierer darf einmal pro Woche "verdoppeln". Ein Wurf entscheidet dann über 2 Punkte.
- **Münzen sammeln und customizen:** Münz-Skins, Würfe mit Effekten, seltene Münzen über Streak-Meilensteine. Das ist die naheliegende Monetarisierung.
- **Wurf-Animation als Signature Moment**, verbindbar mit dem [Duell-Intro](bausteine/duell-intro.md) (Gegner gegenüber am Tisch, Münze fliegt).
- **Titel und Statistiken:** "Nemesis" (gegen wen du am häufigsten verlierst), "Glückspilz der Woche", längste Siegesserie.
- **Gruppen-Turnier:** K.-o.-Bracket mit Münzwürfen im Freundeskreis, eine Runde pro Tag.
- **Andere Mini-Duelle** neben der Münze: Schere-Stein-Papier (async, beide wählen verdeckt), Würfel, Karte ziehen. Das wäre ein sanfter Übergang zu mehr Mechanik.

## Referenzen
- **Snapchat-Flammen:** Streak pro Freund als Bindung
- **Locket:** extrem simple Social-App, deren Wachstum über das Home-Widget lief
- **BeReal:** minimaler Aufwand pro Tag als Ritual
- **Bestehende Coin-Flip-Apps:** Es gibt viele, aber ohne Freunde, Stand oder Streak. Die Lücke ist der soziale Teil.

## Risiken / offene Punkte
- ⚠️ **Wird es nach 2 Wochen langweilig?** Reiner Zufall ohne Entscheidung trägt sich nur über die Social-Ebene (Stand, Streak, Sticheleien, Einsätze). Das ist die große Wette dieser Idee und sollte früh mit Freunden getestet werden.
- **"Warum nicht einfach eine echte Münze?"** Die App bietet das, was die Münze nicht kann: Gedächtnis (Stand über Jahre), Ritual über Distanz, Streak, Widget.
- **Fairness/Vertrauen:** Der Wurf muss serverseitig entschieden werden, sonst kann man manipulieren. Bei 50/50 muss man das sichtbar machen ("fair geworfen", eventuell Statistik).
- **Glücksspiel:** Unkritisch, solange es nur Punkte gibt. Keine echten Geld-Einsätze über die App, keine bezahlten Zusatzwürfe mit Gewinnchance.
- **Monetarisierung schwach:** Wenig Spielzeit bedeutet wenig Werbefläche. Bleiben Kosmetik (Münzen, Effekte) und eventuell ein Abo. Daher eher als Einstiegs- oder Lernprojekt oder als Feature in einer größeren App denkbar.

### Offene Fragen an Henri
- Wirft jeder einmal pro Tag (2 Würfe täglich) oder abwechselnd (1 Wurf täglich)?
- Ist es ein Duell 1:1 pro Freund oder auch in Gruppen?
- Zählt nur der Gesamtstand, oder gibt es Saisons mit Reset?
- Eigene App oder Feature in einer der anderen Ideen?

## Monetarisierung
Münz-Skins, Wurf-Effekte, Widget-Themes. Optional ein Abo (alle Münzen, Statistiken). Rewarded Ads höchstens für einen Streak-Retter.

## MVP-Skizze
Login · Freund per Link einladen · Rivalität mit Stand und Flamme · 1 Wurf pro Tag mit Animation und Haptik · Push an den Freund · Streak-Warnung am Abend. **Vorher:** klickbarer Prototyp der Wurf-Animation, um zu prüfen, ob der Moment sich gut anfühlt.

## Bewertung
Steht noch aus.

## Erste Einschätzung
Die simpelste und am schnellsten baubare Idee. Ihr Erfolg hängt komplett an der Social-Ebene, nicht am Spiel. Stark als Lernprojekt oder als "Feature-Kern", der später Mini-Duelle dazubekommt. Ob es allein trägt, entscheidet ein Test mit 5–10 Freunden über zwei Wochen.
