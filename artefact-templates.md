# LUMEN³ — Artefact Templates
## Single Source of Truth für Schemas, Layouts und Brand-Tokens
## Framework: LUMEN³ by Owlist | www.owlist.ch
## Version 1.1 | April 2026

---

## Zweck

Diese Datei definiert verbindlich, wie LUMEN³-Artefakte aussehen müssen — Markdown,
Slides, Miro. Jeder Skill liest aus dieser Datei. Keine Skill-Datei definiert eigene
Farben, eigene Layouts oder eigene Section-Strukturen. So bleiben Outputs über alle
Projekte hinweg replizierbar.

**Regel:** Wenn ein Skill etwas anderes braucht als hier definiert, wird zuerst diese
Datei erweitert — nie der Skill allein.

---

## TEIL 1 — MARKDOWN-SCHEMAS

Jeder Skill schreibt seinen Output mit den hier definierten Pflicht-Sections in
exakt dieser Reihenfolge. Skill 06 (`lumen-universe`) liest deterministisch aus
diesen Sections — fehlt eine, bricht Skill 06 mit klarer Fehlermeldung ab.

### Schema-Konventionen (gelten für alle Skills)

- H1 = Skill-Name in der Form `# LUMENx — [Skill-Bezeichnung]`
- H2 unter H1 = Projektname und Datum
- H2 unter Datum = Framework-Hinweis und Methodik-Quelle
- Pflicht-Sections sind H2-Überschriften mit dem hier definierten Wortlaut
- Optionale Sections sind erlaubt, müssen aber nach den Pflicht-Sections kommen
- Letzte Pflicht-Section ist immer `## Nächster Schritt`

### Schema 00 — Creative Footprint Full Potential Analyse (v2.0)

```
# LUMEN¹ — Creative Footprint Full Potential Analyse
## [Projektname] | [Datum]
## Methodik: Enigma Creative Footprint (2022) + Owlist Asset-Erweiterung
## Framework: LUMEN³ by Owlist | www.owlist.ch

## Markt-Übersicht
## Full Potential Ranking (Phase 1)
## Dimension-Profile pro Wettbewerber
## Visuelle Analyse des Wettbewerbsumfelds (Phase 2)
### Farbrad
### Schriftart-Tabelle
### Namens-Archetypen
### Tagline-Quadrant
## Positionierungs-Lücken
## Strategische Insights
## Abgleich mit deiner Hypothese
## Nächster Schritt
```

**Pflicht-Felder in `Full Potential Ranking`:**
- Tabelle mit Spalten: Rang · Wettbewerber · Full Score · Assets · Paid · Earned · Shared · Owned (alle 0–100)

**Pflicht-Felder in `Dimension-Profile pro Wettbewerber`:**
- Pro Wettbewerber: Positionierung in einem Satz · Full Potential Score · Dimension-Breakdown mit Kurz-Kommentar · Top-3 Stärken (DPs mit Score 2) · Top-3 Schwächen (DPs mit Score 0)

**Pflicht-Felder in `Visuelle Analyse`:**
- Pro Modul (Farbrad/Fonts/Namen/Taglines): SVG-Verweis · Crowded/Potential-Zonen · Eine strategische Aussage

**Pflicht-Felder in `Abgleich mit deiner Hypothese`:**
- `Deine Hypothese:` (aus SCHRITT 4)
- `Bewertung:` (trifft die Lücke / überlappt / liegt außerhalb)
- `Empfehlung:` (weiterverfolgen / schärfen / Alternativen prüfen)

**Datenpunkt-Scoring:** Voll dokumentiert in `skills/_review/skill-00-datapoints-v2.md` (nach Freigabe: `skills/00-datapoints.md`). 123 Datenpunkte, 3-Punkt-Skala (0/1/2), auf 100 normiert, gewichtet zu Full Potential Score.

**Dimensions-Gewichte:** Assets 44% · Paid 6% · Earned 14% · Shared 11% · Owned 25%.

### Schema 01 — Business Context

```
# LUMEN¹ — Business Context
## [Projektname] | [Datum]
## Framework: LUMEN³ by Owlist

## 1. Business & Person
## 2. Zielgruppe & Markt
## 3. Angebot & Versprechen
## 4. Sichtbarkeit & Kundenfeedback
## Brand-Strategische Insights
## Offene Fragen / Lücken
## Nächster Schritt
```

### Schema 02 — Brand Archetype

```
# LUMEN¹ — Brand Archetype
## [Projektname] | [Datum]
## Methodik: Hogshead Fascinate (2014) + Pearson/Jung Archetypes

## Fascinate Advantage
## Brand Archetype (Pearson/Jung)
## Synthese
## Strategische Konsequenzen
## Nächster Schritt
```

**Pflicht-Felder in `Fascinate Advantage`:** `Primary:`, `Secondary:`, `Dormant:`
**Pflicht-Felder in `Brand Archetype (Pearson/Jung)`:** `Primary:`, `Shadow:`

### Schema 03 — Brand Interview (We Are / We Are Not)

```
# LUMEN² — Brand Interview: We Are / We Are Not
## [Projektname] | [Datum]
## Methodik: Aaker (1997) + Meyerson (2012)

## WIR SIND — CORE
## ASPIRATION
## UNSICHER
## WIR SIND NICHT
## Analyse
## Nächster Schritt
```

**Pflicht-Format in den vier Wort-Sections:** Markdown-Liste, ein Adjektiv pro Zeile,
exakt in der englischen Schreibweise aus `trigger-mapping.md` (z.B. `- Inspiring`,
nicht `- inspirierend`). Sonst bricht Skill 04 das Scoring ab.

### Schema 04 — Trigger Analysis

```
# LUMEN² — Neuromarketing Trigger Analyse
## [Projektname] | [Datum]
## Methodik: Damasio (1994), Zaltman (2003), LUMEN³ Trigger-Modell
## Scoring: lumen3/trigger-mapping.md

## Deterministisches Scoring-Protokoll
## Trigger-Hierarchie
## Qualitative Insights
## Trigger-Profile
## Strategische Konsequenzen
## Nächster Schritt
```

**Pflicht-Format in `Trigger-Hierarchie`:**
```
Primary: [TRIGGER] (Score: [N])
Secondary: [TRIGGER] (Score: [N])
Dormant: [TRIGGER] (Score: [N])
```

### Schema 05 — Story Identity

```
# LUMEN² — Story, Identity, Tonality
## [Projektname] | [Datum]
## Methodik: Brand Story Canvas + Neuro-Color Research

## Story-Kern
## Identity-Statement
## Tonalitäts-Profil
## Farb-Empfehlung (Neuro-Color)
## Sprach-Regeln
## Nächster Schritt
```

### Schema 06 — Brand Universe

```
# LUMEN³ — Brand Universe
## [Projektname] | [Datum]
## Synthese aller LUMEN³-Stufen

## Executive Summary
## Brand-Fundament
## Brand-Persönlichkeit
## Trigger & Emotionale Aktivierung
## Story & Tonalität
## Visuelles Universum
## Anwendungs-Empfehlungen
## Brand Context (maschinenlesbar)
```

Skill 06 schreibt zusätzlich `brand-context.md` als reines YAML-Frontmatter für die
Übergabe an nachgelagerte Tools (Webdesign-Briefings, KI-Marketing-Agents).

---

## TEIL 2 — SLIDE-LAYOUTS

Sechs wiederverwendbare Layout-IDs. Jeder Skill, der Slides erzeugt, referenziert
eine dieser IDs — keine eigenen Layouts erfinden.

### `layout-cover`
Verwendung: Slide 1 jedes Slide-Decks.
Inhalt: Projektname (H1), Skill-Bezeichnung (H2), Datum, Owlist-Logo unten rechts.
Hintergrund: Owlist Primary `#596A71`, Text weiss.

### `layout-overview-2col`
Verwendung: Gegenüberstellungen (We Are / We Are Not, Primary / Dormant Trigger).
Inhalt: H1 oben, zwei Spalten mit je einer farbigen Headline und einer Liste.
Linke Spalte: positive Farbe (`#52B788` Grün). Rechte Spalte: Abgrenzungs-Farbe
(`#E76F51` Koralle).

### `layout-trigger-bar`
Verwendung: Trigger-Hierarchie als Balkendiagramm.
Inhalt: H1, sieben horizontale Balken (PA, IN, PR, PO, TR, MY, AL), Score-Zahl
rechts neben jedem Balken. Primary-Balken in Owlist Akzent `#A55B1C`,
Secondary in Mittelton, Rest grau.

### `layout-single-statement`
Verwendung: Identity-Statement, Trigger-Satz, Story-Kern.
Inhalt: Eine grosse Aussage zentriert (max 20 Wörter), darunter klein die Quelle
(z.B. "LUMEN² Story Identity, April 2026").

### `layout-grid-3x2`
Verwendung: Sechs Brand-Tokens auf einer Slide (z.B. Farben + Fonts + Tonalität).
Inhalt: H1, sechs gleichgrosse Boxen in 3×2-Anordnung mit Token-Name und Wert.

### `layout-brain-diagram`
Verwendung: Slide 5 in Skill 04 (Gehirn-Diagramm).
Inhalt: H1 oben, mittig der Bild-Prompt-Output (Midjourney/DALL-E generiert),
unten kleine Legende mit Primary/Secondary/Dormant-Trigger-Namen und Farben.

### Slide-Set pro Skill (verbindlich)

| Skill | Slide-Set |
|---|---|
| 03 Brand Interview | cover, overview-2col, single-statement, single-statement, single-statement |
| 04 Trigger Analysis | cover, trigger-bar, single-statement, single-statement, brain-diagram, grid-3x2 |
| 05 Story Identity | cover, single-statement, grid-3x2, grid-3x2 |
| 06 Brand Universe | cover, single-statement, trigger-bar, grid-3x2, grid-3x2, overview-2col |

---

## TEIL 3 — MIRO-FRAME-DEFINITIONEN

Miro ist Spiegel-Layer, nicht Speicher. Jeder Frame hat eine fixe ID, fixe Farbe,
fixe Sticky-Note-Farbe. Skill schreibt nie freie Frames.

| Frame-ID | Verwendet in | Rahmen-Farbe | Sticky-Farbe | Layout |
|---|---|---|---|---|
| `wir-sind-core` | Skill 03 | `#2D6A4F` (Dunkelgrün) | `#52B788` (Hellgrün) | Grid 3 Spalten, 150×100px |
| `wir-sind-aspiration` | Skill 03 | `#1D6FA4` (Dunkelblau) | `#74B3CE` (Hellblau) | Grid 3 Spalten |
| `wir-sind-unsicher` | Skill 03 | `#E9C46A` (Gelb) | `#F4D35E` (Hellgelb) | Grid 3 Spalten |
| `wir-sind-nicht` | Skill 03 | `#C1121F` (Dunkelrot) | `#E76F51` (Koralle) | Grid 3 Spalten |
| `trigger-hierarchie` | Skill 04 | `#6A0572` (Violett) | je nach Rang | Balken horizontal |
| `competitive-grid` | Skill 00 | `#596A71` (Owlist Primary) | `#A55B1C` (Akzent) | Grid 4 Spalten pro Wettbewerber |
| `brand-universe` | Skill 06 | `#A55B1C` (Owlist Akzent) | gemischt | Hub-and-Spoke |

**Frame-Grösse:** Standard 600×800px, ausser `trigger-hierarchie` (1000×400px) und
`brand-universe` (1200×900px).

**Board-Header (immer identisch):**
```
[Projektname] — [Skill-Bezeichnung]
LUMEN³ by Owlist | [Datum]
Methodik: [Quelle aus Skill]
```

---

## TEIL 4 — OWLIST BRAND-TOKENS

Diese Tokens werden überall eingesetzt, wo LUMEN³ visuell auftritt — Slides, Miro,
PDF-Reports, Markdown mit Inline-Styling.

### Farben

| Token | Hex | Verwendung |
|---|---|---|
| `owlist-primary` | `#596A71` | Hauptfarbe, Hintergründe, Body-Text auf hell |
| `owlist-accent` | `#A55B1C` | Akzent, CTAs, Highlights |
| `owlist-light` | `#F5F1EA` | Heller Hintergrund, Cards |
| `owlist-dark` | `#2A3438` | Dunkler Hintergrund, Cover-Slides |
| `owlist-success` | `#52B788` | Positive Aussagen, CORE, Primary Trigger |
| `owlist-warning` | `#F4D35E` | Unsicher, Übergang |
| `owlist-danger` | `#E76F51` | Abgrenzung, NICHT, Dormant |

### Fonts

| Token | Familie | Verwendung |
|---|---|---|
| `font-primary` | Poppins | Body-Text, UI, Markdown |
| `font-display` | PP Rader | Headlines, Cover-Slides, grosse Statements |
| `font-mono` | JetBrains Mono | Code, Hex-Werte, technische Tabellen |

### Tonalität (für Owlist-eigene Outputs, nicht für Kunden-Outputs)

- Tone: Simple, Optimistic, Avant-gardiste, Entrepreneurial, Visionary
- Archetype: The Catalyst (Passion Primary, Innovation Secondary)
- Tagline: "Catalyst for change"

**Wichtig:** Diese Tokens gelten für Owlist-Branding der LUMEN³-Outputs selbst
(Footer, Cover-Slides, Board-Header). Die **Kunden-Brand** hat eigene Tokens, die
in Skill 05 (Neuro-Color) und Skill 06 (Visual Universe) festgelegt werden.

---

## TEIL 5 — VALIDIERUNGS-REGELN

Skill 06 prüft beim Einlesen jeder Vorgänger-Datei:

1. **H1-Format** entspricht `# LUMENx — [Bezeichnung]`
2. **Alle Pflicht-H2-Sections** aus dem jeweiligen Schema sind vorhanden
3. **Section-Reihenfolge** stimmt mit der Schema-Definition überein
4. **Mindest-Inhalt** pro Section: > 50 Zeichen (sonst gilt sie als leer)
5. **Schema-spezifische Pflicht-Felder** sind ausgefüllt (z.B. `Primary:` in 02 und 04)

Bei Fehler bricht Skill 06 ab mit:
```
Skill 06 kann nicht starten: [Skill X] Output entspricht nicht dem Schema.
Fehler: [konkreter Hinweis welche Section fehlt oder leer ist]
Lösung: [Skill X] erneut laufen lassen — erzeugt v2.
```

---

## TEIL 6 — VERSIONIERUNG DIESER DATEI

Diese Datei ist versioniert wie ein Vertrag. Änderungen brechen potenziell
bestehende Outputs. Regel:

- **Patch (1.0 → 1.1):** Neue optionale Sections, neue Tokens hinzufügen. Bestehende
  Outputs bleiben gültig.
- **Minor (1.0 → 2.0):** Pflicht-Sections umbenennen, Reihenfolge ändern. Alte
  Outputs müssen mit Migrations-Hinweis markiert werden.
- **Major:** Schema-Brüche. Erfordert Re-Run aller betroffenen Skills.

Aktuelle Version: **1.1** — Teil 7 (Memory-Schema) ergänzt.
Vorher: 1.0 (initiale Definition).

---

## TEIL 7 — MEMORY-SCHEMA

Jeder Skill schreibt nach Abschluss oder bewusstem Abbruch einen Memory-Block
in die zentrale Memory-Datei des Kunden. Memory ist internes Strategie-Gedächtnis
— niemals Teil eines Kunden-Deliverables.

### Speicherort und Datei-Kopf

Eine Datei pro Kunde: `clients/[name]/memory.md`

Alle Skills schreiben in dieselbe Datei. Existiert sie nicht, legt sie der
schreibende Skill selbst an mit folgendem Kopf:

```
# LUMEN³ — Memory
## [Projektname] | intern, niemals Teil eines Deliverables
## Format: append-only, Blöcke chronologisch
```

### Block-Format

Jeder Lauf produziert genau einen H3-Block:

```markdown
### 2026-04-11 | Skill 03 | v1 | abgeschlossen

**Dauer (geschätzt):** 25 min

**Strategisch (freigabefähig für Skill 06):**
Adjektiv-Liste war zu lang. Nutzer wollte max. 15 Begriffe pro Kategorie.

**Intern (bleibt im Memory):**
Gründer war am Anfang defensiv, hat sich erst nach Frage 8 geöffnet.
```

### Pflicht-Struktur (exakt)

- **H3-Zeile:** `### [YYYY-MM-DD] | Skill [NN] | v[N] | [Status]`
  Parsbar via Regex `^### (\d{4}-\d{2}-\d{2}) \| Skill (\d{2}) \| v(\d+) \| (\w+)$`
- **Dauer-Zeile:** `**Dauer (geschätzt):** [N] min`
- **Strategisch-Block:** `**Strategisch (freigabefähig für Skill 06):**` + Prosa
- **Intern-Block:** `**Intern (bleibt im Memory):**` + Prosa

Mindestens eines der beiden Reflexions-Felder muss Inhalt haben. Leere Felder
werden mit `—` markiert. Blöcke mit beiden Feldern leer gelten als ungültig
und werden von späteren Skills nicht als "vorherige Lesson" eingelesen.

### Status-Werte (erlaubte Wortlaute)

| Status | Bedeutung | Output-Datei |
|---|---|---|
| `abgeschlossen` | Skill ist regulär durchgelaufen | existiert |
| `abgebrochen` | Bewusster Stopp durch Nutzer oder Schema-Fehler | existiert nicht |
| `wiederholt` | Re-Run, Memory der Vorgänger-Version wurde gelesen | existiert (v2+) |

`wiederholt` ist ein Sonderfall von `abgeschlossen` und markiert, dass der
Skill in Schritt 0 bestehende Memory-Blöcke zur Vorgänger-Version geladen hat.

### Versions-Kopplung

Die Version im Memory-Block entspricht **exakt** dem Suffix der Output-Datei:

- `03-brand-interview.md` → Memory-Version `v1`
- `03-brand-interview-v2.md` → Memory-Version `v2`
- `03-brand-interview-v3.md` → Memory-Version `v3`

Pro Version existiert maximal **ein** Memory-Block. Zweite Reflexionen zur
gleichen Version sind verboten — das würde das Append-only-Prinzip brechen.

### Append-only

- Memory-Blöcke werden ausschliesslich ans Ende der Datei angehängt.
- Bestehende Blöcke werden niemals editiert, umgeschrieben, verschoben oder
  gelöscht.
- Korrekturen zu alten Einträgen erscheinen als neuer Block mit Verweis in
  der Reflexion (z.B. "Korrektur zu v1: ...").
- Technisch umgesetzt via Append-Operation, nicht Edit/Replace. Die Pflicht
  steht zusätzlich als globale Regel in `CLAUDE.md`.

### Strategisch vs. intern — Klassifikation

Der Skill fragt bei der Reflexion explizit nach beiden Feldern:

1. **Strategisch:** "Gibt es eine Beobachtung, die in die Brand-Arbeit
   einfliessen darf (Skill 06 — Brand Universe)?"
2. **Intern:** "Gibt es Prozess-Vermerke für mich als Stratege, die nicht
   nach aussen gehen dürfen?"

Leseregeln:
- **Strategisch:** lesbar von Skill 06 und `/lumen-learn`. Skill 06 holt
  trotzdem eine zweite Freigabe vom Nutzer, bevor der Inhalt ins Brand
  Universe wandert.
- **Intern:** ausschliesslich lesbar von `/lumen-strategist` und `/lumen-learn`.
  Darf niemals in einen Kunden-sichtbaren Output wandern.

### Abgrenzung — was Teil 7 nicht regelt

- **Wann** ein Skill die Reflexion abfragt — steht in der jeweiligen Skill-Datei
  als Schritt 99.
- **Wie** `/lumen-learn` Muster aus Einträgen mehrerer Kunden erkennt — steht
  im Helper-Skill.
- **Wie** Skill 06 das strategische Feld in das Brand Universe einbaut — steht
  in Skill 06 unter der Section "Strategische Anmerkungen aus dem Prozess".
