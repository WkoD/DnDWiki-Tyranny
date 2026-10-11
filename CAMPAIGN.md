# CAMPAIGN.md

Kampagnenspezifischer Kontext für Claude. **Strikt pointer-basiert**: nur stabile
Meta-Infos und Zeiger auf die Wiki-Tiddler - **keine** aus Tiddlern ableitbaren Daten
(Namen, Spielerstufe, Datumswerte, Plot-Status), damit diese Datei nicht veraltet. Den
echten Stand immer live aus den Tiddlern lesen.

## Identität

**Tyranny of Dragons** - offizielles WotC-D&D-Abenteuer (Hoard of the Dragon Queen +
The Rise of Tiamat), gespielt auf Deutsch (Wiki-Sprache `de-DE`). Setting: Forgotten Realms
(Sword Coast), Kalender von Harptos und Münzen der Forgotten Realms über das Plugin
`tiddlyrpg-setting-forgottenrealms`. Regelsystem D&D 5e, Regeln von 2014 (Plugin
`tiddlyrpg-ruleset-dnd5e2014`).

**Regelsprache** (Control-Panel → Einstellungen → TiddlyRPG → Regelwerk Einstellungen und
Kampagnenwelt Einstellungen): Regelbegriffe erscheinen englisch wie im Regelbuch am Tisch (ft,
lb, d6, WIS), ebenso die Münzen (gp); nur Monats- und Festnamen deutsch (Wiki-Sprache).
Zahlen stehen in `<<unit>>` immer mit Einheit, so wie die Quelle sie nennt (`<<ft 60 range>>`).

## Tisch-Meta (steht NICHT in Tiddlern)

- **Hausregeln:** <!-- abweichende Regeln; vom Nutzer zu ergänzen -->

Wer welche Figur spielt, steht im Feld `player` der Figuren (siehe unten), nicht hier.

## Konventionen (DM-Entscheidung)

- **Session-Doku:** keine separaten Session-Log-Tiddler. Sitzungen werden als
  Ergänzung an das jeweilige Ereignis-Tiddler (Tag `Event`) angehängt - ein
  Ereignis-Tiddler kann mehrere In-World-Zeitpunkte sammeln: die Daten stehen im Feld
  `date`, jeder Abschnitt im Text beginnt mit `<<date>>` (optional mit Beschriftung
  `<<date "…">>`). Die Spielerfiguren, die dabei waren, stehen als Tags am Ereignis.
- **Offene Punkte/Plot-Fäden:** das Snippet „Offene Punkte“ (`open-items`) wird inline in
  Ereignis-Tiddlern eingefügt (rot umrandete Callout-Box); wird
  entfernt/verkleinert, sobald der Strang aufgelöst ist. Kein zentraler Tracker.
- **Karten zu Orten:** keine Unter-Tiddler. Das Kartenbild steht im Feld `map` des Orts
  (Bild aus `images/map/`) und erscheint im Ort als Tab „Karte“.
- **Spieler-Sichtbarkeit:** Am Tisch wird über den Knopf „Sicht“ (Sidebar) zwischen der
  öffentlichen Sicht, der Sicht eines Spielers und der DM-Sicht gewechselt. Was nur
  einzelne Spieler kennen, trägt den Tag `Secret` mit ihren Figuren; Teile eines Texts
  werden mit `<<secret "Figur">>` bzw. `<$secret for="Figur">…</$secret>` gesperrt. Die
  veröffentlichte Fassung bietet die DM-Sicht nicht an (kein
  `$:/config/tiddlyrpg/view/dm-published`). Reine Render-Bequemlichkeit, kein Zugriffsschutz -
  das Repo ist öffentlich.
- **Kampagnenspezifische Ordner/Assets:** <!-- aktuell keine zusätzlichen
  Unterordner unter images/ -->
- **Erzählstil (Tempus):** durchgängige Vergangenheitsform (Präteritum) als
  Chronik-Stil - auch für andauernde Eigenschaften/Fakten (z. B. "war ein
  Mensch" statt "ist ein Mensch"); impliziert **nicht** Tod/Nicht-Existenz.
  Ausnahmen, die im Ursprungstempus bleiben: wörtliche Rede/Zitate, primäre
  In-World-Dokumente (Tagebücher, Briefe, Ich-Perspektive-"Visionen"), rot
  umrandete TBC-Callout-Boxen (`@@.tc-tiddler-frame ... @@`), sowie
  Trivia-Quiz-Frage/Antwort-Blöcke (wie zitierter Spielkarten-Text behandelt).
  Ich-Perspektive-Tabellen wie Personality Traits/Ideals/Bonds/Flaws sind
  **nicht** ausgenommen - werden trotz Ich-Form ins Präteritum gesetzt.

## Story-Planungs-Workflow für Claude

**Erst den echten Tiddler-Stand über diese Pointer lesen, nie aus dem Gedächtnis
oder aus dieser Datei planen:**

- **Fraktionen / Orte / NPCs:** Tiddler mit dem jeweiligen Typ-Tag. Startpunkte:
  `Index` und die Kategorie-Hub-Tiddler `Person`, `Location`, `Organisation`, `Event`,
  `Campaign`, ... (Shadows aus `tiddlyrpg-core`).
- **Orte-Hierarchie (Ober-/Unterort):** über das Feld `location` („liegt in“). Die Orte des
  Abenteuers liegen in der `Schwertküste`, `Skyreach Castle` ist eine eigene Wurzel. Tags
  drücken keine Orte aus.
- **Spielerstufe:** Body von `PlayerLevel.tid`.
- **Offene Plot-Fäden:** Suche nach dem Offene-Punkte-Snippet (`@@.tc-tiddler-frame`) in
  `Event`-Tiddlern.
- **Kampagnenstruktur / Handlungsbögen (Kapitel des Abenteuers):** Ereignisse, an denen eine
  Spielerfigur als Tag hängt (die Figuren, die dabei waren); Zeitstrahl und Tabelle am
  `Campaign`-Hub.
- **Spielercharaktere:** `Player`-getaggte Tiddler (aktiv) und Tiddler mit Feld `player`
  (früher gespielt, z. B. `Bran`), bzw. der `Player`-Hub. Das Feld `player` nennt den
  realen Spieler.
- **Geheimes:** `Secret`-getaggte Tiddler (Hub `Secret`, in der DM-Sicht vollständig).

*Dann* konsistente Vorschläge machen, die an bestehende Tiddler/Tags anknüpfen
(explizite `[[WikiLinks]]` setzen). Bei offiziellem
Abenteuer-Material Konsistenz mit dem publizierten Kanon wahren.
