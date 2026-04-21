# LUMEN³ — Vollständiges Paket | Stand 21. April 2026

> **Neu hier?** Lies zuerst **[README.md](README.md)** (Framework-Übersicht) oder
> **[GETTING-STARTED.md](GETTING-STARTED.md)** (Schritt-für-Schritt-Anleitung für
> komplette Einsteiger). Dieses Dokument ist die Paket-Referenz für bestehende
> Nutzer, die Updates einspielen.

## Status: LUMEN³ v1.5 (21. April 2026) — Brand Visual System

**Neu in v1.5:** Skill 07 (`/lumen-visual-system`) überführt das strategische
Brand Universe in ein vollständiges visuelles System — Logo-Varianten, Farb-/
Typo-Tokens (Hex, Font-Familien, Scales), Icons, Print- und Digital-Applications,
und abschliessend ein `DESIGN.md` im 10-Abschnitte-Format (über den externen
Skill `design-md-generator`). Sechs Phasen sequenziell, Sonnet-Standard,
Sub-Brand-Variante via `parent-brand`-Parameter, Memory-Block-Pflicht.

**Erweitert:**
- **Skill 06** (v1.5 → v1.6): Neue Section `visual_direction` in `brand-context.md`
  liefert strategische Richtungen (color_bias, type_character, imagery_direction,
  layout_rhythm, do/dont) — bewusst KEINE Hex-Werte oder Font-Namen. Diese
  Konkretisierung passiert ausschliesslich in Skill 07.
- **Skill 00** (v2.1 → v2.2): Neuer Sub-Schritt 5.7 aktiviert
  `design-md-generator` pro gescraptem Wettbewerber und legt eine `DESIGN.md`
  in `competitive/[domain]/` ab. Optional analog Miro-MCP.
- **CLAUDE.md** (v1.4 → v1.5): Neue Verhaltensregel 13 (Visual-Tokens bleiben
  bei Skill 07). Trigger-Tabelle um Skill 07 ergänzt.

**Vorangegangene Sprints (unverändert):** Sprint 1 (Refactor), Sprint 2
(Memory-System), Sprint 3 (Creative Footprint — 123 Datenpunkte Enigma),
Sprint 4 (Claude-Design-Integration v2.1) — Details unter "Changelog-Chronik"
weiter unten.

Neu: Python-Helper `scripts/analyze_page.py` für SEO- und Marketing-Audit-
Datenpunkte (MIT-lizenziert, adaptiert von zubair-trabzada/ai-marketing-claude).

## Struktur

```
lumen3-package/
├── README-PACKAGE.md            ← Diese Datei
│
├── CLAUDE.md                    ← v1.5 (Verhaltensregel 13 + Skill 07 im Trigger-Index)
├── artefact-templates.md        ← v1.2 (Schema 00 Full Potential, unverändert in v1.5)
├── methodology.md               ← v1.1 (§6 Dietrich PESO + Enigma ergänzt)
├── trigger-mapping.md           ← unverändert (Single Source of Truth)
│
├── scripts/                     ← NEU (Sprint 3)
│   └── analyze_page.py          ← HTML/SEO/Marketing-Analyzer (MIT, adaptiert)
│
└── skills/
    ├── lumen-bootstrap.md                 v1.3 (unverändert)
    ├── lumen-strategist.md                v1.3+ (Memory-Status in Phase 1 + Variante B)
    ├── lumen-learn.md                     v1.0 (Helper, Memory-Mustererkennung)
    ├── 00-competitive-analysis.md         v2.2 (design-md-generator pro Wettbewerber, Schritt 5.7)
    ├── 00-datapoints.md                   v2.0 (NEU — 123 Datenpunkt-Definitionen)
    ├── 00-competitive-analysis.v1-backup.md  v1.0 (Backup, kann später entfernt werden)
    ├── 01-business-context.md             v1.4 (Memory Schritt 0 + 99)
    ├── 02-brand-archetype.md              v1.4 (Memory Schritt 0 + 99)
    ├── 03-brand-interview.md              v1.4 (Memory-Pilot)
    ├── 04-trigger-analysis.md             v1.4 (Memory Schritt 0 + 99)
    ├── 05-story-identity.md               v1.4 (Memory Schritt 0 + 99)
    ├── 06-brand-universe.md               v1.6 (Visual Direction Tokens in brand-context.md)
    └── 07-brand-visual-system.md          v1.0 (NEU — Brand Visual System, 6 Phasen)
```

## Versions-Übersicht

| Datei | Version | Status |
|---|---|---|
| **CLAUDE.md** | **1.5** | **✓ NEU Verhaltensregel 13 + Skill 07 im Trigger-Index** |
| artefact-templates.md | 1.2 | ✓ Schema 00 Full Potential |
| methodology.md | 1.1 | ✓ §6 Dietrich/Enigma |
| trigger-mapping.md | unverändert | ✓ |
| scripts/analyze_page.py | 1.0 | ✓ NEU (MIT-adaptiert) |
| lumen-bootstrap.md | 1.3 | ✓ |
| lumen-strategist.md | 1.3+ | ✓ Memory-Status |
| lumen-learn.md | 1.0 | ✓ |
| **00-competitive-analysis.md** | **2.2** | **✓ design-md-generator pro Wettbewerber (5.7)** |
| 00-datapoints.md | 2.0 | ✓ 123 Datenpunkte |
| 01-business-context.md | 1.4 | ✓ Memory |
| 02-brand-archetype.md | 1.4 | ✓ Memory |
| 03-brand-interview.md | 1.4 | ✓ Memory-Pilot |
| 04-trigger-analysis.md | 1.4 | ✓ Memory |
| 05-story-identity.md | 1.4 | ✓ Memory |
| **06-brand-universe.md** | **1.6** | **✓ Visual Direction Tokens in brand-context.md** |
| **07-brand-visual-system.md** | **1.0** | **✓ NEU — Brand Visual System, 6 Phasen** |

## Vier Single Sources of Truth (SoT)

LUMEN³ hat vier zentrale Dateien, aus denen alle Skills lesen.
Skills definieren NIEMALS eigene Schemas, Tokens, Frames oder Methodik-Quellen.

| Datei | Inhalt |
|---|---|
| `CLAUDE.md` | Globale Regeln, Modell-Routing, Sub-Agent-Strategie, Miro-Spiegel-Prinzip |
| `artefact-templates.md` | Markdown-Schemas (00–06), Slide-Layouts, Miro-Frames, Owlist Brand-Tokens, Validierungs-Regeln (Teil 5) |
| `methodology.md` | Wissenschaftliche Quellen in 5 Paragraphen (§1 Aaker/Meyerson, §2 Pearson/Hogshead, §3 Damasio/Zaltman, §4 Card Sort, §5 Haller/Neuro-Color) |
| `trigger-mapping.md` | Adjektiv→Trigger-Mapping, deterministische Scoring-Regeln |

## Refactor-Muster (einheitlich für alle Skills)

Alle v1.3-Skills folgen diesem Muster:

1. **Frontmatter** mit Versions-Hinweis und Verweis auf SoT-Dateien
2. **Voraussetzungs-Block** am Anfang (welche Dateien werden gebraucht)
3. **Methodik-Verweis** statt Inline-Erklärung: *"Methodische Basis: §X, siehe `methodology.md`"*
4. **Schema-Verweis** statt eigener Definition: *"Lies Schema X aus `artefact-templates.md`"*
5. **Frame/Layout-Verweise** statt eigener Farben: *"Frame `xyz` aus `artefact-templates.md` Teil 3"*
6. **"Was dieser Skill explizit NICHT tut"** am Ende

## Zweiter Refactor-Durchlauf — Zusammenfassung (11. April 2026)

Dieser Durchlauf hat die fünf verbleibenden Skills aus `skills-todo/`
nach denselben Regeln aufgeräumt:

| Skill | Zeilen alt | Zeilen neu | Delta | Besonderheiten |
|---|---|---|---|---|
| 01-business-context.md | 215 | 246 | +14% | Kein Methodik-Ballast zu cutten; Zuwachs durch neue Pflicht-Blöcke |
| 02-brand-archetype.md | 1214 | 1006 | −17% | Hogshead/Pearson-Erklärung raus, Schema 02 mit Primary/Secondary/Dormant/Shadow, matrix.html unverändert |
| 05-story-identity.md | 641 | 554 | −14% | Sinek-Kern bleibt, neuer Neuro-Color-Block mit optionalem OpenRouter-API-Call |
| 06-brand-universe.md | 750 | 506 | −33% | Vier externe Framework-Erklärungen raus, Schema-Validierung als Pflicht-Schritt, 31 Track-Slides mit Layout-IDs |
| lumen-strategist.md | 341 | 358 | +5% | Touch-Up: neuer SoT-Verweis-Block |

**Gesamt:** 3161 → 2670 Zeilen (−16%). Im Zielkorridor.

### Inhaltliche Klarstellungen aus diesem Durchlauf

**Skill 05 — OpenRouter und Neuro-Color neu integriert.** Die alte Version
enthielt nur Sinek Golden Circle + Dante Labs, ohne Haller oder Neuro-Color.
Schema 05 und methodology.md §5 verlangen aber eine `Farb-Empfehlung (Neuro-Color)`.
Der Refactor behält den Sinek-Kern und ergänzt einen neuen Teil-B4-Block mit
einem 4-Schritte-Verfahren: Trigger einlesen → optionale Live-Recherche via
OpenRouter (Perplexity Sonar Pro, Fallback bei fehlendem Key) → statische
Haller-Trigger-Farbtabelle → Kulturkontext-Frage. Das macht den Skill
schema-konform ohne den bestehenden Workflow zu brechen.

**Skill 02 — H1 von LUMEN² auf LUMEN¹ geändert.** Schema 02 in
`artefact-templates.md` verlangt `# LUMEN¹ — Brand Archetype`. Die alte
Datei nutzte `LUMEN²`. Korrigiert.

**Skill 06 — Schema-Validierung als Schritt 1 vor dem Einlesen.** Neue
Regel: Vor dem inhaltlichen Einlesen jeder Vorgänger-Datei (01–05) wird
das Schema gegen `artefact-templates.md` Teil 5 validiert. Bei Verletzung
Abbruch mit konkreter Fehlermeldung (Datei, Problem, Lösung = betroffenen
Skill als v2 neu laufen lassen).

**Skill 06 — Track-Deck bleibt, aber mit Layout-ID-Referenzen.** Die
Owlist Visual Universe Struktur mit 31 Slides in 7 Tracks ist operativ
nützlich und bleibt vollständig erhalten. Jede Slide referenziert jetzt
eine Layout-ID aus `artefact-templates.md` Teil 2 (`layout-cover`,
`layout-single-statement`, `layout-grid-3x2`, `layout-trigger-bar`,
`layout-overview-2col`). Keine eigenen Layouts mehr.

## Sprint 2 — Memory-System (11. April 2026)

Dieser Sprint hat ein Memory-System ergänzt, damit Skills Lessons aus
vorherigen Läufen berücksichtigen können und ein Helper-Skill Muster über
alle Kunden hinweg erkennt.

### Die sieben Backlog-Items

| # | Item | Datei | Delta |
|---|---|---|---|
| 1 | Memory-Schema | artefact-templates.md Teil 7 | +106 Z (308→414) |
| 2 | Memory-Prinzip global | CLAUDE.md v1.4 | +32 Z (227→259) |
| 3 | Memory-Pilot | 03-brand-interview.md v1.4 | +32 Z (301→333) |
| 4 | Test-Simulation | — | manuell beim Nutzer |
| 5 | Skills 01/02/04/05/06 | Bulk-Rollout v1.4 | +33/+33/+33/+33/+56 Z |
| 6 | Helper-Skill | lumen-learn.md v1.0 | +180 Z (neu) |
| 7 | Memory-Status | lumen-strategist.md | +3 Z (358→361) |

**Gesamt-Ergänzung Sprint 2:** +528 Zeilen über alle betroffenen Dateien.

### Memory-Mechanik in einer Zeile

Jeder Skill schreibt nach Abschluss einen Block in `clients/[name]/memory.md`
(append-only, zwei Felder: strategisch + intern). Beim Re-Run liest der
Skill die Blöcke zur Vorgänger-Version und fragt den Nutzer nach Berücksichtigung.
Skill 06 liest alle Projekt-Blöcke, bittet um Freigabe pro Eintrag und
übernimmt freigegebene strategische Inhalte in die optionale Section
`## Strategische Anmerkungen aus dem Prozess` — reformuliert ohne
Meta-Vokabular. `/lumen-learn` analysiert Muster über alle Kunden hinweg
(Schwelle: 10 Einträge pro Skill für aussagekräftige Musteranalyse, läuft
aber immer und zeigt Skills unter Schwelle als Zeile mit Einträge-Zähler).

### Sicherheits-Test Skill 06 — bestanden

Statischer Lese-Test: Die Wörter „Reflexion", „Feedback", „Memory", „Lessons"
erscheinen in Skill 06 nur in **Instruktionen** an den Skill (SCHRITT 0
Reformulierungs-Verbot, SCHRITT 99 Überschrift, NICHT-Block). In keinem
Output-Template (Header, Pflicht-Sections-Liste, Optionale-Sections-Liste,
YAML, Abschluss-Meldung) taucht auch nur eines dieser Wörter auf. Die
optionale Section heisst neutral „Strategische Anmerkungen aus dem Prozess".

### Offene TODOs (nicht blockierend)

- Skill 05 Miro-Frames (`golden-circle`, `story-tonality`) sind im Skill
  inline definiert, gehören aber bei nächstem Minor-Bump in
  `artefact-templates.md` Teil 3 als zentrale Frame-IDs aufgenommen.
- Skill 02 `matrix.html` und `slides-outline.md` sind skill-spezifische
  Outputs ausserhalb von Schema 02. Wenn das irgendwann einheitlich
  werden soll, muss Schema 02 in Teil 1 erweitert werden.
- Skill 06 bei +56 Zeilen leicht über dem Budget von +30 — Grund: die
  Freigabe-Mechanik für alle Projekt-Blöcke plus Reformulierungs-Regel
  braucht explizite Instruktionen. Nicht verkürzbar ohne Qualitätsverlust.
- `lumen3/learnings/` Ordner existiert initial nicht — `/lumen-learn`
  legt ihn beim ersten Lauf an.
- Skill 03 Test-Simulation mit drei Iterationen macht der Nutzer manuell
  in einer echten Session.

## Sprint 3 — Creative Footprint (11. April 2026)

Sprint 3 hat Skill 00 vollständig neu geschrieben, um die Enigma Creative
Footprint Methodik (2022) strukturell zu implementieren. Der alte v1.0-Skill
arbeitete mit einer vereinfachten 4-Dimensionen-Heuristik, die beim Refactor
aus methodischer Unachtsamkeit entstanden war.

**Die Backlog-Items von Sprint 3:**

| # | Item | Datei | Delta |
|---|---|---|---|
| 1 | Methodology-Quelle ergänzen | methodology.md §6 | +98 Z (250→348) |
| 2 | Schema 00 erweitern | artefact-templates.md | ca. +25 Z (Schema 00 komplett neu) |
| 3 | Skill 00 v2.0 schreiben | 00-competitive-analysis.md | 378 → 560 Z (+48 %) |
| 4 | 123 Datenpunkte definieren | 00-datapoints.md (neu) | +700 Z |
| 5 | Python-Helper integrieren | scripts/analyze_page.py (neu) | +475 Z (MIT-adaptiert) |
| 6 | Gap-Report Skills 01–06 | _Archiv/skills/_review | +250 Z |

**Methodische Kern-Änderungen in Skill 00 v2.0:**

- Scoring-Basis: **4 Dimensionen → 5 Dimensionen** (PESO + Assets-Erweiterung von Enigma)
- Anzahl Datenpunkte: **unstrukturiert → 123 kuratierte Datenpunkte**
- Dimensions-Gewichtung: **heuristisch → Assets 44 % / Paid 6 % / Earned 14 % / Shared 11 % / Owned 25 %**
- Skill-Phasen: **1 → 4** (Rohdaten / Scoring / Visuelle Analyse / Synthese+Output)
- Phase 2 neu: **4 visuelle Analyse-Module** (Farbrad, Font-Tabelle, Namens-Archetypen, Tagline-Quadrant)
- Python-Helper `analyze_page.py` für technische SEO- und Marketing-Datenpunkte

**Historischer Kontext:** Die 139-Datenpunkt-Methodik wurde von Enigma Swiss
(Bern) am 03.05.2022 im Creative Footprint Workshop für Thought Leader &
Partner entwickelt — dem Unternehmen, aus dem später Owlist wurde. LUMEN³ v2
hat die 139 Datenpunkte auf 123 kuratiert (redundanzfreie Schärfung).

## Installation in bestehendes LUMEN³ Projekt

1. Backup deines aktuellen `lumen3/` Verzeichnisses machen
2. Vier Root-Dateien nach `lumen3/` kopieren (`CLAUDE.md`, `artefact-templates.md`, `methodology.md`, `trigger-mapping.md`)
3. `scripts/`-Ordner nach `lumen3/scripts/` kopieren
4. Alle elf Skill-Dateien aus `skills/` nach `lumen3/.claude/skills/[name]/SKILL.md` (inklusive `00-competitive-analysis.md` v2.0 und `00-datapoints.md`)
5. Playwright installieren: `claude mcp add playwright -- npx -y @playwright/mcp@latest`
6. Python 3 verifizieren: `python3 --version` (benötigt für `scripts/analyze_page.py`)
7. `.env` anpassen: `OPENROUTER_API_KEY=...` (optional, nur für Skill 05 Neuro-Color Live-Recherche)
8. Sanity-Check: `/lumen-bootstrap`

Das `00-competitive-analysis.v1-backup.md` kann nach erfolgreichem Test-Lauf
entfernt werden.

## Credits & Lizenz-Hinweise

**Methodische Quellen** (in `methodology.md` dokumentiert): Jennifer Aaker (1997),
Rob Meyerson (2012), Carol S. Pearson & Margaret Mark (2001), Sally Hogshead
(2014), Antonio Damasio (1994), Gerald Zaltman (2003), Simon Sinek (2009),
Jim Collins (2001), Gini Dietrich (2014), Enigma Swiss Creative Footprint
Workshop (2022), Karen Haller (2019), Dante Labs Positioning Framework,
Focus Lab Stress Test, Jakob Nielsen / Nielsen Norman Group Card Sorting.

**Übernommener Code:**

- `scripts/analyze_page.py` ist adaptiert aus
  [`zubair-trabzada/ai-marketing-claude`](https://github.com/zubair-trabzada/ai-marketing-claude)
  (MIT License, Copyright 2026 Zubair Trabzada). Der vollständige
  MIT-Copyright-Vermerk ist im Datei-Header erhalten. LUMEN³-Anpassungen
  sind Copyright 2026 Owlist GmbH, ebenfalls unter MIT.

**LUMEN³ selbst** ist proprietäres Framework von Owlist GmbH. Verwendung zu
Schulungs- und Beratungszwecken im Rahmen von LUMEN³-Lizenzvereinbarungen
gestattet.
