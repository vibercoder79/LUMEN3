---
name: lumen-trigger
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-trigger" eingibt
  oder "Starte Trigger Analyse" oder "Neuromarketing Trigger" sagt.

  Dieser Skill berechnet deterministisch die 7 Neuromarketing Trigger
  der Marke — Primary, Secondary und Dormant — auf Basis der Outputs
  aus Skill 02 (Brand Archetype) und Skill 03 (We Are / We Are Not).

  Deterministisch bedeutet: Identische Input-Dateien ergeben immer
  identisches Ergebnis.

  Methodische Basis: §3 (Damasio, Zaltman, LUMEN³ Trigger-Modell), siehe methodology.md
  Schemas, Frames, Layouts: artefact-templates.md
  Scoring-Logik: trigger-mapping.md (Single Source of Truth)

  Voraussetzung: 02-brand-archetype.md und 03-brand-interview.md müssen
  im outputs/ Verzeichnis vorhanden sein.

  Output:
  - 04-trigger-analysis.md (Schema 04 aus artefact-templates.md)
  - Miro Board Ergänzung (falls aktiv)
  - slides-trigger.md (Slide-Set für Skill 04)

  Version 1.4 — April 2026
---

# LUMEN² — Neuromarketing Trigger Analyse
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 04, Frame `trigger-hierarchie`, Slide-Set)
- `lumen3/methodology.md` (§3 — wissenschaftliche Begründung bei Bedarf)
- `lumen3/trigger-mapping.md` (Adjektiv-Trigger-Mapping, Scoring-Regeln)
- `clients/[name]/outputs/02-brand-archetype.md`
- `clients/[name]/outputs/03-brand-interview.md`
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Methodische Basis: §3 (Damasio, Zaltman, LUMEN³ Trigger-Modell).
Verweise dem Nutzer auf `methodology.md` nur, wenn er explizit fragt.

Wichtig: Das LUMEN³-Trigger-Modell ist kein peer-reviewed Framework, sondern
eine deterministische Operationalisierung von Hogsheads sieben Fascinate
Advantages. Der Mehrwert liegt in der Reproduzierbarkeit, nicht in einer
neuen wissenschaftlichen Hypothese. (siehe `methodology.md` §3)

---

## Verhaltensprinzipien

- Stelle nur eine Frage auf einmal.
- Zeige die Berechnung transparent — jeder Punkt-Eintrag muss nachvollziehbar sein.
- Bei fehlenden Voraussetzungen: Klar benennen, nicht abbrechen, sondern
  zurück an `/lumen-strategist` verweisen.
- Wenn Adjektive in 03-brand-interview.md nicht der englischen Schreibweise
  aus `trigger-mapping.md` entsprechen: Skill abbrechen mit klarer Fehlermeldung
  und Hinweis, Skill 03 als v2 erneut laufen zu lassen.

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/04-trigger-analysis.md` nicht: weiter mit
EINSTIEG, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 04 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## EINSTIEG

```
🦉 LUMEN² Neuromarketing Trigger Analyse von Owlist.

Ich lese deine Outputs aus Skill 02 und 03 und berechne deterministisch,
welche der 7 Trigger deine Marke aktiviert. Identische Inputs ergeben
immer identisches Ergebnis — kein Interpretationsspielraum.

Bitte stelle sicher, dass folgende Dateien existieren:
- clients/[name]/outputs/02-brand-archetype.md
- clients/[name]/outputs/03-brand-interview.md

Soll ich starten? (Standard: Ja)
```

---

## SCHRITT 1 — DATEIEN EINLESEN

Lies aus `02-brand-archetype.md`:
- Fascinate Primary Advantage
- Fascinate Secondary Advantage
- Fascinate Dormant Advantage
- Brand Archetype Primary
- Brand Archetype Shadow

Lies aus `03-brand-interview.md`:
- Alle CORE-Adjektive (englische Schreibweise)
- Alle ASPIRATION-Adjektive
- Alle NICHT-Adjektive
- Alle UNSICHER-Adjektive (fliessen nicht ins Scoring)

**Schema-Validierung:** Prüfe, ob jedes Adjektiv im `trigger-mapping.md`
existiert. Falls nicht: Konkrete Adjektive nennen, Skill abbrechen.

Zeige dem Nutzer was eingelesen wurde:

```
Eingelesen aus deinen LUMEN²-Outputs:

FASCINATE: Primary=[X] | Secondary=[Y] | Dormant=[Z]
ARCHETYPE: Primary=[X] | Shadow=[Y]

CORE ([N] Adjektive): [Liste]
ASPIRATION ([N]): [Liste]
NICHT ([N]): [Liste]

Alles korrekt? Dann starte ich das Scoring. (Ja/Korrigieren)
```

---

## SCHRITT 2 — DETERMINISTISCHES SCORING

Berechne alle 7 Trigger-Scores nach den Regeln in `trigger-mapping.md`.
Die Scoring-Logik selbst — wie viele Punkte pro CORE/ASPIRATION/NICHT,
wie Fascinate-Advantages und Archetypen einzahlen, wie Split-Adjektive
behandelt werden — steht ausschliesslich in `trigger-mapping.md`.

**Zeige die Berechnung transparent**, mit allen Quellen pro Trigger:

```
PASSION (PA):
+ Fascinate Primary=PASSION: +4 [oder 0]
+ Fascinate Secondary=PASSION: +2 [oder 0]
+ Fascinate Dormant=PASSION: -1 [oder 0]
+ Archetype Primary Mapping: +[0-3]
+ Archetype Shadow Mapping: +[0-1]
+ CORE-Adjektive mit PA-Mapping: +[N × 2]
  ([Liste der PA-Adjektive auf CORE])
+ ASPIRATION-Adjektive mit PA-Mapping: +[N × 1]
+ NICHT-Adjektive mit PA-Mapping: -[N × 1]
= TOTAL PA: [Score]
```

Diese Struktur für alle 7 Trigger (PA, IN, PR, PO, TR, MY, AL).

---

## SCHRITT 3 — ERGEBNIS

```
TRIGGER-HIERARCHIE [Projektname]:

#1 PRIMARY:    [TRIGGER] (Score: [N])
#2 SECONDARY:  [TRIGGER] (Score: [N])
#3             [TRIGGER] (Score: [N])
#4             [TRIGGER] (Score: [N])
#5             [TRIGGER] (Score: [N])
#6             [TRIGGER] (Score: [N])
#7 DORMANT:    [TRIGGER] (Score: [N]) ← bewusst NICHT einsetzen

Wichtig: Der Dormant Trigger ist nicht schwach — er ist einfach nicht
der emotionale Hauptkanal dieser Marke. Ihn erzwingen würde die Marke
inkonsistent machen.
```

---

## SCHRITT 4 — VERTIEFUNGS-INTERVIEW (8 Fragen)

Diese Fragen verändern das Scoring NICHT. Sie liefern qualitative
Validierung für den Output. Stelle sie einzeln, nicht auf einmal.

**V1:** Wenn du an deinen besten Kunden denkst — was hat ihn emotional
zu dir gezogen? (nicht rational)

**V2:** Gibt es einen Moment in deinem Business, wo Kunden besonders
begeistert oder berührt reagiert haben? Was war das?

**V3:** Welcher der 7 Trigger überrascht dich als Ergebnis? Passt er zur
Marke — oder fühlst du Widerstand?

**V4:** Der Dormant Trigger ist [TRIGGER]. Warum glaubst du, dass das
nicht euer Hauptkanal ist?

**V5:** Gibt es Momente, wo ihr bewusst Zurückhaltung zeigt (Mystique) —
oder zeigt ihr immer alles?

**V6:** Wie reagieren Kunden, wenn ihr innovativ kommuniziert vs. wenn
ihr Vertrauen und Verlässlichkeit betont? Was wirkt besser?

**V7:** Gibt es eine Diskrepanz zwischen wie ihr kommunizieren WOLLT
und wie ihr es tatsächlich TUT?

**V8:** Wenn du morgen nur noch einen Trigger nutzen dürftest — welcher
wäre es und warum?

---

## SCHRITT 5 — TRIGGER-PROFILE FÜR PRIMARY UND SECONDARY

Gib für Primary und Secondary die vollständige Beschreibung aus dem
folgenden Trigger-Katalog in den Output.

Diese Profile sind **inhaltlich** Teil dieses Skills (nicht der `methodology.md`),
weil sie operativ nutzbar sein müssen — Empfehlungen für Messaging, Visuals,
Formate. Sie kommen direkt in den Markdown-Output und in die Slides.

### PASSION — "Connect with emotion"
- Mechanismus: Zugehörigkeit, Begeisterung, emotionale Resonanz
- Signal: Wärme, Inspiration, Beziehung
- Formate: Persönliche Geschichten, Community, emotionale Kampagnen
- Visuell: Warm, nah, menschlich, Nahaufnahmen
- Sprache: Ich/Wir, Gefühle benennen, einladen
- Vermeiden: Kalt, distanziert, rein rational, korporativ
- Trigger-Satz: "Wir sehen dich — und wir sind für dich da"

### INNOVATION — "Change the game with creativity"
- Mechanismus: Neugier, Aufregung, Disruption, Überraschung
- Signal: Frische Ideen, unerwartete Perspektiven
- Formate: Thought Leadership, Experimente, "Was wäre wenn"
- Visuell: Kühn, unkonventionell, forward-looking
- Sprache: Fragen stellen, Annahmen brechen, neue Wörter
- Vermeiden: Vorhersehbar, konventionell, "wie alle anderen"
- Trigger-Satz: "Wir denken, was andere nicht zu denken wagen"

### PRESTIGE — "Earn respect with higher standards"
- Mechanismus: Aspiration, Status, Bewunderung, Exzellenz
- Signal: Qualität, Standards, Auswahl
- Formate: Awards, Case Studies, Premium-Positionierung
- Visuell: Elegant, reduziert, hochwertig, dunkel mit Gold-Akzenten
- Sprache: Präzise, kein Übertreiben, Fakten die beeindrucken
- Vermeiden: Massenappeal, zu freundlich, Rabatte, Casual
- Trigger-Satz: "Nicht für alle — für die, die Exzellenz kennen"

### POWER — "Lead with command"
- Mechanismus: Orientierung, Sicherheit durch Stärke, Klarheit
- Signal: Entschlossenheit, Führung, Richtung geben
- Formate: Klare Aussagen, Manifeste, Führungsposition
- Visuell: Bold, kontraststark, strukturiert, klar
- Sprache: Aktiv, direkt, keine Umwege, Imperative
- Vermeiden: Unentschlossen, vage, zu viele Optionen
- Trigger-Satz: "Wir führen — ihr könnt euch auf uns verlassen"

### TRUST — "Build loyalty with consistency"
- Mechanismus: Vorhersehbarkeit, Loyalität, Sicherheit
- Signal: Beständigkeit, Verlässlichkeit, Bewährtheit
- Formate: Langjährige Kundenstories, Garantien, Beweise
- Visuell: Beständig, warm, vertraut, keine Überraschungen
- Sprache: Klar, ehrlich, konkret, belegt
- Vermeiden: Häufige Änderungen, Überraschungen, Inkonsistenz
- Trigger-Satz: "Wir sind immer da — verlasst euch drauf"

### MYSTIQUE — "Communicate with substance"
- Mechanismus: Faszination, Neugier, Exklusivität durch Zurückhaltung
- Signal: Weniger zeigen als man hat, selektiv sein
- Formate: Teaser, curated Content, "inner circle" Feeling
- Visuell: Dunkel, selektiv, nie alles zeigen, viel Weissraum
- Sprache: Andeutet statt erklärt, Fragen offen lassen
- Vermeiden: Zu viel erklären, zu transparent, overexposed
- Trigger-Satz: "Nicht jeder versteht uns — das ist in Ordnung"

### ALERT — "Prevent problems with care"
- Mechanismus: Sicherheit durch Kontrolle, Präzision, Voraussicht
- Signal: Details, Risiken benennen, Schutz bieten
- Formate: Checklisten, Warnungen, Präzisions-Content
- Visuell: Klar strukturiert, kein Chaos, Präzision sichtbar
- Sprache: Genau, dokumentiert, keine Versprechungen ohne Belege
- Vermeiden: Vage, unstrukturiert, Risiken ignorieren
- Trigger-Satz: "Wir sehen, was andere übersehen — und schützen euch"

---

## OUTPUTS ERSTELLEN

### Output 1: 04-trigger-analysis.md

Lies Schema 04 aus `artefact-templates.md` Teil 1. Schreibe die Datei nach
diesem Schema mit folgenden H2-Headern:

```
## [Projektname] | [Datum]
## Methodische Basis: §3 (Damasio, Zaltman, LUMEN³ Trigger-Modell)
## Scoring: trigger-mapping.md | LUMEN³ by Owlist
```

Pflicht-Format in `Trigger-Hierarchie`:
```
Primary: [TRIGGER] (Score: [N])
Secondary: [TRIGGER] (Score: [N])
Dormant: [TRIGGER] (Score: [N])
```

In `Trigger-Profile` die vollständigen Beschreibungen für Primary und
Secondary aus dem Katalog oben einfügen — plus eine Kurzbeschreibung
für Dormant mit klarer Empfehlung "nicht aktiv einsetzen".

### Output 2: slides-trigger.md

Slide-Set gemäss `artefact-templates.md` Teil 2 für Skill 04:
`cover, trigger-bar, single-statement, single-statement, brain-diagram, grid-3x2`

- **Slide 1 (cover):** Projektname, "Trigger Analyse", Datum
- **Slide 2 (trigger-bar):** Balkendiagramm aller 7 Trigger
- **Slide 3 (single-statement):** Primary Trigger als Aussage
- **Slide 4 (single-statement):** Dormant Trigger als bewusste Abgrenzung
- **Slide 5 (brain-diagram):** Gehirn-Diagramm, Bild-Prompt für Midjourney/DALL-E
- **Slide 6 (grid-3x2):** Strategische Konsequenzen (Messaging, Visuals,
  Kanäle, Vermeiden, Tonalität, Beispiele)

**Bild-Prompt für Slide 5 (brain-diagram):**
```
A human brain diagram showing 7 labeled regions.
[PRIMARY TRIGGER] region: bright [PRIMARY_COLOR], dominant glow.
[SECONDARY TRIGGER] region: medium [SECONDARY_COLOR] glow.
[DORMANT TRIGGER] region: dark grey, minimal.
All other regions: subtle mid-tone.
Clean scientific illustration, dark background, white labels,
neuromarketing brand visualization.
```

### Output 3: Miro Board Ergänzung (falls Miro MCP aktiv)

Füge auf dem bestehenden We Are/Not Board (aus Skill 03) einen neuen
Frame hinzu nach Definition `trigger-hierarchie` aus `artefact-templates.md`
Teil 3.

Inhalt: Sticky Notes für jeden Trigger mit Score, Layout als horizontale
Balken-Reihe (Höhe proportional zum Score). Primary in Owlist Akzent,
Secondary in Mittelton, Rest grau, Dormant durchgestrichen oder mit
Warn-Markierung.

---

## ABSCHLUSS-MELDUNG

```
LUMEN² Trigger Analyse abgeschlossen.

Deterministisches Ergebnis:
Primary:   [TRIGGER] ([N] Punkte)
Secondary: [TRIGGER] ([N] Punkte)
Dormant:   [TRIGGER] ([N] Punkte)

Outputs:
04-trigger-analysis.md — Scoring-Protokoll + vollständige Analyse
slides-trigger.md — 6 Slides + Gehirn-Diagramm Prompt
[Falls Miro aktiv:] Trigger Frame auf Miro Board ergänzt

Wichtig: Dieses Ergebnis ist deterministisch. Gleiche Inputs aus Skill
02 und 03 ergeben immer dieses Ergebnis. Scoring-Logik: trigger-mapping.md

Weiter mit: /lumen-story — Story, Identity, Tonality
```

---

## SCHRITT 99 — Reflexion und Memory-Block

Nach der Abschluss-Meldung stelle eine Frage:
"Bist du mit diesem Lauf zufrieden? Falls nicht — was hätte besser sein können?"

Frage danach getrennt nach beiden Feldern aus Teil 7:
- **Strategisch:** relevant für Skill 06?
- **Intern:** nur für den Strategen, nicht nach aussen?

Append den Block an `clients/[name]/memory.md` gemäss Format und Kopf aus
`artefact-templates.md` Teil 7. Nur Append, nie Edit. Datei bei Bedarf
erstmalig anlegen.

---

## Was dieser Skill explizit NICHT tut

- Keine eigene Scoring-Logik (kommt aus `trigger-mapping.md`)
- Keine eigenen Frame-Definitionen (kommen aus `artefact-templates.md`)
- Keine eigenen Slide-Layouts (kommen aus `artefact-templates.md`)
- Keine wissenschaftliche Erklärung der Methodik im Skill selbst
  (kommt aus `methodology.md`, falls der Nutzer fragt)
- Keine Interpretation des Scoring — die Berechnung ist mechanisch,
  die qualitative Einordnung kommt aus dem Vertiefungs-Interview
- Keine Korrektur der Adjektiv-Schreibweise — bei Diskrepanz wird
  Skill 03 erneut gestartet (v2)
- Schreibt niemals Memory-Inhalte in Kunden-Outputs (Markdown, Slides, Miro, PDF)
