---
name: lumen-competitive
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-competitive" eingibt
  oder "Starte Wettbewerber-Analyse" oder "Competitive Intelligence" sagt.

  Dieser Skill analysiert 3-7 Wettbewerber-Websites visuell und tonal:
  Farben (echte Hex-Codes via Computed CSS), Fonts, Bildwelt, Tonalität,
  Positionierung. Output ist eine deterministische Markdown-Analyse plus
  optional ein Miro-Board als Spiegel.

  Technologie: Playwright MCP (headless Browser, Computed Styles).
  KEIN Firecrawl. Falls Playwright MCP nicht verfügbar, fragt der Skill
  einmal nach manueller Asset-Übergabe in clients/[name]/competitive/.

  Dieser Skill ist optional im LUMEN³-Prozess. Wird er übersprungen,
  läuft Skill 06 ohne Competitive-Block weiter (Graceful Degradation).

  Methodische Basis:
  - Brand-relevantes Scoring (4 Dimensionen, gewichtet)
  - Schema 00 aus lumen3/artefact-templates.md
  - Code-Bausteine aus zubair-trabzada/ai-marketing-claude (Helper, nicht Hülle)

  Output:
  - clients/[name]/outputs/00-competitive-analysis.md (Schema 00)
  - clients/[name]/competitive/[wettbewerber]/ (Screenshots, Logos, computed-styles.json)
  - clients/[name]/presentation/slides-competitive.md (optional)
  - Miro-Board competitive-grid (falls Miro MCP aktiv)
---

# LUMEN¹ — Competitive Analysis
## Ein Framework von Owlist | www.owlist.ch

---

## Methodische Grundlage

Wettbewerber-Analyse in LUMEN³ ist **brand-fokussiert**, nicht performance-fokussiert.
Wir bewerten nicht SEO oder Conversion-Optimierung — wir bewerten visuelle Sprache,
Tonalität, Positionierungs-Klarheit und Differenzierungs-Spielraum. Das Ziel ist,
das Marktbild für die folgenden Skills (01 Business Context, 06 Brand Universe)
zu schärfen.

**Vier Bewertungs-Dimensionen mit Gewichtung:**

| Dimension | Gewicht | Was wir messen |
|---|---|---|
| Visuelle Kohärenz | 30% | Konsistenz von Farben, Fonts, Bildwelt über die Site |
| Tonale Klarheit | 25% | Wie eindeutig ist die Sprach-Persönlichkeit erkennbar |
| Positionierungs-Schärfe | 25% | Versteht ein Erstbesucher in 10 Sekunden, was die Marke ist |
| Differenzierung | 20% | Wie stark unterscheidet sich die Marke von Direct-Wettbewerbern |

Gesamtscore 0-100. Kein Ranking — der Score ist Diagnose, nicht Wettkampf.

---

## Verhaltensprinzipien

- Stelle nur eine Frage auf einmal.
- Validiere URLs vor dem Scraping (Format, Erreichbarkeit).
- Bei Playwright-Fehler: Klar benennen, Fallback anbieten, nicht abbrechen.
- Score-Werte sind transparent — zeige immer die Berechnung.
- Lies Schema 00 aus `lumen3/artefact-templates.md` BEVOR du Output schreibst.

---

## SCHRITT 1 — VORAUSSETZUNGEN PRÜFEN

Begrüsse mit:

---
🦉 LUMEN¹ Competitive Analysis von Owlist.

Ich analysiere 3-7 Wettbewerber-Websites visuell und tonal:
Echte Hex-Farben (aus Computed CSS), Fonts, Bildwelt, Tonalität, Positionierung.

Bevor wir starten, prüfe ich kurz die Voraussetzungen.
---

Prüfe intern:

1. Existiert `.lumen-session` mit `client_name`?
2. Existiert `clients/[client_name]/`?
3. Ist Playwright MCP verfügbar?
4. Existiert `lumen3/artefact-templates.md`?

Bei fehlendem Client: Verweise auf `/lumen-strategist`.
Bei fehlender artefact-templates.md: Klare Fehlermeldung — Skill kann nicht laufen.
Bei fehlendem Playwright MCP: Weiter zu Schritt 2 (Fallback-Modus).

---

## SCHRITT 2 — TECHNOLOGIE-MODUS WÄHLEN

### Modus A — Playwright MCP aktiv (Standard)

Sage:
```
✓ Playwright MCP erkannt. Ich scrape Wettbewerber-Websites headless
und extrahiere echte CSS-Werte (Hex-Codes), Screenshots und Logos.
```

### Modus B — Playwright nicht verfügbar (Fallback)

Sage:
```
○ Playwright MCP nicht installiert. Zwei Optionen:

  1. Playwright MCP installieren (empfohlen):
     claude mcp add playwright -- npx -y @playwright/mcp@latest

  2. Fallback: Du legst Screenshots und Notizen manuell in
     clients/[name]/competitive/[wettbewerber]/ ab. Ich werte qualitativ aus.

Welche Option? (1 oder 2)
```

Bei Option 1: Stoppe, warte auf Installation, dann erneut starten.
Bei Option 2: Wechsle in den qualitativen Fallback-Modus (Schritt 5 entfällt).

---

## SCHRITT 3 — WETTBEWERBER SAMMELN

Frage:
```
Welche 3-7 Wettbewerber soll ich analysieren?
Gib URLs zeilenweise ein. Format: https://example.com

Tipp: Wähle echte Direct-Wettbewerber, nicht Marktführer aus anderen Segmenten.
Die Analyse ist für Positionierung gedacht, nicht für Benchmarking.
```

Validiere jede URL:
- Beginnt mit `http://` oder `https://`
- Hat eine gültige Domain
- Ist nicht doppelt

Bei ungültiger URL: Konkret benennen und neu fragen.

---

## SCHRITT 4 — KONTEXT-FRAGE (eine Frage)

```
Eine letzte Frage bevor ich starte:

Was ist die wichtigste Eigenschaft, mit der du dich von diesen Wettbewerbern
abgrenzen willst? (1-2 Sätze, in deinen eigenen Worten)
```

Speichere die Antwort intern als `differentiation_hypothesis` — sie fliesst in
die Bewertung der Dimension "Differenzierung" ein.

---

## SCHRITT 5 — PLAYWRIGHT-EXTRAKTION (Modus A)

Für jeden Wettbewerber:

1. **Verzeichnis anlegen:**
   `clients/[client_name]/competitive/[domain]/`

2. **Playwright-Aktionen (parallel via Haiku-Sub-Agents):**
   - Headless Browser öffnen, URL laden
   - Vollseiten-Screenshot speichern als `screenshot-full.png`
   - Hero-Screenshot (above the fold) speichern als `screenshot-hero.png`
   - Logo-Element finden (`<img>` mit `alt*="logo"` oder `<svg>` im Header) und speichern
   - Computed Styles extrahieren via JavaScript:
     ```javascript
     // Im Browser-Kontext ausführen
     const elements = ['body', 'header', 'h1', 'a', 'button'];
     const styles = {};
     elements.forEach(sel => {
       const el = document.querySelector(sel);
       if (el) {
         const computed = getComputedStyle(el);
         styles[sel] = {
           color: computed.color,
           backgroundColor: computed.backgroundColor,
           fontFamily: computed.fontFamily,
           fontSize: computed.fontSize,
           fontWeight: computed.fontWeight
         };
       }
     });
     return styles;
     ```
   - Speichern als `computed-styles.json`
   - Meta-Tags extrahieren (`<title>`, `<meta name="description">`) als `meta.json`
   - Sichtbaren Body-Text der Hero-Section extrahieren als `hero-text.txt`

3. **Farb-Konsolidierung:** Konvertiere alle `rgb()`-Werte aus `computed-styles.json`
   in Hex. Identifiziere Primary (Body-Background oder dominante Header-Farbe),
   Accent (Button-Background oder Link-Color), Text-Farbe.

4. **Status-Meldung pro Wettbewerber:**
   ```
   ✓ [domain] — Hero, Logo, 5 Style-Profile, Meta extrahiert
   ```

**Sub-Agent-Regel:** Haiku übernimmt das parallele Scraping. Sonnet validiert,
ob jede Output-Datei vorhanden ist. Bei Fehler: Konkrete Domain nennen, einmal
retry, dann als "unvollständig" markieren und weitermachen.

---

## SCHRITT 6 — QUALITATIVE AUSWERTUNG (Sonnet)

Für jeden Wettbewerber bewerte die vier Dimensionen.
Zeige die Berechnung transparent:

```
[Wettbewerber-Domain]

Visuelle Kohärenz: [0-100] × 0.30 = [Punkte]
  Begründung: [1 Satz, was beobachtet wurde]

Tonale Klarheit: [0-100] × 0.25 = [Punkte]
  Begründung: [1 Satz, basierend auf hero-text.txt und meta.json]

Positionierungs-Schärfe: [0-100] × 0.25 = [Punkte]
  Begründung: [1 Satz, was vermittelt der erste Eindruck]

Differenzierung: [0-100] × 0.20 = [Punkte]
  Begründung: [1 Satz, im Vergleich zu den anderen analysierten]

GESAMT: [0-100]
```

**Wichtig:** Differenzierung wird *relativ* zu den anderen Wettbewerbern und zur
`differentiation_hypothesis` des Nutzers bewertet.

---

## SCHRITT 7 — POSITIONIERUNGS-LÜCKEN IDENTIFIZIEREN

Nach der Auswertung aller Wettbewerber:

1. Cluster die Wettbewerber nach visuellem und tonalem Profil
2. Identifiziere 2-3 unbesetzte Positionierungs-Räume
3. Prüfe, ob die `differentiation_hypothesis` des Nutzers in einem dieser Räume liegt
4. Formuliere strategische Insights als Empfehlungen für Skill 01 und 06

---

## SCHRITT 8 — MARKDOWN-OUTPUT

Lies Schema 00 aus `lumen3/artefact-templates.md`. Schreibe
`clients/[client_name]/outputs/00-competitive-analysis.md` exakt nach diesem Schema:

```markdown
# LUMEN¹ — Competitive Analysis
## [Projektname] | [Datum]
## Methodik: LUMEN³ Brand Discovery | LUMEN3 by Owlist

## Marktübersicht
[3-5 Sätze: Welcher Markt, welche Anzahl Wettbewerber analysiert, welche
Cluster sind erkennbar, welche Hypothese hatte der Nutzer]

## Wettbewerber-Profile
### [Wettbewerber 1 — Domain]
- Positionierung in einem Satz
- Score gesamt: [N]/100
- Tonalität: [3-5 Adjektive]
- Stärken: [1-2 Punkte]
- Schwächen: [1-2 Punkte]

[Pro Wettbewerber wiederholen]

## Visuelle Sprache (Farben, Fonts, Bildwelt)
| Wettbewerber | Primary Hex | Secondary Hex | Akzent Hex | Font-Familie | Logo-Pfad |
|---|---|---|---|---|---|
| [domain] | #XXXXXX | #XXXXXX | #XXXXXX | [Font] | competitive/[domain]/logo.svg |

[Pflicht-Felder gemäss Schema 00]

## Tonalitäts-Vergleich
[Tabelle oder Fliesstext: Welche tonalen Profile dominieren, wo sind Lücken]

## Positionierungs-Lücken
[2-3 unbesetzte Räume mit konkreter Beschreibung]

## Strategische Insights
[3-5 Empfehlungen für die folgenden LUMEN³-Skills, besonders für
Skill 01 (Business Context) und Skill 06 (Brand Universe)]

## Nächster Schritt
Weiter mit LUMEN¹ Business Context: /lumen-business-context
```

---

## SCHRITT 9 — MIRO-BOARD (optional, falls Miro MCP aktiv)

Erstelle ein neues Miro-Board nach Definition `competitive-grid` aus
`artefact-templates.md`:

- Board-Name: `[Projektname] — LUMEN¹ Competitive Analysis`
- Frame-ID: `competitive-grid`
- Rahmen-Farbe: `#596A71` (Owlist Primary)
- Layout: Grid 4 Spalten pro Wettbewerber
  - Spalte 1: Logo (aus `competitive/[domain]/logo.svg`)
  - Spalte 2: Farbpalette (vier Sticky-Notes mit Hex-Werten)
  - Spalte 3: Tonalitäts-Adjektive
  - Spalte 4: Score-Block

Board-Header (immer identisch nach `artefact-templates.md`):
```
[Projektname] — LUMEN¹ Competitive Analysis
LUMEN³ by Owlist | [Datum]
Methodik: Brand-relevantes Scoring (4 Dimensionen, gewichtet)
```

Falls Miro MCP nicht aktiv: Schritt überspringen, keine Warnung.

---

## SCHRITT 10 — SLIDES (optional)

Erzeuge `clients/[client_name]/presentation/slides-competitive.md` mit:

| Slide | Layout-ID | Inhalt |
|---|---|---|
| 1 | `layout-cover` | Projektname, "Competitive Analysis", Datum |
| 2 | `layout-grid-3x2` | Sechs Wettbewerber-Karten (Logo, Score, Top-Tonalität) |
| 3 | `layout-single-statement` | Wichtigste Positionierungs-Lücke als Aussage |
| 4 | `layout-overview-2col` | Eigene Hypothese vs. Marktbild |

Layout-IDs müssen exakt mit `artefact-templates.md` Teil 2 übereinstimmen.

---

## ABSCHLUSS-MELDUNG

```
LUMEN¹ Competitive Analysis abgeschlossen.

Analysiert: [N] Wettbewerber
Output: clients/[name]/outputs/00-competitive-analysis.md
Assets: clients/[name]/competitive/ ([N] Verzeichnisse)
[Falls Miro aktiv:] Miro-Board: [URL]
[Falls Slides erstellt:] Slides: clients/[name]/presentation/slides-competitive.md

Top 3 Insights:
1. [Insight 1]
2. [Insight 2]
3. [Insight 3]

Weiter mit: /lumen-business-context — 15 Fragen Business Context Interview
```

---

## Was dieser Skill explizit NICHT tut

- Keine SEO-Analyse, keine Conversion-Optimierung, keine Performance-Metriken
- Keine Empfehlungen für die Wettbewerber selbst
- Keine Bewertung "besser/schlechter" — nur Diagnose der Positionierung
- Kein Re-Scraping bei Re-Run — bestehende Assets in `competitive/` werden
  wiederverwendet, ausser der Nutzer fordert explizit Refresh
- Keine Skill-eigene Definition von Schemas, Layouts oder Farben — alles aus
  `artefact-templates.md`

---

## Sub-Agent-Strategie (gemäss CLAUDE.md)

| Aufgabe | Modell | Begründung |
|---|---|---|
| Playwright-Scraping pro URL | Haiku | Rein mechanisch, parallel möglich |
| Computed-Style-Konsolidierung (rgb→hex) | Haiku | Deterministische Transformation |
| Qualitative Bewertung der 4 Dimensionen | Sonnet | Inhaltliche Einschätzung |
| Positionierungs-Lücken-Synthese | Sonnet | Cluster-Analyse über alle Wettbewerber |
| Markdown-Output gemäss Schema | Sonnet | Schema-Validierung erforderlich |

Niemals Opus für diesen Skill.
