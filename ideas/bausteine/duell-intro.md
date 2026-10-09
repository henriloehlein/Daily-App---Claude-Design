# Baustein: Duell-Intro (Charakter + Face-off-Animation)

> Status: 💡 Rohidee · Stand 2026-10-09 · **Ideenübergreifend**, also keine eigene App, sondern ein Feature für jede Idee mit Duellen

## Originalidee (Henri)
- Geistesblitz: eine charakteristische Animation, wenn man ein Spiel mit einem Freund startet
- Funktioniert wie ein Loading Screen: Man sitzt aus der **Ego-Perspektive an einem Tisch** und sieht den Gegner gegenüber
- Dann läuft eine **2–3-Sekunden-Animation** des Gegners, zum Beispiel:
  - schlägt die Faust in die andere Hand
  - macht Schattenboxen
  - macht ein V mit zwei Fingern zu den eigenen Augen und zeigt dann auf den anderen ("Ich sehe dich")
- Danach geht es ins Spiel
- Ausbaubar: Charakter customizen und Duell-Animationen auswählen
- Ziel: dem Game einen eigenen Charakter geben, etwas, das Leute im Kopf behalten
- Für die Roguelite-Idee vielleicht nicht optimal, eher für Daily Challenges, aber als Aspekt für alle festhalten

## Weitergedacht

### Warum das stark sein kann
- **Wiedererkennung:** Ein fester "Signature Moment" macht eine App unverwechselbar (vgl. das Pack-Öffnen bei TCG Pocket oder den Victory-Screen bei Clash Royale). Er zeigt sich auch gut in Werbe-Clips und auf TikTok.
- **Macht ein async Duell persönlich:** Der Freund ist nicht live da, aber sein Charakter mit *seinem* gewählten Emote sitzt dir gegenüber. Das fühlt sich an wie "gegen Max spielen" und nicht wie "gegen eine Zahl".
- **Kosmetik-Monetarisierung ohne Pay-to-win:** Emotes, Outfits und Tische lassen sich gut verkaufen (Fortnite, Brawl Stars). Das passt zu den roten Linien in [monetarisierung-recht.md](../../knowledge/monetarisierung-recht.md).

### Erweiterungen (später)
- **Antwort-Emote:** Gegner provoziert, dein Charakter reagiert mit deinem gewählten Konter (Augenrollen, Gähnen, Fingerknacken). Daraus wird ein kleiner Dialog.
- **Outro:** Sieger-Emote und Verlierer-Reaktion nach dem Duell. Das bietet sich als teilbarer Clip an ("Max hat mich mit dem Tanz gedemütigt").
- **Tisch passt zum Spiel:** Spieltisch bei 02 (Karten liegen bereit), Automaten-Bank bei 03, Schreibtisch bei 01.
- **Freischaltbare Emotes** als Belohnung für Streaks oder Meilensteine (verbindet sich mit Retention).

### Wo es passt
| Idee | Passung | Wie |
|---|---|---|
| [01 Daily Challenges](../01-daily-challenges.md) | mittel | Nur im `duel`-Modus. Das Haupt-Daily ist solo, dort gibt es keinen Gegner. |
| [02 Kartenduell](../02-card-duel.md) | **sehr gut** | Zwei Spieler am Tisch sind beim Kartenspiel das natürliche Bild |
| [03 Duo-Roguelite](../03-duo-roguelite.md) | gut | Vor dem Seed-Duell gegenüber, beim Co-op-Duo nebeneinander an der Automaten-Bank (Fist-Bump statt Provokation) |

## Risiken / offene Punkte
- **Nervt beim 50. Mal:** Kürzer als 3 Sek., antippen zum Überspringen, nur einmal pro Duell. Idealerweise verdeckt es echte Ladezeit, statt künstlich zu warten.
- **Content-Aufwand explodiert:** Jede Animation mal jedes Outfit wird teuer. → 2D-Rigging statt 3D: **Rive** oder **Spine** erlauben austauschbare Körperteile/Outfits auf derselben Animation. Ego-Perspektive als illustrierte Szene (2.5D) statt echtem 3D.
- **Stil-Entscheidung früh treffen:** Der Charakter-Look prägt die ganze App (Branding). Gehört zur Namens-/Branding-Frage.
- **Performance auf Low-End-Android** testen (Rive läuft in React Native, Lottie ist eine leichtere Alternative ohne Customizing).

## MVP-Skizze
1 Basis-Charakter mit 3–4 Farben/Accessoires · 3 Intro-Emotes (Faust in Hand, Schattenboxen, "Ich sehe dich") · fester Tisch · überspringbar. Als Prototyp: eine Rive-Datei oder ein animiertes HTML-Mockup, um zu testen, ob es den "Wow, das ist anders"-Effekt hat.
