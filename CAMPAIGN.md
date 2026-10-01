# CAMPAIGN.md

Kampagnenspezifischer Kontext für Claude. **Strikt pointer-basiert**: nur stabile
Meta-Infos und Zeiger auf die Wiki-Tiddler - **keine** aus Tiddlern ableitbaren Daten
(Namen, Spielerstufe, Datumswerte, Plot-Status), damit diese Datei nicht veraltet. Den
echten Stand immer live aus den Tiddlern lesen.

## Identität

**Tyranny of Dragons** - offizielles WotC-D&D-Abenteuer (Hoard of the Dragon Queen +
The Rise of Tiamat), gespielt auf Deutsch (Wiki-Sprache `de-DE`). Setting: Forgotten Realms
(Sword Coast), Kalender von Harptos über das Plugin `dndwiki-forgottenrealms`.

## Tisch-Meta (steht NICHT in Tiddlern)

- **Spieler <-> Charakter:** <!-- reale Spielernamen <-> Charaktere; vom Nutzer zu ergänzen -->
- **Hausregeln:** <!-- abweichende Regeln; vom Nutzer zu ergänzen -->

## Konventionen (DM-Entscheidung)

- **Session-Doku:** keine separaten Session-Log-Tiddler. Sitzungen werden als
  Ergänzung an das jeweilige Ereignis-Tiddler (Tag `Event`) angehängt - ein
  Ereignis-Tiddler kann mehrere In-World-Zeitpunkte sammeln, getrennt durch `---` und
  mit `<<datelong ...>>`-Überschriften.
- **Offene Punkte/Plot-Fäden:** das Snippet „Offene Punkte“ (`open-items`) wird inline in
  Ereignis-Tiddlern eingefügt (rot umrandete Callout-Box); wird
  entfernt/verkleinert, sobald der Strang aufgelöst ist. Kein zentraler Tracker.
- **Karten zu Orten:** Orte haben oft einen begleitenden Karten-Tiddler `<Name>/Map`
  (Datei `<Name>_Map.tid`, Tag `Map`, Feld `image`) neben dem Haupt-Tiddler `<Name>.tid`;
  er erscheint im Ort als Tab „Karte“.
- **Spieler-Sichtbarkeit:** der Spieler-Login auf dem `Player`-Hub
  (`$:/state/dndwiki/player`) wird genutzt, um am
  Tisch zwischen DM- und Spieler-Perspektive zu wechseln (reine
  Render-Bequemlichkeit, kein Zugriffsschutz - das Repo ist öffentlich).
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
  `Campaign`, ... (Shadows aus `dndwiki-core`).
- **Spielerstufe:** Body von `PlayerLevel.tid`.
- **Offene Plot-Fäden:** Suche nach dem Offene-Punkte-Snippet (`@@.tc-tiddler-frame`) in
  `Event`-Tiddlern.
- **Kampagnenstruktur / Handlungsbögen (Kapitel des Abenteuers):** `Campaign`-getaggte Tiddler.
- **Spielercharaktere:** `Player`-getaggte Tiddler bzw. der `Player`-Hub.

*Dann* konsistente Vorschläge machen, die an bestehende Tiddler/Tags anknüpfen
(explizite `[[WikiLinks]]` setzen). Bei offiziellem
Abenteuer-Material Konsistenz mit dem publizierten Kanon wahren.
