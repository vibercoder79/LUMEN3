---
name: lumen-universe
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-universe" eingibt,
  "Brand Universe", "Brand Identity Document" oder "Finaler Brand Report" sagt.

  Dieser Skill ist der Abschluss der LUMEN³ Brand Strategist Arbeit.
  Er synthesiert alle Outputs aus Skills 01–05 zu einem vollständigen
  Brand Universe Document — finales Deliverable für den Kunden und
  Briefing-Dokument für nachgelagerte Tools.

  Zusätzlich erstellt er brand-context.md — einen maschinenlesbaren
  Connector für nachgelagerte Marketing- und Webdesign-Skills.

  Methodische Basis: Synthese über alle Paragraphen von methodology.md
  (§1 Aaker/Meyerson, §2 Pearson/Hogshead, §3 Damasio/Zaltman,
  §4 Card Sort, §5 Haller/Neuro-Color). Dieser Skill hat keine eigene
  Methodik — er liest die Outputs der Vorgänger-Skills und verdichtet sie.

  Schemas, Layouts, Miro-Frames, Tokens: artefact-templates.md
  Validierungs-Regeln: artefact-templates.md Teil 5

  Voraussetzung (alle empfohlen, Pflicht ist mindestens 05):
  outputs/01-business-context.md, 02-brand-archetype.md,
  03-brand-interview.md, 04-trigger-analysis.md, 05-story-identity.md

  Output:
  - 06-brand-universe.md (Schema 06 aus artefact-templates.md)
  - slides-brand-universe.md (Owlist Track-Deck, 31 Slides)
  - design-brief.md (Input für Website Creator / Webflow)
  - brand-context.md (maschinenlesbarer Connector)
  - brand-guidelines.md (Tone, Typografie, Farben im Anthropic-Format)
  - Miro Board: Brand Universe Summary Frame (falls aktiv)

  Version 1.4 — April 2026 (Memory-Integration)
---

# LUMEN³ — Brand Universe Document
## Finaler Deliverable des Brand Strategist
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 06, Slide-Set, Miro-Frame `brand-universe`, Validierungs-Regeln Teil 5)
- `lumen3/methodology.md` (§1–§5 — Synthese über alle Paragraphen)
- `lumen3/trigger-mapping.md` (für Konsistenz-Check der Trigger-Hierarchie)
- `clients/[name]/outputs/05-story-identity.md` (**Pflicht**, sonst Abbruch)
- `clients/[name]/outputs/01–04.md` (empfohlen — fehlende Dateien werden
  im Konsistenz-Check als Lücke markiert)
- `clients/[name]/memory.md` (append-only, liest ALLE Blöcke des Projekts)

Methodische Basis: Synthese über alle §§ von `methodology.md`. Verweise
dem Nutzer auf `methodology.md` nur dann, wenn er explizit nach einer
einzelnen Quelle fragt.

---

## Rolle & Qualitätsanspruch

Agiere als Senior Brand Consultant mit 20+ Jahren Erfahrung. Denke und
liefere wie die führenden Strategieberatungen:

- **McKinsey** — Jede Aussage mit Evidenz belegen. Keine Behauptung ohne
  Grundlage aus den LUMEN²-Outputs. Struktur: Situation → Complication → Resolution.
- **BCG** — Strategische Klarheit. Nicht beschreiben was ist — sondern was
  es bedeutet. Jeder Track hat eine Kernaussage (So-What).
- **Bain** — Handlungsorientierung. Jedes Kapitel endet mit einer klaren
  Implikation für die Praxis.
- **Oliver Wyman** — Präzision in der Sprache. Kein Wort zu viel.
- **Roland Berger** — Visuell-narrative Exzellenz. Ein Gedanke pro Slide.
  Headline = Aussage, nicht Thema.

**Qualitäts-Checkliste vor jedem Output:**
- [ ] Jede Slide-Headline ist eine Aussage, kein Thema
  FALSCH: "Brand Archetype" | RICHTIG: "[Brand Name] ist [Archetype] — der Katalysator für [X]"
- [ ] Jeder Track hat eine So-What-Aussage
- [ ] Kein Slide hat mehr als einen Hauptgedanken
- [ ] Executive-lesbar in unter 30 Sekunden pro Slide
- [ ] Kein Consulting-Jargon (leverage, synergize, best-in-class)
- [ ] Kein generisches Lob (innovative, leading, excellent)

---

## Verhaltensprinzipien

- Lese zuerst ALLE verfügbaren Output-Dateien (01–05).
- **Validiere jede Datei gegen ihr Schema BEVOR du sie inhaltlich einliest.**
- Zeige was gelesen wurde, bevor du mit der Synthese beginnst.
- Synthesiere — nicht zusammenfassen. Neue Einsichten aus der Kombination.
- Erstelle alle 5 Output-Dateien automatisch.
- Frage am Ende nach Miro Board.

---

## EINSTIEG

```
🦉 LUMEN³ Brand Universe von Owlist.

Dies ist der Abschluss der Brand Strategist Arbeit.

Drei Fragen:

1. Sprache?
   Deutsch (Standard) | English | Français | Andere

2. Brand Name des Projekts?
   [Wird verwendet für Titelseite und alle Dokumente]

3. Miro Board?
   - Bestehend: URL eingeben
   - Neu erstellen
   - Kein Miro

Ich validiere und lese jetzt alle verfügbaren Output-Dateien...
```

---

## SCHRITT 0 — Projekt-Memory lesen und Freigabe einholen

Lies `clients/[name]/memory.md` falls vorhanden. Extrahiere ALLE Blöcke im
gesamten Projekt — nicht nur zu Skill 06. Lies ausschliesslich das
**strategische** Feld jedes Blocks. Das interne Feld wird nie gelesen,
nie angezeigt, nie verwendet.

Existieren strategische Einträge, zeige sie dem Nutzer nummeriert und
frage nach expliziter Zweitfreigabe pro Eintrag:

```
Ich habe [N] strategische Beobachtung(en) aus dem Prozess gefunden:

[1] Skill 03, v1: [strategischer Inhalt, eine Zeile]
[2] Skill 03, v2: [strategischer Inhalt, eine Zeile]
[3] Skill 05, v1: [strategischer Inhalt, eine Zeile]

Welche sollen in die Section "Strategische Anmerkungen aus dem Prozess"
des Brand Universe einfliessen? (Komma-Liste, "alle" oder "keine")
```

Freigegebene Einträge werden inhaltlich übernommen, aber **reformuliert**
als strategische Beobachtung über die Marke:
- Keine Meta-Begriffe wie "Reflexion", "Feedback", "Memory", "Lessons",
  "Erkenntnis aus Skill X", "gelernt"
- Keine Verweise auf Skill-Namen, Versionen oder Prozess-Historie
- Formuliert als Aussage über die Marke, nicht über den Arbeitsprozess

Ohne Freigabe fällt die Section "Strategische Anmerkungen aus dem Prozess"
in OUTPUT 1 komplett weg. Anschliessend weiter mit SCHRITT 1.

---

## SCHRITT 1 — SCHEMA-VALIDIERUNG (PFLICHT VOR EINLESEN)

**Diese Validierung läuft vor dem inhaltlichen Einlesen jeder Vorgänger-Datei.**
Sie ist in `artefact-templates.md` Teil 5 definiert und hier als
Pflicht-Schritt verankert.

Für jede der fünf Dateien (`01-business-context.md`, `02-brand-archetype.md`,
`03-brand-interview.md`, `04-trigger-analysis.md`, `05-story-identity.md`) prüfe:

1. **H1-Format** entspricht `# LUMENx — [Bezeichnung]` gemäss Schema
2. **Alle Pflicht-H2-Sections** aus dem jeweiligen Schema sind vorhanden
3. **Section-Reihenfolge** stimmt mit der Schema-Definition überein
4. **Mindest-Inhalt** pro Section: > 50 Zeichen (sonst gilt sie als leer)
5. **Schema-spezifische Pflicht-Felder** sind ausgefüllt
   (`Primary:` in Schema 02, `Primary:` / `Secondary:` / `Dormant:` in Schema 04,
   Adjektiv-Listen in Schema 03 in englischer Schreibweise)

**Bei Validierungs-Fehler brich ab mit folgender Fehlermeldung:**

```
Skill 06 kann nicht starten: [Skill X] Output entspricht nicht dem Schema.

Datei:    clients/[name]/outputs/[dateiname]
Problem:  [konkreter Hinweis welche Section fehlt, in falscher Reihenfolge
           steht oder leer ist]

Lösung: Lass [Skill X] erneut laufen — das erzeugt [dateiname]-v2.
        Dann starte /lumen-universe neu.
```

**Ausnahme:** Wenn eine Datei komplett fehlt (z.B. kein `00-competitive-analysis.md`),
ist das kein Fehler — der Skill läuft weiter und markiert die Lücke im
Konsistenz-Check (siehe Schritt 3). Nur wenn eine vorhandene Datei das Schema
verletzt, wird abgebrochen. Pflicht ist mindestens `05-story-identity.md` —
fehlt die, bricht der Skill mit Hinweis auf `/lumen-story` ab.

---

## SCHRITT 2 — ALLE OUTPUTS EINLESEN

Nach erfolgreicher Validierung lese die Inhalte ein. Bei den Pflicht-Feldern
reicht der strukturierte Teil — keine Freitext-Interpretation.

Zeige Lesebestätigung:

```
Eingelesen und validiert:
01 Business Context:  [Ja/Fehlt] — [Branche, Zielgruppe, Phase]
02 Brand Archetype:   [Ja/Fehlt] — [Primary/Secondary/Dormant, Shadow]
03 We Are/Not:        [Ja/Fehlt] — [CORE-Count, NICHT-Count, Aaker-Dimension]
04 Trigger Analyse:   [Ja/Fehlt] — [Primary Trigger, Score]
05 Story Identity:    [Ja]       — [WHY Statement, 3 Kern-Adjektive, Neuro-Color Primary]

Starte Brand Universe Synthese...
```

---

## SCHRITT 3 — BRAND VOICE ANALYSE (5 Dimensionen)

Analysiere still (Bewertung 1–10), zeige dann die Ergebnisse:

- **Dimension 1 — Tone Analysis** (aus 05 Tonalität + 03 We Are/Not)
- **Dimension 2 — Core Messaging** (aus 05 WHY/HOW/WHAT + Positioning)
- **Dimension 3 — Visual Consistency** (aus 05 Neuro-Color + 02 Archetype + 04 Trigger)
- **Dimension 4 — Target Audience Alignment** (aus 01 Business Context + 04 Trigger-Profil)
- **Dimension 5 — Competitive Differentiation** (aus 03 NICHT + 05 Positioning)

```
Brand Voice Gesamt-Score: [Durchschnitt X/10]
```

---

## SCHRITT 4 — KONSISTENZ-CHECK

Prüfe, ob die Vorgänger-Outputs einander widersprechen:

- Stimmt der Pearson/Jung-Primary (Skill 02) mit der dominanten Aaker-Dimension (Skill 03) überein?
- Passt der Primary Trigger (Skill 04) zum Primary Advantage (Skill 02)?
- Spiegeln die 3 Kern-Adjektive (Skill 05) die CORE-Wörter aus Skill 03 wider?
- Passt die Neuro-Color Primary (Skill 05) zum Primary Trigger (Skill 04) gemäss §5-Tabelle?

Bei Widersprüchen: Benennen, nicht auflösen. Die Widersprüche gehen in
die `Konsistenz-Analyse` Section des finalen Outputs ein.

---

## OUTPUT 1 — 06-brand-universe.md

Lies Schema 06 aus `artefact-templates.md` Teil 1. Schreibe die Datei nach
`clients/[name]/outputs/06-brand-universe.md` mit folgendem Header:

```
# LUMEN³ — Brand Universe
## [Brand Name] | [Datum]
## Synthese aller LUMEN³-Stufen | LUMEN³ by Owlist
```

**Pflicht-Sections (Reihenfolge wie in Schema 06):**

- `## Executive Summary` — 3–4 Sätze: Wer ist die Marke, was macht sie
  einzigartig, für wen, und wozu?
- `## Brand-Fundament` — Archetyp (aus 02) + Fascinate Advantage +
  Business Context (aus 01) + WHY Statement (aus 05)
- `## Brand-Persönlichkeit` — 3 Kern-Adjektive + Charakter-Beschreibung
  + Positioning Statement (aus 05 B2) + dominante Aaker-Dimension (aus 03)
- `## Trigger & Emotionale Aktivierung` — Primary/Secondary/Dormant Trigger
  (aus 04) + operative Konsequenzen (Messaging, Visuals, Vermeiden)
- `## Story & Tonalität` — Brand Story (3 Versionen), Tonalitäts-Profil,
  5 Beispielsätze / 5 Gegenbeispiele, Wort-Verbote (aus 05)
- `## Visuelles Universum` — Neuro-Color Palette (aus 05 B4), Typografie-
  Charakter, Bildsprache, Mood Board Prompt
- `## Anwendungs-Empfehlungen` — Homepage-Struktur, Key Messages,
  Prioritäten-Liste (Sofort / Kurzfristig / Mittel), Übergabe an nachgelagerte Tools
- `## Brand Context (maschinenlesbar)` — Verweis auf `brand-context.md`
  plus Kurz-Zusammenfassung der YAML-Struktur

**Optionale Sections (nach Pflicht-Sections):**
- `## Konsistenz-Analyse` — Widersprüche zwischen den LUMEN²-Outputs,
  falls im Schritt 4 gefunden
- `## Strategische Anmerkungen aus dem Prozess` — nur falls in SCHRITT 0
  Einträge explizit freigegeben wurden. Inhalte reformuliert als
  Aussagen über die Marke, ohne Meta-Vokabular und ohne Skill-Verweise.
- `## Quellen` — Verweis auf `methodology.md` §§1–5

---

## OUTPUT 2 — slides-brand-universe.md

Slide-Set gemäss `artefact-templates.md` Teil 2 für Skill 06:
`cover, single-statement, trigger-bar, grid-3x2, grid-3x2, overview-2col`

Das ist das **minimale Pflicht-Slide-Set**. Der volle Owlist-Track-Deck
(31 Slides in 7 Tracks) bleibt als erweiterte Variante erhalten — er
referenziert ausschliesslich Layout-IDs aus `artefact-templates.md` Teil 2.

### Pflicht-Slides (aus artefact-templates.md)

- **Slide 1 (cover):** Brand Name, "Brand Universe", Datum
- **Slide 2 (single-statement):** WHY Statement als grosse Aussage
- **Slide 3 (trigger-bar):** Trigger-Hierarchie der 7 Trigger aus Skill 04
- **Slide 4 (grid-3x2):** 6 Tokens — 3 Kern-Adjektive + Primary Color + Secondary Color + Font-Charakter
- **Slide 5 (grid-3x2):** 6 Tokens — Mission + Vision + Positioning + Hedgehog Sweet Spot + Primary Trigger + Archetype-Name
- **Slide 6 (overview-2col):** Links CORE (grün), Rechts NICHT (koralle) aus Skill 03

### Erweiterter Track-Deck (31 Slides, optional, nach den Pflicht-Slides)

Der Track-Deck ist operativ nützlich für längere Kundenpräsentationen und
folgt der Owlist Visual Universe Struktur: Cover → Intro → 7 Tracks → Summary.
**Jede Slide referenziert eine Layout-ID aus `artefact-templates.md` Teil 2.**
Keine eigenen Layouts erfinden.

#### COVER (Slide 1 — layout-cover)
Brand Name vertikal zentriert. Rechte Hälfte: Brand Primary Color als Farbfeld.
Footer: Owlist Logo + www.owlist.ch.

#### INTRO-KAPITEL

**Slide 2 — Der LUMEN³ Brand Prozess** (layout-grid-3x2)
Headline: "Wie diese Marke entstanden ist"
Sub: "6 Skills. Ein vollständiges Brand Universe."
6 Boxen: Competitive (falls vorhanden), Business Context, Brand Archetype,
We Are/Not, Trigger, Story & Identity.

**Slide 3 — Brand Map** (layout-overview-2col)
Links: WIR SIND (CORE-Adjektive aus Skill 03, grün).
Rechts: WIR SIND NICHT (NICHT-Adjektive, koralle).
Fuss: "Dominante Aaker-Dimension: [NAME]"

#### TRACK 01 — PURPOSE (Slides 4–7)

- **Slide 4 (layout-single-statement):** Track Opener "Track 01 — Purpose"
- **Slide 5 (layout-grid-3x2):** Archetype + Fascinate Advantage. Links Archetype-Name gross. Rechts 3 Zeilen: Primary / Secondary / Dormant Advantage.
- **Slide 6 (layout-single-statement):** "[Brand Name] ist [ARCHETYPE]" — Zitat-Slide mit 2–3 Sätzen aus Skill 02, Keywords als Tags.
- **Slide 7 (layout-trigger-bar):** Trigger-Hierarchie. Primary in Owlist Akzent, Secondary Mittelton, Rest grau, Dormant durchgestrichen.

#### TRACK 02 — GOLDEN CIRCLE (Slides 8–11)

- **Slide 8 (layout-single-statement):** Track Opener "Track 02 — Golden Circle"
- **Slide 9 (layout-single-statement):** WHY Statement gross zentriert, in Anführungszeichen. Footer: "Entdeckt, nicht erfunden."
- **Slide 10 (layout-overview-2col):** Links HOW (Unser Ansatz, 3 Punkte). Rechts WHAT (Unser Beweis — Angebote als WHY-Beweis).
- **Slide 11 (layout-overview-2col):** Links Mission (Gegenwart). Rechts Vision (Zukunft).

#### TRACK 03 — STORY (Slides 12–14)

- **Slide 12 (layout-single-statement):** Track Opener "Track 03 — Story"
- **Slide 13 (layout-single-statement):** 1-Satz-Essenz als grosse Aussage, Sub: Kurzform der About-Page Version.
- **Slide 14 (layout-grid-3x2):** 6 Keywords der Marke aus CORE + 3 Kern-Adjektiven.

#### TRACK 04 — IDENTITY (Slides 15–17)

- **Slide 15 (layout-single-statement):** Track Opener "Track 04 — Identity"
- **Slide 16 (layout-single-statement):** 3 Kern-Adjektive als zentrale Aussage. Darunter: "Wenn [Brand Name] eine Person wäre..." mit 3–4 Sätzen.
- **Slide 17 (layout-single-statement):** Positioning Statement (Dante Labs Format) — For / Who / Is a / That / Unlike / Because, zeilenweise gross.

#### TRACK 05 — VISUAL UNIVERSE (Slides 18–22)

- **Slide 18 (layout-single-statement):** Track Opener "Track 05 — Visual Universe"
- **Slide 19 (layout-grid-3x2):** Neuro-Color Palette. 6 Farbfelder: Primary, Secondary, Accent, Background Light, Background Dark, Kulturkontext-Hinweis. Hex + Rolle unter jedem Feld.
- **Slide 20 (layout-grid-3x2):** Typography Direction. 3 Zeilen — Headline / Body / Accent Charakter — plus Grössen-Empfehlung.
- **Slide 21 (layout-overview-2col):** Links "WIR ZEIGEN" (5 Bildsprache-Beschreibungen). Rechts "WIR ZEIGEN NIE" (5 Gegenbeispiele).
- **Slide 22 (layout-single-statement):** Mood Board Prompt als grosse Aussage (für Midjourney/DALL-E/Claude).

#### TRACK 06 — VOICE & TONE (Slides 23–25)

- **Slide 23 (layout-single-statement):** Track Opener "Track 06 — Voice & Tone"
- **Slide 24 (layout-single-statement):** "SO klingt [Brand Name]" — 5 Beispielsätze als Zitate. Fuss: Brand Voice Score.
- **Slide 25 (layout-single-statement):** "SO klingt [Brand Name] NICHT" — 5 Gegenbeispiele, rot markiert. Wort-Verbote als Tags unten.

#### TRACK 07 — WEBDESIGN DIRECTION (Slides 26–28)

- **Slide 26 (layout-single-statement):** Track Opener "Track 07 — Webdesign Direction"
- **Slide 27 (layout-grid-3x2):** Homepage-Struktur. 6 Boxen — Hero / Trust / Services / Proof / CTA / Tone-of-Voice-Note. Empfohlene Headline-Richtung pro Box.
- **Slide 28 (layout-grid-3x2):** Key Messages. 3 Nachrichten-Karten — Rationale (WHAT) / Emotionale (WHY) / Differenzierungs-Botschaft (HOW), je 1 Satz.

#### SUMMARY & ÜBERGABE (Slides 29–31)

- **Slide 29 (layout-grid-3x2):** Summary. 7 Track-Kern-Aussagen plus Brand Name in der Mitte.
- **Slide 30 (layout-single-statement):** Finale Version — Brand Name gross, Tagline darunter, Primary Color Background.
- **Slide 31 (layout-overview-2col):** Übergabe. Links "Website Creator → design-brief.md". Rechts "Marketing Skills → brand-context.md". Footer: "Content Team → brand-guidelines.md".

**Qualitäts-Check vor Abschluss des Decks:**
- [ ] Jede Slide-Headline ist eine Aussage, kein Thema
- [ ] Jede Slide referenziert eine Layout-ID aus `artefact-templates.md` Teil 2
- [ ] Keine Owlist-Brand-Tokens hartcodiert — alles aus Teil 4
- [ ] Kein Slide hat mehr als einen Hauptgedanken

---

## OUTPUT 3 — design-brief.md

Kompakter Design-Brief für den Website Creator (Webflow). Enthält:
- Brand Name, Tagline, WHY Statement
- Neuro-Color Palette (alle Hex aus Skill 05 B4)
- Typografie-Charakter (Headline / Body / Accent)
- Bildsprache-Regeln (5 × zeigen / 5 × zeigen nie)
- Mood Board Prompt (für Midjourney/DALL-E/Claude)
- Homepage-Struktur (5 Boxen: HERO / TRUST / SERVICES / PROOF / CTA)
- Trigger-basierte Messaging-Empfehlungen

Kein zusätzliches Schema — dieses Dokument ist ein operatives
Übergabe-Dokument, kein Schema-Output.

---

## OUTPUT 4 — brand-context.md

Maschinenlesbarer Connector als YAML-Frontmatter. Nachgelagerte
Marketing-Skills lesen diese Datei automatisch als Shared Context.

```yaml
---
brand_name: [Brand Name]
project: [Projektname]
framework: LUMEN³ by Owlist
version: 1.3
generated: [Datum]

archetype:
  fascinate_primary: [ADVANTAGE]
  fascinate_secondary: [ADVANTAGE]
  fascinate_dormant: [ADVANTAGE]
  pearson_primary: [ARCHETYP]
  pearson_shadow: [ARCHETYP]

trigger:
  primary: [TRIGGER]
  primary_score: [N]
  secondary: [TRIGGER]
  secondary_score: [N]
  dormant: [TRIGGER]

personality:
  core_adjectives: [wort1, wort2, wort3]
  aaker_dimension: [DIMENSION]
  positioning_statement: "[Dante Labs Format]"

story:
  why: "To [BEITRAG] so that [WIRKUNG]"
  how: [how1, how2, how3]
  what: "[WHAT]"
  mission: "[Mission Statement]"
  vision: "[Vision Statement]"
  tagline: "[1-Satz-Essenz]"

voice:
  style_adjectives: [adj1, adj2, adj3, adj4, adj5]
  forbidden_words: [wort1, wort2, wort3]
  address_form: "du|sie"

neuro_color:
  primary: "#HEX"
  secondary: "#HEX"
  accent: "#HEX"
  background_light: "#HEX"
  background_dark: "#HEX"
  cultural_context: "[Haller-Hinweis]"

typography:
  headline_character: "[Beschreibung]"
  body_character: "[Beschreibung]"
  accent_character: "[Beschreibung]"

sources:
  methodology: lumen3/methodology.md
  templates: lumen3/artefact-templates.md
  trigger_mapping: lumen3/trigger-mapping.md
---
```

Nach dem Frontmatter: 3–5 Sätze Kurz-Zusammenfassung der Marke als
Freitext, damit LLM-basierte Tools die Struktur mit Kontext verbinden können.

---

## OUTPUT 5 — brand-guidelines.md

Tone, Typografie, Farben und Formatting im Anthropic-Brand-Guidelines-Format.
Kein eigenes Schema — die Datei ist ein Content-Team-Deliverable mit
folgenden Sections:

- `## Tone of Voice` (aus Skill 05 B3)
- `## Color System` (aus Skill 05 B4 — Neuro-Color mit Hex + Rolle)
- `## Typography System` (Headline / Body / Accent mit Charakter und Grössen-Empfehlung)
- `## Formatting Rules` (Satzlänge, Anrede, Humor, Wort-Verbote)
- `## Voice Examples` (5 × "so klingt die Marke" + 5 × "so klingt sie nicht")

---

## MIRO BOARD — Brand Universe Summary Frame (falls aktiv)

Verwende Frame `brand-universe` aus `artefact-templates.md` Teil 3.
Rahmen-Farbe, Grösse (1200×900px), Sticky-Farben kommen aus der zentralen
Definition — keine eigenen Frames oder Farben.

Layout: Hub-and-Spoke. Mittig Brand Name + Tagline. Sieben Spokes zu den
sieben Tracks mit je einer Kern-Aussage. Board-Header nach Vorlage aus
`artefact-templates.md` Teil 3.

---

## ABSCHLUSS-MELDUNG

```
LUMEN³ Brand Universe abgeschlossen.

Brand Universe:   [BRAND NAME]
Tagline:          "[Tagline]"
WHY:              "To [BEITRAG] so that [WIRKUNG]"
3 Kern-Adjektive: [Wort 1] · [Wort 2] · [Wort 3]
Primary Trigger:  [TRIGGER] (Score: [N])
Neuro-Color:      Primary [Hex] · Secondary [Hex]
Brand Voice Score: [X/10]

5 Deliverables erstellt:
06-brand-universe.md      — Schema 06, vollständige Synthese
slides-brand-universe.md  — Pflicht-Slides + erweiterter Track-Deck
design-brief.md           — Input für Website Creator / Webflow
brand-context.md          — Maschinenlesbarer Connector (YAML + Freitext)
brand-guidelines.md       — Tone, Typografie, Farben, Formatting
[Falls Miro aktiv:] brand-universe Frame auf [URL]

Der Brand Strategist hat seine Arbeit abgeschlossen.
Die Marke hat ein vollständiges, dokumentiertes Universe.

Übergabe Website Creator:  design-brief.md
Übergabe Marketing Skills: brand-context.md
Übergabe Content Team:     brand-guidelines.md
```

---

## SCHRITT 99 — Reflexion und Memory-Block

Nach der Abschluss-Meldung stelle eine Frage:
"Bist du mit diesem Lauf zufrieden? Falls nicht — was hätte besser sein können?"

Frage danach getrennt nach beiden Feldern aus Teil 7:
- **Strategisch:** relevant für spätere Re-Runs der LUMEN³-Skills?
- **Intern:** nur für den Strategen, nicht nach aussen?

Append den Block an `clients/[name]/memory.md` gemäss Format und Kopf aus
`artefact-templates.md` Teil 7. Nur Append, nie Edit.

---

## Was dieser Skill explizit NICHT tut

- Keine eigene Methodik — Skill 06 liest `methodology.md` §§1–5 und die
  Outputs von 01–05, verdichtet, interpretiert nicht neu
- Keine Korrektur von Widersprüchen in den Vorgänger-Outputs — sie werden
  im Konsistenz-Check benannt, aber nicht aufgelöst. Aufgelöst wird durch
  erneutes Laufen der betroffenen Vorgänger-Skills (v2, v3, ...)
- Keine eigene Scoring-Logik — Trigger-Scores kommen unverändert aus Skill 04
- Keine eigenen Farben, Frame-IDs oder Slide-Layouts — alles aus
  `artefact-templates.md`
- Keine Einlese-Bypässe bei Schema-Verletzung — wenn eine Datei
  schema-invalid ist, wird abgebrochen, nicht geraten
- Keine automatische Aktualisierung älterer Versionen — wenn `-v2` oder
  `-v3` existiert, liest Skill 06 immer die höchste Version jeder Vorgänger-Datei
- Keine Miro-Sonderbehandlung bei Ausfall — Markdown-only läuft weiter
  (Miro-Spiegel-Prinzip aus `CLAUDE.md`)
- Liest niemals das interne Feld aus `memory.md` — nur das strategische.
  Auch das strategische Feld nur nach expliziter Nutzer-Freigabe pro Eintrag.
  Reformuliert freigegebene Inhalte ohne Meta-Vokabular ("Reflexion",
  "Feedback", "Memory", "Lessons", "Erkenntnis aus Skill X") und ohne
  Skill-/Versions-Verweise.
