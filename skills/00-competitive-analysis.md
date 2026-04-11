---
name: lumen-competitive
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-competitive" eingibt
  oder "Starte Wettbewerber-Analyse" oder "Creative Footprint" sagt.

  Dieser Skill führt die Full Potential Analyse nach dem Enigma
  Creative Footprint Process (2022) durch — 123 Datenpunkte in 5
  Dimensionen (PESO + Assets-Erweiterung), plus eine visuelle
  Analyse des Wettbewerbsumfelds (Farbrad, Font-Tabelle, Namens-
  Archetypen, Tagline-Quadrant).

  Output ist eine deterministische Markdown-Analyse plus
  Positionierungs-Lücken-Synthese. Optional: Miro-Board als Spiegel,
  Slide-Set für Präsentation.

  Technologie: Playwright MCP (headless Browser, Computed Styles,
  Screenshots) plus Python-Helper-Scripts für SEO, Performance, Meta.
  Falls Playwright nicht verfügbar, fragt der Skill einmal nach
  manueller Asset-Übergabe in clients/[name]/competitive/.

  Dieser Skill ist optional im LUMEN³-Prozess. Wird er übersprungen,
  läuft Skill 06 ohne Competitive-Block weiter (Graceful Degradation).

  Methodische Basis: §6 (Dietrich PESO + Enigma Creative Footprint),
  siehe methodology.md
  Schemas, Layouts, Tokens: artefact-templates.md

  Output:
  - clients/[name]/outputs/00-competitive-analysis.md (Schema 00)
  - clients/[name]/competitive/[domain]/ (Screenshots, Logos, computed-styles.json, scores.json)
  - clients/[name]/competitive/_synthesis/farbrad.svg, fonts.svg, names.svg, taglines.svg
  - clients/[name]/presentation/slides-competitive.md (optional)
  - Miro-Board competitive-grid (falls Miro MCP aktiv)

  Version 2.0 — April 2026 (Enigma-Alignment)
---

# LUMEN¹ — Creative Footprint Full Potential Analyse
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 00, Visual-Module-Layouts, Slide-Set, Teil 7 Memory)
- `lumen3/methodology.md` (§6 — Dietrich PESO + Enigma Creative Footprint)
- `lumen3/trigger-mapping.md` (Trigger-Farb-Zuordnung für Neuromarketing-Datenpunkte in Phase 1)
- `clients/[name]/` als Zielordner für Outputs und Memory
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Methodische Basis: §6 (Dietrich 2014 + Enigma 2022). Verweise dem Nutzer auf
`methodology.md` nur dann, wenn er explizit nach der wissenschaftlichen Quelle
fragt. Die didaktische Erklärung gehört nicht in diese Skill-Datei.

---

## Methodische Grundlage

LUMEN³ nutzt die Full Potential Analyse von Enigma Swiss (Mai 2022), entwickelt
im Rahmen des Creative Footprint Workshops für Thought Leader & Partner
(später Owlist). Die Methode ergänzt Gini Dietrichs PESO-Modell (2014) um eine
fünfte Dimension **Assets** — die nicht-medialen Markenwerte.

**5 Dimensionen, 123 Datenpunkte, 3-Punkt-Skala (0/1/2), normiert auf 100.**

| Dimension | Datenpunkte | Gewicht | Inhalt |
|---|---|---|---|
| Assets | 54 | 44% | Brand Evolution, Why/How/What, Neuromarketing, Brand Toolbox, Brand Story |
| Paid Media | 8 | 6% | Channels, Tracking, Funnel Coverage |
| Earned Media | 17 | 14% | Google News, Influencer, Media Corner, Social Proof |
| Shared Media | 14 | 11% | Facebook, Instagram, LinkedIn, Twitter/X, TikTok |
| Owned Media | 30 | 25% | Newsletter, Content Strategy, Performance, SEO, Mobile UX, Security |

**Vollständige Datenpunkt-Definition:** `skills/00-datapoints.md` (123 Datenpunkte mit Scoring-Kriterien pro 0/1/2-Stufe).

**Ehrlichkeits-Hinweis:** Das Enigma-Original dokumentierte 139 Datenpunkte. LUMEN³
v2 arbeitet mit 123 kuratierten, redundanzfreien Datenpunkten in derselben
5-Dimensionen-Struktur. Das ist Schärfung, keine Abschwächung.

---

## Verhaltensprinzipien

- **Stelle nur eine Frage auf einmal.**
- Validiere URLs vor dem Scraping (Format, Erreichbarkeit).
- Bei Playwright-Fehler: Klar benennen, Fallback anbieten, nicht abbrechen.
- Datenpunkt-Scores sind transparent — zeige auf Rückfrage immer die Berechnung.
- Lies Schema 00 aus `lumen3/artefact-templates.md` BEVOR du Output schreibst.
- Nutze Sub-Agents (Haiku) für parallele Scraping-Tasks, Sonnet für inhaltliche Bewertung.
- Phase 1 (Scoring) und Phase 2 (Visuelle Analyse) laufen parallel, wo möglich.

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/00-competitive-analysis.md` nicht: weiter mit
SCHRITT 1, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 00 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## SCHRITT 1 — Voraussetzungen prüfen

Begrüsse mit:

```
🦉 LUMEN¹ Creative Footprint — Full Potential Analyse nach Enigma (2022).

Ich analysiere 3–7 Wettbewerber auf 123 Datenpunkten in 5 Dimensionen
(Assets, Paid, Earned, Shared, Owned) und zeichne dir das visuelle
Wettbewerbsumfeld (Farbe, Schrift, Namen, Taglines).

Der Durchlauf dauert je nach Anzahl 30–90 Minuten. Du kannst pausieren
und später weitermachen.

Bevor wir starten, prüfe ich die Voraussetzungen.
```

Prüfe intern:

1. Existiert `.lumen-session` mit `client_name`?
2. Existiert `clients/[client_name]/`?
3. Ist Playwright MCP verfügbar?
4. Existiert `lumen3/artefact-templates.md` mit Schema 00?
5. Existiert `lumen3/methodology.md` §6?

Bei fehlendem Client: Verweise auf `/lumen-strategist`.
Bei fehlender artefact-templates.md oder methodology.md §6: Klare Fehlermeldung — Skill kann nicht laufen.
Bei fehlendem Playwright MCP: Weiter zu SCHRITT 2 (Fallback-Modus).

---

## SCHRITT 2 — Technologie-Modus wählen

### Modus A — Playwright MCP aktiv (Standard)

```
✓ Playwright MCP erkannt. Ich scrape Wettbewerber-Websites headless
und extrahiere echte CSS-Werte, Screenshots, Meta-Daten und
Performance-Metriken. Parallelisierung via Haiku-Sub-Agents.
```

### Modus B — Playwright nicht verfügbar (Fallback)

```
○ Playwright MCP nicht installiert. Zwei Optionen:

  1. Playwright MCP installieren (empfohlen):
     claude mcp add playwright -- npx -y @playwright/mcp@latest

  2. Fallback: Du legst Screenshots und ein ausgefülltes Scoring-
     Template manuell in clients/[name]/competitive/[domain]/ ab.
     Ich bewerte dann qualitativ (Phase 2 läuft, Phase 1 reduziert).

Welche Option? (1 oder 2)
```

Bei Option 1: Stoppe, warte auf Installation, dann erneut starten.
Bei Option 2: Wechsle in den qualitativen Fallback-Modus.

---

## SCHRITT 3 — Wettbewerber sammeln

Frage:

```
Welche 3–7 Wettbewerber soll ich analysieren?
Gib URLs zeilenweise ein. Format: https://example.com

Tipp: Wähle echte Direct-Wettbewerber, nicht Marktführer aus anderen
Segmenten. Die Analyse ist für Positionierung gedacht, nicht für
Benchmarking gegen unerreichbare Marken.

Maximal 7 — jeder zusätzliche Wettbewerber verdünnt die Muster statt
sie zu schärfen.
```

Validiere jede URL:
- Beginnt mit `http://` oder `https://`
- Hat eine gültige Domain
- Ist nicht doppelt erfasst

Bei ungültiger URL: Konkret benennen und neu fragen.

---

## SCHRITT 4 — Kontext-Fragen (zwei Fragen, nacheinander)

**Frage 1:**
```
Was ist die wichtigste Eigenschaft, mit der du dich von diesen Wettbewerbern
abgrenzen willst? (1–2 Sätze, in deinen eigenen Worten)
```

**Frage 2 (nach Antwort auf F1):**
```
Welche 3 Core-Keywords rankst du (oder willst du ranken)? Diese nutze ich
für den SEO-Datenpunkt O.SE.05 in der Messung.
```

Speichere intern:
- `differentiation_hypothesis` (F1 → fließt in Synthese Phase 3)
- `core_keywords` (F2 → fließt in Datenpunkt O.SE.05)

---

## SCHRITT 5 — Phase-1-Extraktion: Rohdaten sammeln (Playwright + Helper)

Für jeden Wettbewerber parallel (Haiku-Sub-Agents):

### 5.1 Playwright-Aktionen

1. **Verzeichnis anlegen:**
   `clients/[client_name]/competitive/[domain]/`

2. **Headless Browser:**
   - Vollseiten-Screenshot → `screenshot-full.png`
   - Hero-Screenshot (above the fold) → `screenshot-hero.png`
   - Mobile-Viewport-Screenshot (375×667) → `screenshot-mobile.png`
   - Logo-Element (`<img alt*="logo">` oder `<svg>` im Header) → `logo.svg` oder `logo.png`

3. **Computed Styles extrahieren:**
   ```javascript
   const elements = ['body', 'header', 'h1', 'h2', 'h3', 'a', 'button', 'p', 'footer'];
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
         fontWeight: computed.fontWeight,
         fontStyle: computed.fontStyle
       };
     }
   });
   return styles;
   ```
   → `computed-styles.json`

4. **Meta-Tags + Hero-Text:**
   - `<title>`, `<meta name="description">`, `<meta property="og:*">`
   - H1, H2 Text-Inhalt
   - Hero-Section Body-Text (erste 500 Zeichen über the fold)
   - Footer-Text (Claim, Tagline, Contact-Info)
   → `meta.json`, `hero-text.txt`, `footer-text.txt`

5. **Link-Inventur:**
   - Alle sichtbaren Navigationslinks
   - Social-Media-Links aus Footer/Header
   - Newsletter-Opt-in erkennbar?
   - Press-Kit-Seite (/presse, /media, /press, /news)
   → `links.json`, `social-profiles.json`

### 5.2 Performance-Metriken (Lighthouse)

Rufe Lighthouse im Playwright-Kontext auf (oder via Python-Helper):

```
lighthouse https://[domain] --only-categories=performance,seo,best-practices \
  --output=json --quiet
```

Extrahiere:
- Performance Score
- LCP, CLS, INP, TTFB
- SEO-Score, Title/Meta-Present, Robots.txt, Sitemap, Schema.org

→ `lighthouse.json`

### 5.3 SEO-Deep-Check (Python-Helper)

Nutze den Python-Helper `scripts/analyze_page.py` (übernommen aus
`zubair-trabzada/ai-marketing-claude` unter MIT-Lizenz, angepasst für LUMEN³):

```
python3 lumen3/scripts/analyze_page.py https://[domain] --output clients/[name]/competitive/[domain]/seo.json
```

Der Helper extrahiert zusätzlich:
- H-Struktur-Hierarchie (H1–H6)
- Alt-Tag-Vollständigkeit auf Images
- JSON-LD Schema.org Anzahl und Typen
- Interne vs. externe Links
- Form-Felder (Newsletter-Opt-in-Länge)

### 5.4 Social-Media-Check (manuell/Fallback, da keine API-Keys in LUMEN³)

Für jeden im Footer/Header verlinkten Social-Account:
- URL speichern
- Optional: letzter sichtbarer Post via Playwright (Facebook, LinkedIn öffentlich)
- Follower-Count (wenn öffentlich sichtbar)
- Posting-Frequenz (letzte 5 Posts)

Fallback: Sonnet bewertet qualitativ aus dem Screenshot der Social-Seite.
→ `social-metrics.json`

### 5.5 External-API-Datenpunkte (optional)

Einige Datenpunkte brauchen externe APIs (Ahrefs für Backlinks, Meta Ad Library,
Google Trends). Diese sind **optional** — wenn keine Keys vorhanden, werden die
entsprechenden DPs mit 0 oder geschätzt bewertet.

- O.SE.04 Backlink-Profil (DR-Wert): Ahrefs API, falls Key in `.env`
- P.CH.01–03 Paid-Channels: Meta Ad Library (public), Google Ads Transparency
- E.GN.01–03 Google News: Google News Search (scraped)

Fehlende Keys → Datenpunkt-Wert = 0, Kommentar in Output: "(nicht gemessen)".

### 5.6 Status-Meldung pro Wettbewerber

```
✓ [domain] — Hero, Logo, 9 Style-Profile, Lighthouse, SEO, Social-Links extrahiert
```

Bei Fehler: Konkrete Domain nennen, einmal retry, dann als "unvollständig"
markieren und weitermachen. Kein Abbruch.

---

## SCHRITT 6 — Phase 1: Datenpunkt-Scoring (123 DPs, Sonnet)

Lade die Datenpunkt-Definitionen aus `skills/00-datapoints.md`.

Für jeden Wettbewerber, iteriere durch alle 123 Datenpunkte und vergib 0/1/2.

### Scoring-Ablauf

1. **Automatisch aus Playwright/Lighthouse** (Sonnet liest JSON):
   - Alle technischen DPs (Website Performance, SEO, Security, Mobile UX)
   - Logo-Datenpunkte (SVG vs. PNG, Varianten aus /media-kit)
   - Font-Datenpunkte (aus computed-styles)
   - Meta-Datenpunkte (Title, Description, OG)

2. **Qualitativ durch Sonnet-Analyse** (braucht Hero-Text, Screenshots, About-Page):
   - Alle Assets-DPs (Brand Evolution, Why/How/What, Neuromarketing, Brand Story)
   - Brand Toolbox Soft-DPs (Voice & Tone, Style-Konsistenz)
   - Social Media Brand-Konformität
   - Content Strategy Tiefe

3. **Score transparent schreiben** in `clients/[name]/competitive/[domain]/scores.json`:
   ```json
   {
     "domain": "example.com",
     "dimensions": {
       "assets": {
         "raw": 67,
         "normalized_100": 62,
         "sub": {
           "brand_evolution": {"raw": 8, "max": 12, "normalized": 67},
           "why_how_what": {"raw": 14, "max": 22, "normalized": 64},
           ...
         },
         "datapoints": {
           "A.BE.01": {"value": 2, "evidence": "Positionierungs-Statement prominent in Hero"},
           "A.BE.02": {"value": 1, "evidence": "Vision erwähnt, aber unspezifisch"},
           ...
         }
       },
       "paid": { ... },
       "earned": { ... },
       "shared": { ... },
       "owned": { ... }
     },
     "full_potential_score": 58
   }
   ```

4. **Evidence-Pflicht:** Jeder Datenpunkt bekommt einen `evidence`-String (1 Satz),
   der begründet, warum 0/1/2. Das ist die Grundlage für Prüfbarkeit und Re-Run-
   Stabilität.

### Status-Anzeige während Scoring

Pro Wettbewerber:
```
Scoring example.com ...
  Assets: 67/108 (62%)
  Paid: 6/16 (38%)
  Earned: 14/34 (41%)
  Shared: 12/28 (43%)
  Owned: 38/60 (63%)
  FULL POTENTIAL: 58/100
```

### Gleichstand-Regel

Bei identischen Full-Scores wird nach Assets-Score sortiert (Assets ist die
tragende Dimension). Bei weiterem Gleichstand: alphabetisch.

---

## SCHRITT 7 — Phase 2: Visuelle Analyse (4 Module, parallel)

Phase 2 arbeitet **wettbewerbs-relativ** — sie analysiert das Marktbild,
nicht einzelne Player. Alle 4 Module laufen parallel über Haiku-Sub-Agents.

### 7.1 Farbanalyse (Farbrad)

**Input:** `computed-styles.json` aller Wettbewerber → Primary Background, Primary Color,
Accent/Button-Color, Link-Color.

**Verarbeitung:**
1. rgb() → Hex → HSL konvertieren
2. Hue (0–360°) auf einem Farbkreis plotten
3. Saturation → Punktgröße (10–40 px)
4. Lightness → Füllfarbe des Punkts
5. 12-Segment-Dichte-Analyse (30° pro Segment): zählen, wo wie viele Farben liegen
6. Crowded zones: Segmente mit ≥40% aller Farben
7. Potential zones: Segmente mit 0 Farben (mindestens 2 benachbarte)

**Output:**
- `clients/[name]/competitive/_synthesis/farbrad.svg`
- Text-Beschreibung in Markdown: "Im Markt dominieren Blau (180–240°) und
  Dunkelgrün (120–150°). Unbesetzt: Warmes Terrakotta (10–40°), Gelb (50–70°),
  kühles Violett (270–300°)."

### 7.2 Schriftart-Analyse (Font-Tabelle)

**Input:** `computed-styles.json` → fontFamily, fontWeight pro Element.

**Verarbeitung:**
1. Dedupliziere Display-Font (meistens H1-Font) und Body-Font (body/p)
2. Google Fonts API Lookup (öffentlich, kein Key nötig) für Font-Metadaten:
   - Kategorie (serif / sans-serif / display / handwriting / monospace)
   - Verfügbare Gewichte
3. Wenn Font nicht in Google Fonts: manuelle Klassifikation durch Sonnet
   (Screenshot-basiert, ggf. Fontshare-Lookup)
4. 2D-Raster:
   - X-Achse: Condensed (−1) ↔ Extended (+1), Mittelwert 0 = normal
   - Y-Achse: Light (100) ↔ Bold (900)
5. Farbkodierung: serif (blau) / sans-serif (orange) / script+display (grün)

**Output:**
- `clients/[name]/competitive/_synthesis/fonts.svg` mit allen Display + Body Fonts
- "Font-Tabu-Liste": Elemente, die im Markt überstrapaziert sind (basierend auf
  Häufigkeits-Schwellwert ≥50% der Wettbewerber)
- Empfehlungs-Korridor: "3 von 5 Wettbewerbern nutzen Sans-serif Bold-Normal.
  Serif-Light-Extended wäre maximal differenzierend."

### 7.3 Namensanalyse (4 Namens-Archetypen)

**Input:** Wettbewerber-Namen (aus URL → Company-Name via Logo-Alt oder Footer).

**Verarbeitung:**
Sonnet klassifiziert jeden Namen nach Regel:

| Archetyp | Erkennungsregel |
|---|---|
| **Familienname** | Enthält offensichtlichen Nachnamen (Duden/Wikipedia-Lookup optional) |
| **Stimmungsvoll** | Im Wörterbuch, mit emotionaler Konnotation (Poetik, Natur, Mythos) |
| **Erfunden** | Nicht im Wörterbuch, keine erkennbare Ableitung |
| **Erlebnisorientiert** | Beschreibt eine Wirkung oder Erfahrung (z.B. "Clear", "Flow", "Spark") |

**Output:**
- `clients/[name]/competitive/_synthesis/names.svg`: Balkendiagramm der 4 Archetypen
- Strategische Aussage: "5 von 6 Wettbewerbern nutzen Familienname. Ein erfundener
  oder erlebnisorientierter Name wäre im Markt unverwechselbar."

### 7.4 Tagline-Analyse (2D-Quadrant)

**Input:** Taglines aus Footer, Header, Meta-Title, Claim. Falls keine Tagline
vorhanden: H1 der Homepage als Ersatz.

**Verarbeitung:**
Sonnet bewertet jede Tagline auf zwei Achsen (je 0–10):

| Achse | 0 | 10 |
|---|---|---|
| X | Selbsterklärend (man versteht sofort, was die Marke tut) | Geheimnisvoll (Bedeutung erschließt sich erst nach Nachdenken) |
| Y | Business (pragmatisch, direkt, transaktional) | Wissenschaft (reflexiv, abstrakt, akademisch) |

**Kalibrierungs-Beispiele aus dem Enigma-Workshop:**
- "Leidenschaft für Zusammenarbeit" → X=3 (selbsterklärend), Y=3 (Business)
- "Wir stärken die Selbsterneuerungskraft Ihrer Organisation" → X=5, Y=8 (Wissenschaft)
- "Independent and neutral IT consulting from Switzerland" → X=1 (sehr selbsterklärend), Y=2 (Business)
- "Everyone has a meaningful life with ease" → X=8 (geheimnisvoll), Y=5

**Output:**
- `clients/[name]/competitive/_synthesis/taglines.svg`: Scatter-Plot
- Cluster-Markierung der dichtesten Zone
- Empfehlungs-Korridor: "Der Business-Selbsterklärend-Quadrant ist übersättigt
  (4 von 5 Wettbewerbern). Wissenschaft-Geheimnisvoll wäre maximal differenzierend."

---

## SCHRITT 8 — Phase 3: Synthese & Positionierungs-Lücken

Sonnet erstellt die Synthese aus Phase 1 + Phase 2:

### 8.1 Score-Ranking

Tabelle aller Wettbewerber sortiert nach Full Potential Score, mit Dimension-Breakdown.

### 8.2 Dimension-Profile

Pro Wettbewerber:
- Top 3 Stärken (DPs mit Score 2)
- Top 3 Schwächen (DPs mit Score 0)
- Auffällige Diskrepanzen (z.B. hohes Owned, schwaches Assets → "technische Marke ohne Strategie")

### 8.3 Visuelle Lücken (aus Phase 2)

Kompakte Zusammenfassung:
- Farbrad: überfüllte vs. unbesetzte Zonen
- Font-Tabelle: überstrapazierte vs. freie Typo-Räume
- Namen: dominante vs. seltene Archetypen
- Taglines: dichter Quadrant vs. leere Quadranten

### 8.4 Strategische Lücken-Hypothesen

Sonnet formuliert 3–5 konkrete Hypothesen:
- "Der Markt kommuniziert durchschnittlich 58/100 — die erste Marke mit ≥75
  hätte Strukturvorteil"
- "Alle Wettbewerber aktivieren Trust-Trigger. Innovation oder Passion als
  Primary wäre unbesetzt."
- "Niemand nutzt Longform-Content (alle O.CS.05 ≤ 1). Eine starke
  Content-Strategie ist freie Positionierung."

### 8.5 Abgleich mit differentiation_hypothesis des Nutzers

Prüfe: Liegt die Nutzer-Hypothese aus SCHRITT 4 in einer dieser Lücken?
- **Ja:** "Deine Hypothese [X] trifft die strategische Lücke [Y]. Weiterverfolgen."
- **Teilweise:** "Deine Hypothese überlappt teilweise mit [X]. Schärfung empfohlen."
- **Nein:** "Deine Hypothese liegt außerhalb der identifizierten Lücken. Das heißt
  nicht automatisch falsch — aber die Begründung sollte explizit sein. Soll ich
  die Analyse mit dieser Hypothese als Prämisse erneut laufen lassen?"

---

## SCHRITT 9 — Phase 4: Markdown-Output nach Schema 00

Lies das erweiterte Schema 00 aus `lumen3/artefact-templates.md`. Schreibe
`clients/[client_name]/outputs/00-competitive-analysis.md` exakt nach diesem Schema:

```markdown
# LUMEN¹ — Creative Footprint Full Potential Analyse
## [Projektname] | [Datum]
## Methodik: Enigma Creative Footprint (2022) + Owlist Asset-Erweiterung
## Framework: LUMEN³ by Owlist | www.owlist.ch

---

## Markt-Übersicht

[3–5 Sätze: Welcher Markt, Anzahl analysierter Wettbewerber, erkennbare
Cluster, Nutzer-Hypothese aus SCHRITT 4]

## Full Potential Ranking (Phase 1)

| Rang | Wettbewerber | Full Score | Assets | Paid | Earned | Shared | Owned |
|---|---|---|---|---|---|---|---|
| 1 | [domain] | 68 | 72 | 50 | 59 | 65 | 74 |
| 2 | ... | ... | ... | ... | ... | ... | ... |

## Dimension-Profile pro Wettbewerber

### [Wettbewerber 1 — Domain]
- **Positionierung in einem Satz:** [aus Hero-Text abgeleitet]
- **Full Potential Score:** 68/100
- **Assets 72:** Starke Brand Toolbox, mittlere Brand Story, schwaches Why/How/What
- **Paid 50:** Tracking sauber, aber kein Funnel-Spread
- **Earned 59:** Gute Social-Proof-Seite, wenig Presse
- **Shared 65:** LinkedIn stark, Instagram aktiv, TikTok nicht vorhanden
- **Owned 74:** Performance excellent, SEO solide, Mobile UX stark
- **Top 3 Stärken:** [DPs mit Score 2, konkret benannt]
- **Top 3 Schwächen:** [DPs mit Score 0]
- **Auffälligkeit:** [falls relevant]

[Pro Wettbewerber wiederholen]

## Visuelle Analyse des Wettbewerbsumfelds (Phase 2)

### Farbrad
![Farbrad](../competitive/_synthesis/farbrad.svg)

**Crowded zones:** [Hue-Bereiche mit Dichte]
**Potential zones:** [unbesetzte Hue-Bereiche]
**Strategische Aussage:** [eine Zeile]

### Schriftart-Tabelle
![Fonts](../competitive/_synthesis/fonts.svg)

**Dominante Fonts:** [Liste]
**Font-Tabu-Liste:** [überstrapazierte Elemente]
**Empfehlungs-Korridor:** [eine Zeile]

### Namens-Archetypen
![Namen](../competitive/_synthesis/names.svg)

**Dominanter Archetyp:** [z.B. Familienname, 5 von 6]
**Unbesetzte Archetypen:** [z.B. Erfunden, Erlebnisorientiert]
**Strategische Aussage:** [eine Zeile]

### Tagline-Quadrant
![Taglines](../competitive/_synthesis/taglines.svg)

**Dichter Quadrant:** [z.B. Business / Selbsterklärend]
**Leere Quadranten:** [z.B. Wissenschaft / Geheimnisvoll]
**Strategische Aussage:** [eine Zeile]

## Positionierungs-Lücken

[3–5 konkrete Lücken-Hypothesen aus Phase 3]

## Strategische Insights

[3–5 Empfehlungen für die folgenden LUMEN³-Skills, besonders für
Skill 01 (Business Context), Skill 02 (Brand Archetype) und Skill 06
(Brand Universe)]

## Abgleich mit deiner Hypothese

**Deine Hypothese:** [aus SCHRITT 4]
**Bewertung:** [trifft die Lücke / überlappt / liegt außerhalb]
**Empfehlung:** [weiterverfolgen / schärfen / alternativen prüfen]

## Nächster Schritt

Weiter mit LUMEN¹ Business Context Interview: `/lumen-business-context`
```

---

## SCHRITT 10 — Miro-Board (optional, falls Miro MCP aktiv)

Erstelle ein neues Miro-Board nach Definition `competitive-grid` aus
`artefact-templates.md`:

- Board-Name: `[Projektname] — LUMEN¹ Creative Footprint`
- Frame 1 `competitive-grid`: Grid mit Score-Karten aller Wettbewerber
- Frame 2 `farbrad`: SVG-Import des Farbrads
- Frame 3 `fonts-matrix`: SVG-Import der Font-Tabelle
- Frame 4 `names-bars`: SVG-Import des Namens-Diagramms
- Frame 5 `taglines-quadrant`: SVG-Import des Tagline-Quadranten
- Frame 6 `gaps-synthesis`: Strategische Lücken als Sticky-Notes

Board-Header (immer identisch nach `artefact-templates.md`):
```
[Projektname] — LUMEN¹ Creative Footprint Full Potential
LUMEN³ by Owlist | [Datum]
Methodik: Enigma (2022) + Owlist Asset-Erweiterung
```

Rahmen-Farbe: `#596A71` (Owlist Primary)

Falls Miro MCP nicht aktiv: Schritt überspringen, keine Warnung.

---

## SCHRITT 11 — Slides (optional)

Erzeuge `clients/[client_name]/presentation/slides-competitive.md` mit:

| Slide | Layout-ID | Inhalt |
|---|---|---|
| 1 | `layout-cover` | Projektname, "Creative Footprint", Datum |
| 2 | `layout-single-statement` | Full Potential Score-Ranking als Headline |
| 3 | `layout-grid-3x2` | Wettbewerber-Karten (Logo, Score, Top-Stärke) |
| 4 | `layout-overview-2col` | Farbrad + Empfehlungs-Korridor |
| 5 | `layout-overview-2col` | Font-Tabelle + Empfehlungs-Korridor |
| 6 | `layout-overview-2col` | Namen + Taglines |
| 7 | `layout-single-statement` | Wichtigste Positionierungs-Lücke |
| 8 | `layout-overview-2col` | Nutzer-Hypothese vs. Marktbild |

Layout-IDs müssen exakt mit `artefact-templates.md` Teil 2 übereinstimmen.

---

## SCHRITT 99 — Memory-Write

Schreibe einen Memory-Block nach `artefact-templates.md` Teil 7 in
`clients/[name]/memory.md` (append-only).

**Pflicht-Felder:**
- `version`: aus SCHRITT 0
- `status`: `abgeschlossen` oder `abgebrochen` oder `wiederholt`
- `strategisches_feld`: 1–3 Sätze, was die wichtigste strategische Erkenntnis dieses Laufs war — freigabefähig für Skill 06
- `internes_feld`: nur für `/lumen-strategist` und `/lumen-learn` — z.B. "Playwright-Timeout bei zwei Domains, manuell nachgepflegt; Hypothese des Nutzers lag in einer Lücke, saubere Weiterverfolgung empfohlen"

---

## Abschluss-Meldung

```
LUMEN¹ Creative Footprint Full Potential Analyse abgeschlossen.

Analysiert: [N] Wettbewerber · 123 Datenpunkte je Wettbewerber
Full Potential Score Range: [min]–[max]/100

Output:
  clients/[name]/outputs/00-competitive-analysis.md
  clients/[name]/competitive/ ([N] Wettbewerber-Verzeichnisse)
  clients/[name]/competitive/_synthesis/ (Farbrad, Fonts, Namen, Taglines)
  [Falls Miro aktiv:] Miro-Board: [URL]
  [Falls Slides erstellt:] clients/[name]/presentation/slides-competitive.md

Top 3 strategische Lücken:
  1. [Lücke 1]
  2. [Lücke 2]
  3. [Lücke 3]

Deine Hypothese: [Bewertung]

Weiter mit: /lumen-business-context — 40 Fragen Business Context Interview
```

---

## Was dieser Skill explizit NICHT tut

- Keine SEO-Optimierungs-Empfehlungen für die Wettbewerber selbst
- Keine Bewertung "besser/schlechter" moralisch — nur Diagnose der Positionierung
- Kein Re-Scraping bei Re-Run — bestehende Assets in `competitive/` werden
  wiederverwendet, ausser der Nutzer fordert explizit Refresh
- Keine Skill-eigene Definition von Schemas, Layouts oder Farben — alles aus
  `artefact-templates.md`
- Keine didaktische Erklärung der Enigma-Methodik — Verweis auf `methodology.md` §6
- Kein Full Ad Operations Audit — für detaillierte Paid-Analyse siehe externes Tool
- Kein Full SEO Content Audit — für tiefere SEO-Analyse siehe separate Skills

---

## Sub-Agent-Strategie (gemäss CLAUDE.md)

| Aufgabe | Modell | Begründung |
|---|---|---|
| Playwright-Scraping pro URL | Haiku | Rein mechanisch, parallel möglich |
| Lighthouse-Run pro URL | Haiku | Mechanische Extraktion |
| Python-Helper `analyze_page.py` | Haiku | Strukturierte Datenextraktion |
| Computed-Style-Konsolidierung (rgb→hex→HSL) | Haiku | Deterministische Transformation |
| Datenpunkt-Scoring qualitativ (Phase 1 Assets-DPs) | Sonnet | Inhaltliche Einschätzung, Evidence-Schreibung |
| Phase 2 Farbrad-Rendering | Haiku | SVG-Generation aus HSL-Koordinaten |
| Phase 2 Font-Klassifikation | Sonnet | Qualitative Einordnung, wo Google-Fonts-Lookup scheitert |
| Phase 2 Namens-Klassifikation | Sonnet | Semantische Zuordnung zu 4 Archetypen |
| Phase 2 Tagline-Bewertung | Sonnet | Qualitative 2D-Einordnung |
| Phase 3 Positionierungs-Synthese | Sonnet | Cluster-Analyse über alle Wettbewerber |
| Markdown-Output gemäss Schema | Sonnet | Schema-Validierung erforderlich |
| Memory-Block schreiben | Sonnet | Strategische vs. interne Trennung |

**Niemals Opus für diesen Skill** — auch nicht für die Synthese. Opus wäre
Overkill für deterministische Datenpunkt-Bewertung.

---

## Externe Abhängigkeiten

| Komponente | Verwendet für | Fallback |
|---|---|---|
| **Playwright MCP** | Scraping, Screenshots, Computed Styles | Manueller Fallback-Modus |
| **Lighthouse CLI** | Performance, SEO, Best Practices | Datenpunkte mit 0 bewerten |
| **Python `analyze_page.py`** | SEO-Deep-Check, Schema.org, Links | Fallback auf Playwright-only |
| **Google Fonts API** | Font-Metadaten (public, kein Key) | Manuelle Klassifikation durch Sonnet |
| **Miro MCP** | Miro-Board | Schritt überspringen |
| **Ahrefs API** (optional) | Backlink-Profil O.SE.04 | DP = 0 |
| **Meta Ad Library** (public) | Paid-Channels P.CH.01–03 | DP = 0 |

**Lizenz-Hinweis:** Der Python-Helper `analyze_page.py` basiert auf Code aus
`zubair-trabzada/ai-marketing-claude` unter MIT-Lizenz (Copyright 2026 Zubair
Trabzada). Angepasst und erweitert für LUMEN³. Der MIT-Copyright-Vermerk bleibt
im Helper-Script erhalten.

---

## Nächste Schritte nach Skill-Abschluss

- `/lumen-business-context` — Skill 01 mit Kontext aus Creative Footprint
- `/lumen-strategist` — zurück zum Orchestrator für Übersicht
