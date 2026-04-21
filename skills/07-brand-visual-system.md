---
tags: [lumen3, skill, brand, visual-system, design]
skill: lumen-visual-system
version: 1.0.0
status: aktiv
datum: 2026-04-21
name: lumen-visual-system
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-visual-system" eingibt,
  "Brand Visual System", "Visual Identity bauen" oder "Logo-Exploration" sagt.

  Dieser Skill ist die visuelle Fortsetzung von Skill 06 (Brand Universe).
  Er liest `brand-context.md` — insbesondere die Section "Visual Direction" —
  und erzeugt daraus das komplette visuelle System: Logo-Varianten,
  Farb- und Typografie-Tokens (Hex, Font-Namen, Scales), Icons, Applications
  (Briefbogen, Visitenkarte, Email-Signatur, Pitch-Deck, Website-Hero,
  Social-Templates) und abschliessend ein Brand-Guidelines-Dokument im
  10-Abschnitte-Format (`DESIGN.md`) abgeleitet vom externen Skill
  `design-md-generator`.

  Methodische Basis: Keine eigene Methodik — der Skill ist Forward-Engineering
  aus der strategischen Richtung von Skill 06. Alle visuellen Entscheidungen
  sind Ableitungen aus Archetyp, Primary Trigger, Neuro-Color und
  Tonalitäts-Profil. Keine neuen Farbpaletten, keine neuen Typografie-
  Entscheidungen aus dem Nichts — nur Konkretisierung der Richtungen aus
  Skill 06.

  Output:
  - clients/[name]/outputs/07-visual-system.md (Narrativ-Doku)
  - clients/[name]/outputs/DESIGN.md (10-Abschnitte-Format aus design-md-generator)
  - clients/[name]/assets/ (Logo-PNGs/SVGs, Icons, Favicons, Mockups)
  - clients/[name]/presentation/slides-visual-system.md
  - optional: Miro-Board-Spiegel (nur über Orchestrator zur Laufzeit)

  Rendering: slides-visual-system.md wird zusammen mit design-brief.md
  an Claude Design (Anthropic, seit 2026-04-17) übergeben für
  PPTX/PDF/Canva-Export im Corporate-Design.

  Version 1.0.0 — April 2026 (Erst-Einführung mit LUMEN³ v1.5)
---

# LUMEN³ — Brand Visual System
## Forward-Engineering des visuellen Systems aus dem Brand Universe
## Ein Framework von Owlist | www.owlist.ch

---

## Verhältnis zu Skill 06 und zu design-md-generator

Skill 07 steht zwischen zwei definierten Nachbarn:

- **Upstream — Skill 06 (Brand Universe).** Skill 06 liefert die
  strategische Richtung: Archetyp, Primary/Secondary/Dormant Trigger,
  Neuro-Color Palette, Tonalitäts-Profil, Bildsprache-Regeln — plus die
  neue Section "Visual Direction" in `brand-context.md` (ab LUMEN³ v1.5).
  Skill 07 nimmt diese Richtung und macht sie konkret: Hex-Werte, Font-
  Namen, Scales, Komponenten, Anwendungen. Skill 07 erfindet niemals
  eigene Richtungen. Fehlt eine Information in `brand-context.md`, bricht
  Skill 07 mit klarer Fehlermeldung ab und verweist auf `/lumen-universe`.

- **Output-Schablone — externer Skill `design-md-generator`.** Skill 07
  schreibt den finalen `DESIGN.md` nach dem 10-Abschnitte-Format des
  externen Skills `design-md-generator`. Der externe Skill wird **am Ende
  von Phase 6** aktiviert, um die 10-Abschnitte-Struktur zu erzeugen.
  Die einzelnen Sections (Farben, Typografie, Spacing, Komponenten etc.)
  werden aus den Outputs der Phasen 1–5 gespeist. Ist der externe Skill
  nicht verfügbar, läuft Skill 07 weiter und schreibt `DESIGN.md` manuell
  nach der 10-Abschnitte-Vorlage (Graceful Degradation — analog zum
  Miro-MCP-Ausfall).

---

## Modell-Routing

**Sonnet-Standard gemäss `lumen3/CLAUDE.md`.** Forward-Engineering aus
strategischen Richtungen ist ein Standard-LUMEN³-Skill — kein Opus nötig.
Haiku nur für rein mechanische Sub-Agent-Aufgaben (z.B. SVG-Konvertierung,
Datei-Batch-Erzeugung, Asset-Renaming).

| Aufgabe | Modell | Begründung |
|---|---|---|
| Phase 1 Logo-Exploration (6–9 Varianten) | Sonnet | Visuelle Konzeption aus strategischer Richtung |
| Phase 2 Commitment + Verfeinerung | Sonnet | Inhaltliche Entscheidung mit Nutzer |
| Phase 3 Icon-System | Sonnet | Konsistenz zu Master-Logo |
| Phase 4 Print & Identity | Sonnet | Layout-Entscheidungen |
| Phase 5 Digital Surfaces | Sonnet | Messaging + Layout kombiniert |
| Phase 6 DESIGN.md Synthese | Sonnet | Strukturierter Output gemäss Schablone |
| Asset-Batch-Renaming, SVG-Konvertierung | Haiku | Rein mechanisch |

---

## Voraussetzungen

- `lumen3/CLAUDE.md` (globale Regeln, Verhaltensregeln 1–13)
- `lumen3/artefact-templates.md` (Teil 4 Owlist-Tokens — für Owlist-Branding
  der Skill-eigenen Deliverables; Teil 7 Memory-Schema)
- `clients/[name]/outputs/brand-context.md` (**Pflicht** — enthält Visual
  Direction Tokens ab LUMEN³ v1.5)
- `clients/[name]/outputs/06-brand-universe.md` (**Pflicht** — Konsistenz-
  Anker für Tonalität, Trigger, Archetyp)
- `clients/[name]/competitive/[domain]/DESIGN.md` (**optional** — falls
  Skill 00 Wettbewerber über `design-md-generator` dokumentiert hat,
  werden sie als Negativ-Referenz gelesen, nicht kopiert)
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

**Sub-Brand-Variante.** Wenn der Nutzer beim Start `parent-brand=[name]`
als Parameter setzt, lädt Skill 07 zusätzlich
`clients/[parent-brand]/outputs/brand-context.md` und erzwingt
Konsistenz mit dem Master:

- Farbpalette wird vom Master geerbt (nur Akzent darf abweichen)
- Typografie-Familie ist identisch zum Master (nur Gewicht/Scale darf variieren)
- Voice-Anker (Tonalität, Wort-Verbote) werden vom Master geerbt

Abweichungen werden in Phase 2 dem Nutzer explizit gezeigt und brauchen
eine Begründung — ohne Begründung wird die Abweichung verworfen.

---

## Verhaltensregeln

Skill 07 hält sich vollständig an die Verhaltensregeln 1–13 aus
`lumen3/CLAUDE.md`. Besonders relevant:

- **Regel 9 — Keine eigenen Tokens.** Alle Farben, Fonts und Layout-
  Richtungen kommen aus `brand-context.md` (strategische Richtung) und
  werden in Phase 1–5 zu konkreten Werten geformt. Keine Erfindung neuer
  Paletten oder Font-Stacks aus dem Nichts. Der einzig zulässige
  Interpretations-Spielraum ist die Konkretisierung einer Richtung in
  einen spezifischen Hex-Wert oder eine spezifische Font-Familie.
- **Regel 10 — Memory-Block Pflicht.** Nach Abschluss wird ein Memory-
  Block gemäss `artefact-templates.md` Teil 7 an `clients/[name]/memory.md`
  angehängt. Nur Append, nie Edit.
- **Regel 11 — Re-Run liest Memory.** Existiert `07-visual-system.md`
  bereits, lädt Skill 07 in SCHRITT 0 die bestehenden Memory-Blöcke
  (nur strategisches Feld), zeigt sie dem Nutzer, fragt nach Berücksichtigung.
  Keine automatische Anpassung ohne Bestätigung.
- **Regel 12 — Memory niemals in Deliverable.** Der Inhalt der Memory-
  Blöcke taucht in keinem Kunden-Output auf — weder `07-visual-system.md`
  noch `DESIGN.md`, Slides, Miro-Board oder Asset-Kommentaren.
- **Regel 13 — Visual-Tokens bleiben bei Skill 07.** Skill 06 liefert
  nur Richtungen (warm/cool, serif/sans, dense/spacious). Konkrete
  Hex-Werte, Font-Familien und Scales werden hier in Skill 07 festgelegt.

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/07-visual-system.md` nicht: weiter mit
SCHRITT 1, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 07 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage:

```
Ich sehe [N] frühere Reflexion(en) zu Skill 07. Soll ich diese Lessons
im neuen Lauf berücksichtigen? (ja/nein)
```

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## SCHRITT 1 — Einstieg und Voraussetzungs-Check

Begrüsse mit:

```
🦉 LUMEN³ Brand Visual System.

Ich baue jetzt das visuelle System aus dem Brand Universe. Sechs Phasen,
sequenziell — keine parallelen Shortcuts.

Phase 1: Lockup-Exploration (6–9 Logo-Varianten)
Phase 2: Commitment auf eine Richtung + Verfeinerung
Phase 3: Icon-System (App-Icon, Favicon, Silhouetten)
Phase 4: Print & Identity (Briefbogen, Visitenkarte, Email, Rechnung, Proposal)
Phase 5: Digital Surfaces (Pitch-Deck, Website-Hero, Social)
Phase 6: Brand-Guidelines-Dokument (DESIGN.md, 10 Abschnitte)

Zeitbedarf: 60–120 Minuten inklusive Entscheidungsphasen.
```

Prüfe intern:

1. Existiert `.lumen-session` mit `client_name`?
2. Existiert `clients/[client_name]/outputs/brand-context.md`?
3. Enthält `brand-context.md` die Section "Visual Direction" (ab LUMEN³ v1.5)?
4. Existiert `clients/[client_name]/outputs/06-brand-universe.md`?
5. Wurde `parent-brand` als Parameter mitgegeben? Falls ja: Master-
   `brand-context.md` laden.

**Bei fehlender `brand-context.md`:**

```
Skill 07 kann nicht starten: clients/[name]/outputs/brand-context.md
existiert nicht. Diese Datei wird von Skill 06 (/lumen-universe) erzeugt
und ist Pflicht-Input für das Visual System.

Lösung: Zuerst /lumen-universe abschliessen, dann /lumen-visual-system.
```

**Bei fehlender Section "Visual Direction":**

```
Skill 07 kann nicht starten: brand-context.md hat keine Section
"Visual Direction" — das deutet auf eine ältere Skill-06-Version
(vor LUMEN³ v1.5) hin.

Lösung: /lumen-universe erneut laufen lassen (erzeugt v2 mit Visual
Direction Tokens), dann /lumen-visual-system.
```

---

## SCHRITT 2 — Strategische Richtung einlesen

Lies die Section "Visual Direction" aus `brand-context.md` und zeige sie
dem Nutzer als Bestätigung:

```
Ich lese die strategische Richtung aus brand-context.md:

Color Bias:          [warm | cool | neutral | contrast-high | contrast-low]
Color Mood:          [3–5 Adjektive]
Type Character:      [serif | sans-geometric | sans-humanist | mono-accent | mixed]
Type Mood:           [3–5 Adjektive]
Imagery Direction:   [photography | illustration | abstract | mixed] — [Kurzbeschreibung]
Layout Rhythm:       [dense | spacious | editorial | technical-grid]
Do:                  [5 Stichpunkte]
Dont:                [5 Stichpunkte]

Zusätzlich aus brand-context.md:
- Archetype:         [ARCHETYPE]
- Primary Trigger:   [TRIGGER] (Score [N])
- Neuro-Color hint:  [Primary Hex aus Skill 05]
- Voice:             [3 Kern-Adjektive]

Passt das? (ja/anpassen)
```

Bei `anpassen`: Nutzer gibt Korrektur — diese wird **nicht** in
`brand-context.md` zurückgeschrieben (Source of Truth bleibt), sondern
als Session-Overlay für diesen Skill-07-Lauf gemerkt. Nutzer wird
erinnert, ggf. Skill 06 erneut zu laufen.

---

## PHASE 1 — Lockup-Exploration (6–9 Varianten)

Ziel: Breite visuelle Suche, nicht Entscheidung.

### Output-Format

Erzeuge eine HTML-Canvas-Datei `clients/[name]/assets/phase-1-lockups.html`
mit einem Grid aus 6–9 Logo-Varianten. Jede Variante:

- Wordmark, Lettermark, Icon+Text, Monogram, Emblem, Abstract — **mindestens
  eine Variante pro Typus, die zur Primary-Trigger-Richtung passt**
- Platzhalter-Farben aus Neuro-Color Primary (aus `brand-context.md`)
- Font-Familie gemäss `type_character`-Richtung aus `brand-context.md`
  konkretisiert (Sonnet wählt eine konkrete Familie aus der passenden
  Google-Fonts-Kategorie; z.B. "sans-geometric" → Inter, Manrope,
  DM Sans, Sora, Space Grotesk — Nutzer bekommt die Auswahl später zur
  Prüfung)

### Trigger-basierte Richtlinien

| Primary Trigger | Lockup-Tendenz |
|---|---|
| PASSION | Handschrift-Akzent, warme Farbe, organische Form erlaubt |
| INNOVATION | Geometrisch, asymmetrisch, kantig, minimal |
| PRESTIGE | Serif, versal, viel Weissraum, monochrom |
| POWER | Bold Sans, grossflächig, kontrastreich |
| TRUST | Humanist Sans, symmetrisch, grounded, rund |
| MYSTIQUE | Monogram, eng gesetzt, dunkler Kontext, leise Typografie |
| ALERT | Technisch, monospaced Akzent, präzise Linien |

### Entscheidungs-Interview

Nach Canvas-Erstellung, genau eine Frage auf einmal:

1. "Welche 2–3 Varianten sprechen dich an?" (Nummern der Varianten)
2. "Was genau zieht dich — das Konstruktions-Prinzip, die Typografie,
   oder die Farb-Anmutung?"
3. "Welche Varianten sind ein klares Nein, und warum?"

Die Antworten werden nicht bewertet, sondern als Input für Phase 2 gemerkt.

---

## PHASE 2 — Commitment + Verfeinerung

Ziel: Eine Richtung wählen und zur Produktionsreife bringen.

### Schritt 2.1 — Commitment

Schlage eine Richtung vor:

```
Aus deinen Antworten lese ich: [Konstruktions-Prinzip] + [Typografie-
Tendenz] + [Farb-Ankerpunkt]. Das passt zu Variante [N] und zum Primary
Trigger [TRIGGER].

Soll ich mit dieser Richtung weitermachen? (ja/andere Variante)
```

### Schritt 2.2 — Verfeinerung (3 Iterations-Runden)

Pro Iteration:

1. Eine konkrete Logo-Variante als SVG in `clients/[name]/assets/logo/`
2. Drei Farbvarianten: Primary, Inverted (auf dunkel), Mono (einfarbig)
3. Drei Grössen-Tests: Favicon-Grösse (32px), Business-Card (120px), Hero (480px)
4. Nutzer gibt Feedback, Sonnet verfeinert

Nach Runde 3 wird die finale Version in drei Formaten exportiert:

- `logo-primary.svg` (Master)
- `logo-primary.png` (2× für Retina)
- `logo-horizontal.svg`, `logo-vertical.svg`, `logo-stacked.svg`
- `logo-white.svg`, `logo-dark.svg`, `logo-mono.svg`

### Farb-Festlegung

Die Neuro-Color-Richtung aus Skill 06 (Primary/Secondary/Accent als
Hex-Hints) wird hier konkretisiert zur Vollpalette:

- `primary` — Markenfarbe, aus Skill 05 Neuro-Color
- `secondary` — Ergänzung, harmoniert mit Primary (gleicher HSL-Abstand)
- `accent` — Call-to-Action, gemäss Trigger-Farb-Zuordnung
- `background_light`, `background_dark` — neutrale Paare
- `semantic_success`, `semantic_warning`, `semantic_error` — WCAG AA gegen beide Backgrounds
- `neutral_100` bis `neutral_900` — Grauskala, 9 Stufen

Alle Hex-Werte werden auf WCAG-AA-Kontrast gegen die jeweiligen
Backgrounds geprüft. Bei Fail: Hell/Dunkel-Shift um 5–10%, erneut prüfen.

### Typografie-Festlegung

Aus der `type_character`-Richtung aus `brand-context.md` wird eine
konkrete Font-Familie gewählt:

| type_character | Empfohlene Familien (wählen, nicht erfinden) |
|---|---|
| serif | Söhne Schmal, GT Sectra, Source Serif 4, PP Editorial New |
| sans-geometric | Inter, Manrope, DM Sans, Sora, Space Grotesk |
| sans-humanist | Söhne, GT America, Satoshi, Geist |
| mono-accent | JetBrains Mono, Geist Mono, IBM Plex Mono |
| mixed | Serif für Headline + Sans für Body (Kombination festlegen) |

Die konkrete Auswahl wird dem Nutzer vorgestellt und bestätigt. Keine
stillen Font-Entscheidungen.

---

## PHASE 3 — Icon-System

Ziel: Konsistente Icon-Sprache, die das Logo-System ergänzt.

### Pflicht-Outputs

- **App-Icon** (1024×1024 PNG, abgerundete Ecken gemäss iOS/Android-Norm)
- **Favicon** (32×32 ICO + 512×512 PNG für Browser-Tab und PWA)
- **Silhouetten/Abstract Marks** — 3 Varianten, die als Pattern oder
  Social-Avatar einsetzbar sind
- **Produkt-/Service-Icons** — 5 Icons mit einheitlicher Strichstärke
  und Eck-Radius, abgeleitet aus `brand-context.md` Services

### Konsistenz-Regeln

- Strichstärke konstant (z.B. 1.5px oder 2px, gewählt nach
  `layout_rhythm`: dense → 1.5px, spacious → 2px)
- Eck-Radius konstant (z.B. 2px oder 4px)
- Grid-Basis: 24×24px Artboard mit 2px Padding
- Einheitliche Metaphern-Familie (z.B. alle Linien-Icons, nicht gemischt
  mit Flächen-Icons)

### Output-Pfad

`clients/[name]/assets/icons/` — alle Icons als SVG plus PNG-Export.

---

## PHASE 4 — Print & Identity

Ziel: Papier-basierte Markenanwendungen — printfertig.

### Pflicht-Deliverables

| Deliverable | Format | Output |
|---|---|---|
| **Briefbogen DE** | A4, Logo + Absender + Footer | `brief-de.pdf` + `.html` |
| **Briefbogen EN** | A4, identisches Layout | `brief-en.pdf` + `.html` |
| **Visitenkarte** | 85×55mm (Euro-Standard), Vorder- und Rückseite | `card-front.pdf`, `card-back.pdf` |
| **Email-Signatur HTML** | Maximal 640px breit, tabellen-basiert | `signature.html` |
| **Email-Signatur Plain** | Plaintext-Fallback | `signature.txt` |
| **Rechnungs-Template** | A4, Logo, Branding, Platzhalter für Zahlen | `invoice-template.pdf` + `.html` |
| **Proposal-Template** | A4, Cover + 3 Inhaltsseiten + Angebots-Tabelle | `proposal-template.pdf` + `.html` |

### Layout-Prinzipien aus brand-context.md

- `layout_rhythm = dense` → engere Zeilenabstände (1.3–1.4), mehr Info pro Seite
- `layout_rhythm = spacious` → weitere Zeilenabstände (1.5–1.7), weniger Info pro Seite
- `layout_rhythm = editorial` → Spalten-Grid, Headlines klar abgesetzt
- `layout_rhythm = technical-grid` → sichtbares Grid, monospace-Akzente erlaubt

### Output-Pfad

`clients/[name]/assets/print/` — PDF + HTML-Quelle, damit Nutzer
HTML-Version editieren und neu exportieren kann.

---

## PHASE 5 — Digital Surfaces

Ziel: Digitale Anwendungen als Mockups und Templates.

### Pflicht-Deliverables

#### 5.1 Pitch-Deck — 4 Key-Slides

Kein komplettes 31-Slide-Deck (das bleibt Skill 06). Hier nur die
**4 Key-Slides, die die visuelle Identität tragen**:

1. **Cover-Slide** — Brand Name, Tagline, Datum
2. **Identity-Slide** — WHY Statement gross, Visual-Anker
3. **Color/Type-Slide** — Primary/Secondary/Accent + Headline/Body-Font
4. **Closing-Slide** — Kontakt, Logo, Tagline

Output: `clients/[name]/presentation/visual-key-slides.md` plus PPTX-
Export über Claude Design (Fallback: praesentation-builder-Skill).

#### 5.2 Website-Hero

**Variante A — Editorial** (Text-First, viel Weissraum): H1 links,
Visual-Anker rechts, CTA unter H1. Geeignet für `layout_rhythm = editorial`.

**Variante B — Technical** (Grid-sichtbar, datenbetont): H1 oben
breit, 3-Spalten-Layout darunter, CTA-Leiste unten. Geeignet für
`layout_rhythm = technical-grid`.

Beide Varianten werden erzeugt — der Nutzer wählt in Phase 6 die
Default-Variante für `DESIGN.md`.

Output: `clients/[name]/assets/web/hero-editorial.html` + `hero-technical.html`
plus Screenshots als PNG.

#### 5.3 Social-Templates

- **LinkedIn Feed-Post** (1200×627) — 3 Template-Varianten
- **Instagram Square-Post** (1080×1080) — 3 Template-Varianten
- **Instagram Story** (1080×1920) — 2 Template-Varianten

Pro Template: HTML + PNG-Export. Templates sind inhaltsleer
(Platzhalter-Text) — nur Layout, Farben, Typografie.

Output: `clients/[name]/assets/social/`

---

## PHASE 6 — Brand-Guidelines-Dokument (DESIGN.md)

Ziel: Handoff-ready Dokument für Entwickler, Designer, Content-Team.

### Aktivierung des externen Skills

Aktiviere den Skill `design-md-generator` mit folgendem Kontext:

- Quelle: alle bisherigen Phase-1–5-Outputs
- Ziel-Pfad: `clients/[name]/outputs/DESIGN.md`
- Format: 10-Abschnitte-Schablone

Falls der externe Skill nicht verfügbar ist, schreibt Skill 07 die
`DESIGN.md` manuell nach der gleichen 10-Abschnitte-Schablone (Graceful
Degradation, kein Abbruch).

### 10 Abschnitte der DESIGN.md

1. **Brand Essence** — 3 Sätze: Wer, Was, Warum. Kommt aus Skill 06.
2. **Logo System** — Varianten, Schutzzone, Mindestgrösse, Don'ts
3. **Color System** — Vollpalette mit Hex, RGB, HSL, Nutzungs-Regeln,
   WCAG-Kontrast-Matrix
4. **Typography** — Headline/Body/Accent-Familien, Scales, Line-Heights,
   Anwendungsbeispiele
5. **Iconography** — Grid, Strichstärke, Metaphern-Familie, Beispiele
6. **Imagery** — Do/Don't, Mood Board Prompt, Bildsprache-Regeln (aus
   `brand-context.md` übernommen)
7. **Layout & Grid** — Spacing-Unit, Grid-Columns, Section-Padding,
   Container-Max-Width
8. **Components** — Button (Primary/Secondary/Ghost), Card, Form-Input,
   Navigation-Item — als Token-Tabelle und Code-Snippet
9. **Voice in Design** — Headline-Ton, Microcopy-Stil, Wort-Verbote
   (aus Skill 06 Tonalitäts-Profil)
10. **Application Examples** — Thumbnails aller Phase-4/5-Deliverables
    mit Verweis auf die Asset-Dateien

### Pflicht-Kopf der DESIGN.md

```
# [Brand Name] — Brand Guidelines
## Generiert aus LUMEN³ Skill 07 | [Datum]
## Quelle: brand-context.md + 06-brand-universe.md
## Framework: LUMEN³ by Owlist | www.owlist.ch
```

---

## OUTPUT 1 — 07-visual-system.md (Narrativ)

Dieses Dokument ist die **narrative Schwester** von `DESIGN.md`. Es
erklärt, **warum** die visuellen Entscheidungen so getroffen wurden —
nicht nur **was** sie sind.

Pflicht-Sections:

- `# LUMEN³ — Brand Visual System`
- `## [Brand Name] | [Datum]`
- `## Framework: LUMEN³ by Owlist`
- `## Strategische Ableitung` — Wie wurde aus Archetype + Trigger + Neuro-Color
  die Farbpalette, Typografie, Bildsprache?
- `## Logo-System` — Welche Richtung gewonnen, welche verworfen, warum?
- `## Farb-Palette` — Hex-Werte + Begründung (Trigger-Fit, WCAG-Fit)
- `## Typografie` — Familien-Wahl + Begründung (Charakter-Fit)
- `## Icons & Bildsprache` — Prinzipien und Beispiele
- `## Anwendungen` — Überblick über Print/Digital/Social
- `## Nächster Schritt` — Übergabe an Entwicklung/Design-Team

Dieses Dokument referenziert `DESIGN.md` für alle Token-Tabellen —
keine Duplizierung.

---

## OUTPUT 2 — DESIGN.md

Siehe Phase 6 oben. 10 Abschnitte gemäss `design-md-generator`-Schablone.

---

## OUTPUT 3 — Asset-Verzeichnis

```
clients/[name]/assets/
├── logo/
│   ├── logo-primary.svg
│   ├── logo-primary.png
│   ├── logo-horizontal.svg
│   ├── logo-vertical.svg
│   ├── logo-stacked.svg
│   ├── logo-white.svg
│   ├── logo-dark.svg
│   └── logo-mono.svg
├── icons/
│   ├── app-icon-1024.png
│   ├── favicon-32.ico
│   ├── favicon-512.png
│   ├── silhouette-01.svg ... silhouette-03.svg
│   └── ui-01.svg ... ui-05.svg
├── print/
│   ├── brief-de.pdf + .html
│   ├── brief-en.pdf + .html
│   ├── card-front.pdf + card-back.pdf
│   ├── signature.html + signature.txt
│   ├── invoice-template.pdf + .html
│   └── proposal-template.pdf + .html
├── web/
│   ├── hero-editorial.html + .png
│   └── hero-technical.html + .png
└── social/
    ├── linkedin-feed-01.html ... 03.html
    ├── instagram-square-01.html ... 03.html
    └── instagram-story-01.html ... 02.html
```

Alle Assets referenzieren ausschliesslich die in Phase 2 festgelegten
Hex-Werte und Font-Familien. Keine Abweichungen.

---

## OUTPUT 4 — slides-visual-system.md

Slide-Set für die Präsentation des Visual Systems beim Kunden. Nutzt
Layout-IDs aus `artefact-templates.md` Teil 2 (keine eigenen Layouts):

| Slide | Layout-ID | Inhalt |
|---|---|---|
| 1 | `layout-cover` | Brand Name, "Visual System", Datum |
| 2 | `layout-single-statement` | Strategische Ableitung: "Von [Archetype] zu [visueller Kern-Aussage]" |
| 3 | `layout-grid-3x2` | Logo-Varianten (Primary/Horizontal/Stacked/White/Dark/Mono) |
| 4 | `layout-grid-3x2` | Farbpalette (Primary/Secondary/Accent/Light/Dark/Neutral-Stack) |
| 5 | `layout-grid-3x2` | Typografie (Headline/Body/Accent mit je Beispiel) |
| 6 | `layout-overview-2col` | Print-Identity (Briefbogen + Visitenkarte) |
| 7 | `layout-overview-2col` | Digital-Surfaces (Hero-Editorial + Hero-Technical) |
| 8 | `layout-grid-3x2` | Social Templates (6 Beispiele) |
| 9 | `layout-single-statement` | Nächster Schritt — Übergabe an Design/Dev |

Rendering über Claude Design (gemäss Skill 06 Pattern): slides-visual-
system.md + DESIGN.md + brand-context.md an Claude Design übergeben.

---

## OUTPUT 5 — Miro-Board (optional)

**Wichtig:** Skill 07 selbst erstellt **kein** Miro-Board. Das Miro-
Spiegel-Prinzip (`lumen3/CLAUDE.md`) besagt: Miro-Boards werden zur
Laufzeit vom Orchestrator (`/lumen-strategist`) erstellt, nicht vom
Sub-Skill. Skill 07 liefert die Markdown-Quellen — der Orchestrator
spiegelt sie optional nach Miro.

Frame-Definition `visual-system-board` würde in `artefact-templates.md`
Teil 3 ergänzt, **wenn** das Miro-Board aktiv benötigt wird. Aktuell
gibt es dafür keinen Nutzer-Auftrag — der Frame existiert nicht in Teil 3.

---

## ABSCHLUSS-MELDUNG

```
LUMEN³ Brand Visual System abgeschlossen.

Brand:              [BRAND NAME]
Primary Color:      [Hex] ([Trigger-Fit])
Headline Font:      [Familie] ([Charakter])
Body Font:          [Familie] ([Charakter])
Accent Font:        [Familie oder identisch]
Layout Rhythm:      [aus brand-context.md]

Outputs:
  clients/[name]/outputs/07-visual-system.md   — Narrativ
  clients/[name]/outputs/DESIGN.md             — 10-Abschnitte-Guidelines
  clients/[name]/assets/                       — Logos, Icons, Print, Web, Social
  clients/[name]/presentation/slides-visual-system.md

Übergabe:
  Design-Team:   DESIGN.md + assets/
  Dev-Team:      DESIGN.md (Token-Tabellen, Komponenten)
  Content-Team:  brand-guidelines.md (aus Skill 06) + voice_in_design-Section

Das Brand Universe ist visualisiert. Der Kunde hat ein vollständiges,
anwendbares Markensystem.
```

---

## SCHRITT 99 — Reflexion und Memory-Block

Nach der Abschluss-Meldung stelle eine Frage:
"Bist du mit diesem Visual System zufrieden? Falls nicht — was hätte
besser sein können?"

Frage danach getrennt nach beiden Feldern aus `artefact-templates.md` Teil 7:
- **Strategisch:** relevant für spätere Re-Runs oder für Skill 06-Wiederholung?
- **Intern:** nur für den Strategen, nicht nach aussen?

Append den Block an `clients/[name]/memory.md` gemäss Format und Kopf
aus `artefact-templates.md` Teil 7. Nur Append, nie Edit.

**Memory-Block-Beispiel:**

```markdown
### 2026-04-21 | Skill 07 | v1 | abgeschlossen

**Dauer (geschätzt):** 90 min

**Strategisch (freigabefähig für Skill 06):**
Nutzer hat Wordmark gewählt, Icon-Varianten verworfen — signalisiert,
dass Typografie als Primär-Identität trägt, nicht Symbol. Das sollte
in künftigen Skill-06-Läufen als Visual-Direction-Hinweis einfliessen.

**Intern (bleibt im Memory):**
Phase 2 Runde 3 war nötig, weil die ersten zwei Runden zu eng an der
Wettbewerber-Typografie lagen (aus competitive/[domain]/DESIGN.md
sichtbar). Nächster Lauf: Phase 1 explizit Abgrenzung fordern.
```

---

## Was dieser Skill explizit NICHT tut

- **Keine** eigene Farb-Palette erfinden — alle Farben leiten sich aus
  Neuro-Color (Skill 05 B4) und der Visual-Direction-Richtung (Skill 06)
  ab. Der Skill konkretisiert nur.
- **Keine** eigene Tonalität oder Voice-Entscheidung — kommt aus Skill 05
  und wird in `voice_in_design` (Phase 6, Abschnitt 9) nur dokumentiert,
  nicht neu festgelegt.
- **Keine** Anpassung der `brand-context.md` — Skill 07 liest sie nur.
  Bei Bedarf wird Skill 06 erneut gelaufen (erzeugt v2).
- **Keine** eigenen Schemas, Layouts oder Tokens — alles aus
  `artefact-templates.md` (Teil 2 Layouts, Teil 4 Owlist-Tokens) bzw.
  aus `brand-context.md` (Kunden-Tokens).
- **Keine** Memory-Inhalte in Deliverables — weder in
  `07-visual-system.md`, noch in `DESIGN.md`, noch in Slides oder
  Asset-Kommentaren.
- **Keine** Re-Scraping der Wettbewerber — wenn
  `competitive/[domain]/DESIGN.md` existiert (aus Skill 00 v2.2 mit
  design-md-generator-Integration), wird sie gelesen, nicht neu erzeugt.
- **Kein** eigenes Miro-Board — das übernimmt der Orchestrator zur
  Laufzeit, wenn der Nutzer es explizit anfordert.

---

## Nächste Schritte nach Skill-Abschluss

- Handoff an Design-Team: `DESIGN.md` + `clients/[name]/assets/`
- Handoff an Dev-Team: `DESIGN.md` Token-Tabellen + `brand-context.md`
- `/lumen-strategist` — zurück zum Orchestrator; alle 8 Stufen (00–07)
  sind jetzt abgeschlossen
