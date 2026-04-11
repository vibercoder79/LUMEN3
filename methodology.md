# LUMEN³ — Methodology
## Wissenschaftliche und praktische Quellen
## Framework: LUMEN³ by Owlist | www.owlist.ch
## Version 1.1 | April 2026

---

## Zweck

Diese Datei dokumentiert die Quellen, auf denen LUMEN³ aufsetzt. Sie ist die
**vierte Single Source of Truth** des Frameworks — neben `CLAUDE.md`,
`artefact-templates.md` und `trigger-mapping.md`.

Skills referenzieren ihre methodische Basis ausschliesslich als Verweis auf
diese Datei (z.B. "Methodische Basis: Aaker (1997), siehe `methodology.md` §1").
Sie wiederholen die wissenschaftlichen Erklärungen nicht in der Skill-Datei selbst.

**Output-Header bleiben unberührt:** Wenn ein Skill seinen Output schreibt,
nennt er die Methodik-Quelle weiterhin im H2-Header der Markdown-Datei. Das
ist für den Kunden, nicht für Claude. Diese Datei ersetzt nur die didaktische
Wiederholung *innerhalb* der Skill-Dateien.

---

## §1 — Brand Personality (verwendet in Skill 03)

### Jennifer Aaker (1997)
**"Dimensions of Brand Personality"**, Journal of Marketing Research, 34(3),
347–356.

Aakers Studie ist das meistzitierte Brand-Persönlichkeits-Framework der
Marketingwissenschaft. Sie identifizierte fünf Dimensionen, die über Branchen
hinweg stabil sind:

1. **Sincerity** — Genuine, Warm, Wholesome, Cheerful
2. **Excitement** — Bold, Daring, Spirited, Imaginative, Unique, Trendy
3. **Competence** — Reliable, Intelligent, Successful, Hardworking, Secure
4. **Sophistication** — Charming, Elegant, Glamorous, Refined, Prestigious
5. **Ruggedness** — Tough, Rugged, Outdoorsy, Masculine, Western

Methodisch validiert mit 631 Befragten und 114 Persönlichkeits-Adjektiven,
reduziert auf 42 Kern-Items. Aaker zeigte, dass diese fünf Dimensionen
empirisch trennscharf sind und Konsumenten-Präferenzen vorhersagen.

**Verwendung in LUMEN³:** Skill 03 nutzt die 42 Adjektive als Kartenset.
Jedes Adjektiv ist in `trigger-mapping.md` einer Aaker-Dimension und einem
LUMEN³-Trigger zugeordnet.

### Rob Meyerson / Heirloom (2012)
**"Brand Personality Cards"** — Agentur-Werkzeug, kein Peer-Review.

Meyersons Beitrag ist methodisch, nicht akademisch. Er übersetzte Aakers
Adjektive in ein Workshop-Format mit Gegensatzpaaren (z.B. *Warm vs. Serious*,
*Bold vs. Wholesome*). Der Mechanismus erzwingt eine echte Entscheidung
statt vager Selbstbeschreibung — wer "Warm" wählt, kann nicht gleichzeitig
"Serious" als Kern-Eigenschaft beanspruchen.

Genutzt von Frontify, Canny Creative, Bolder Agency, MadeBrave und vielen
weiteren Brand-Agenturen.

**Verwendung in LUMEN³:** Skill 03 nutzt das Gegensatzpaar-Prinzip plus die
4-Kategorien-Sortierung (Core / Aspiration / Unsicher / Nicht).

---

## §2 — Brand Archetype (verwendet in Skill 02)

### Carol Pearson & Margaret Mark (2001)
**"The Hero and the Outlaw: Building Extraordinary Brands Through the Power
of Archetypes"**, McGraw-Hill.

Pearson und Mark übertrugen C.G. Jungs Archetypen-Theorie auf
Marken-Positionierung. Sie identifizierten zwölf Archetypen, gruppiert nach
vier Motivations-Kategorien:

- **Stabilität** — Caregiver, Ruler, Creator
- **Zugehörigkeit** — Jester, Everyman, Lover
- **Risiko/Meisterschaft** — Hero, Outlaw, Magician
- **Unabhängigkeit/Erfüllung** — Innocent, Sage, Explorer

Jeder Archetyp hat ein konsistentes Wertesystem, eine charakteristische
Sprache und eine vorhersagbare emotionale Wirkung. Brands, die einen
Archetyp konsequent verkörpern, schaffen stärkere Wiedererkennung.

**Verwendung in LUMEN³:** Skill 02 nutzt die zwölf Archetypen als zweite
Bewertungs-Methode (neben Fascinate). Die Archetyp→Trigger-Zuordnung steht
in `trigger-mapping.md`.

### Sally Hogshead (2014)
**"How the World Sees You"**, HarperBusiness.

Hogsheads "Fascinate System" identifiziert sieben **Advantages** — die Art,
wie eine Person oder Marke andere fasziniert:

- Innovation, Passion, Power, Prestige, Trust, Mystique, Alert

Im Unterschied zu Pearson/Jung ist Fascinate ergebnis-orientiert: Es fragt
nicht "Wer bist du?" sondern "Wie wirkst du auf andere?". Hogshead validierte
das System mit über 100'000 Tests und entwickelte daraus den Fascinate Advantage
Test (Self-Assessment via Fragebogen).

**Verwendung in LUMEN³:** Skill 02 nutzt Fascinate als erste Bewertungs-Methode.
Die sieben Advantages sind direkt deckungsgleich mit den sieben LUMEN³-Triggern
(siehe §3).

---

## §3 — Neuromarketing Trigger (verwendet in Skill 04)

### Antonio Damasio (1994)
**"Descartes' Error: Emotion, Reason, and the Human Brain"**, Putnam.

Damasio zeigte mit Patienten, die Hirnschäden im präfrontalen Cortex hatten:
Wenn die emotionale Bewertung wegfällt, können Menschen *keine Entscheidungen*
mehr treffen — auch wenn ihre Ratio intakt ist. Sie können Optionen analysieren,
aber nicht zwischen ihnen wählen.

Seine Schlussfolgerung: Entscheidungen sind fundamental emotional. Rationale
Argumente bestätigen oder rationalisieren eine emotionale Vorentscheidung,
sie ersetzen sie nicht.

**Verwendung in LUMEN³:** Damasio ist die wissenschaftliche Begründung dafür,
dass Brand-Strategie *bei den Triggern* ansetzen muss, nicht bei den Argumenten.

### Gerald Zaltman (2003)
**"How Customers Think: Essential Insights into the Mind of the Market"**,
Harvard Business School Press.

Zaltman, Harvard-Marketing-Professor, schätzt auf Basis seiner ZMET-Studien
(Zaltman Metaphor Elicitation Technique): **95% aller Kaufentscheidungen
laufen unbewusst ab.** Konsumenten können ihre eigenen Motive nur teilweise
verbalisieren — das meiste wird über Metaphern, Bilder und Emotionen verarbeitet.

Diese Zahl ist eine Schätzung, kein peer-reviewed Messwert. Sie wird in der
Marketingliteratur breit zitiert und in Frage gestellt — der grundlegende
Punkt (überwiegender Anteil unbewusster Verarbeitung) ist robust, die exakte
Prozentzahl nicht.

**Verwendung in LUMEN³:** Zaltman ist die zweite Säule der Trigger-Begründung —
neben Damasio. Wir machen die Quelle transparent und nennen die 95% als
Schätzung, nicht als gemessene Tatsache.

### LUMEN³-eigenes Trigger-Modell

LUMEN³ nutzt sieben Trigger, die deckungsgleich mit Hogsheads Fascinate
Advantages sind:

- **PASSION** — Schafft die Marke emotionale Verbindung?
- **INNOVATION** — Überrascht sie durch neue Ideen?
- **PRESTIGE** — Signalisiert sie Exzellenz und Status?
- **POWER** — Führt sie klar und entschlossen?
- **TRUST** — Ist sie verlässlich und beständig?
- **MYSTIQUE** — Fasziniert sie durch Zurückhaltung?
- **ALERT** — Schützt sie durch Voraussicht?

**Wissenschaftlicher Status:** Das Sieben-Trigger-Modell selbst ist kein
peer-reviewed Framework. Es übernimmt Hogsheads validierte sieben Advantages
und operationalisiert sie deterministisch über das Scoring in
`trigger-mapping.md`. Der Mehrwert von LUMEN³ liegt in der Operationalisierung
(reproduzierbare Berechnung), nicht in einer neuen wissenschaftlichen Hypothese.

**Verwendung:** Skill 04 berechnet die Trigger-Hierarchie deterministisch aus
den Outputs von Skill 02 und Skill 03 nach den Regeln in `trigger-mapping.md`.

---

## §4 — Card Sorting (verwendet in Skill 03)

### Jakob Nielsen / Nielsen Norman Group
Card-Sorting ist eine etablierte UX-Methode zur Strukturierung mentaler Modelle.
Nielsen Norman Group dokumentiert das Verfahren als Standard für
Informationsarchitektur und Konzeptklärung seit den 1990er Jahren.

**4-Kategorien-Variante:** In der Brand-Discovery-Praxis hat sich die
Sortierung in *Core / Secondary / Aspirational / Not Our Brand* etabliert.
Diese Variante wird von Frontify, Canny Creative, Bolder Agency, MadeBrave
und weiteren Brand-Agenturen eingesetzt.

**Verwendung in LUMEN³:** Skill 03 nutzt eine angepasste 4-Kategorien-Variante:
*Core / Aspiration / Unsicher / Nicht*. "Unsicher" ersetzt "Secondary", weil
es ehrlicher ist — es markiert Spannungen, die in Skill 06 noch geklärt
werden müssen.

---

## §5 — Visuelle Sprache und Farbpsychologie (verwendet in Skill 05)

### Karen Haller (2019)
**"The Little Book of Colour: How to Use the Psychology of Colour to
Transform Your Life"**, Penguin.

Haller systematisiert Farbpsychologie für angewandte Kontexte. Wichtig für
LUMEN³: Sie unterscheidet zwischen *kulturell gelernten* Farb-Assoziationen
(z.B. Rot = Liebe in Europa, Glück in China) und *physiologisch wirksamen*
Farb-Reaktionen (z.B. längere Wellenlängen erhöhen Puls).

**Verwendung in LUMEN³:** Skill 05 nutzt Haller als Strukturierungs-Hilfe,
ergänzt durch Live-Recherche via OpenRouter/Perplexity für aktuelle
Farb-Studien. Das Ergebnis ist eine Farbempfehlung, die auf Trigger-Profil
plus Kulturkontext basiert — nicht auf Bauchgefühl.

### Neuro-Color Research (LUMEN³-spezifisch)
Skill 05 fragt zur Laufzeit Perplexity Sonar nach aktuellen Studien zu
Farbe + Trigger-Kombinationen (z.B. "Neuromarketing studies on color
associations with trust and innovation 2020-2026"). Die Ergebnisse fliessen
als zusätzliche Quelle in die Empfehlung ein.

**Status:** Dies ist ein praktisches Verfahren, kein peer-reviewed Framework.
Es gleicht statisches Wissen (Haller) mit dynamischer Recherche aus, um
Empfehlungen aktuell zu halten.

---

## §6 — Creative Footprint & PESO+Asset (verwendet in Skill 00)

### Gini Dietrich (2014)
**"Spin Sucks: Communication and Reputation Management in the Digital Age"**,
Que Publishing.

Dietrich, Gründerin der Marketing-Agentur Arment Dietrich, entwickelte das
**PESO-Modell** als strukturierten Rahmen zur Kategorisierung von
Kommunikationskanälen. Es steht für:

- **Paid** — bezahlte Kanäle (Ads, Sponsored Content)
- **Earned** — verdiente Medien (PR, Backlinks, Mentions)
- **Shared** — geteilte Medien (Social Networks, Community)
- **Owned** — eigene Kanäle (Website, Newsletter, Blog)

PESO ist heute einer der meistzitierten Frameworks im integrierten Marketing
und die Grundlage für strukturierte Kommunikations-Audits.

**Wissenschaftlicher Status:** Dietrichs Modell ist kein peer-reviewed
Framework, sondern ein praktisches Strukturierungswerkzeug. Es ist in der
Marketing-Community breit akzeptiert und dient als operative Referenz.

### Enigma Creative Footprint (2022)
**Full Potential Analyse** — Owlist-Erweiterung des PESO-Modells.
Entwickelt von Enigma Swiss (Bern) im Rahmen des Creative Footprint Workshops
für Thought Leader & Partner (später Owlist) am 03.05.2022. Projektleitung:
Kendy Chen. Executives: Martin Künzi, Olivier Kennedy.

Enigma ergänzte Dietrichs PESO um eine **fünfte Dimension Assets** — die
nicht-medialen, inhärenten Markenwerte. Die Begründung: Eine Marke ist zuerst
in sich selbst stark (Assets), dann in ihrer Kommunikation (PESO). Wer nur
Kommunikationskanäle auditiert, misst die Sichtbarkeit, nicht die Substanz.

**Die 5 Dimensionen und ihre Sub-Kategorien:**

1. **Assets** — Brand Evolution, Why/How/What, Neuromarketing, Brand Toolbox, Brand Story
2. **Paid Media** — Channels, Tracking Setup, Funnel Coverage
3. **Earned Media** — Google News, Influencer, Media Corner, Social Proof
4. **Shared Media** — Facebook, Instagram, LinkedIn, Twitter/X, TikTok
5. **Owned Media** — Newsletter, Content Strategy, Website Performance, SEO, Mobile UX, Security

**Scoring:** 3-Punkt-Skala (0 = nicht vorhanden, 1 = schwach/ausbaufähig,
2 = gut umgesetzt). Pro Dimension werden die Roh-Scores auf 100 normiert
und gewichtet zum **Full Potential Score 0–100** zusammengeführt.

**Wissenschaftlicher Status:** Die Enigma-Erweiterung ist ein praxiserprobtes
Beratungsinstrument mit hoher Face-Validität. Sie ist keine peer-reviewed
Methode, sondern eine strukturierte Operationalisierung eines breit
akzeptierten Modells (PESO).

**Verwendung in LUMEN³:** Skill 00 führt die Full Potential Analyse mit
123 kuratierten Datenpunkten durch (Enigma-Original: 139 Datenpunkte; LUMEN³
hat redundante Punkte zusammengefasst). Zusätzlich werden die vier visuellen
Analyse-Module aus dem Enigma-Workshop umgesetzt:

- **Farbrad** — Cluster-Analyse aller Wettbewerber-Farben auf HSL-Kreis
- **Schriftart-Tabelle** — 2D-Positionierung (Condensed↔Extended × Light↔Bold)
- **Namens-Archetypen** — 4 Typen: Familienname / Stimmungsvoll / Erfunden / Erlebnisorientiert
- **Tagline-Quadrant** — 2D-Positionierung (Selbsterklärend↔Geheimnisvoll × Business↔Wissenschaft)

Diese visuelle Analyse arbeitet wettbewerbs-relativ und identifiziert
überfüllte Zonen sowie Positionierungs-Lücken im Marktbild.

**Referenzwerte aus dem Original-Workshop** (Thought Leader & Partner,
Mai 2022): Campana Schott 50 · Atrete 42 · Sedlak & Partner 33 · Murakamy 49.
Diese werden in LUMEN³ **nicht** als Benchmark angezeigt — der Score ist
Diagnose, nicht Wettkampf.

---

## Was diese Datei NICHT ist

- Kein Lehrbuch zur Markenführung
- Kein erschöpfender Literatur-Review
- Keine wissenschaftliche Verteidigung der Methode

Sie ist die *Quellen-Sammlung* der praktischen Bausteine, die LUMEN³ nutzt.
Wer tiefer einsteigen will, geht an die Originalquellen.

---

## Wann Skills auf diese Datei verweisen

| Skill | Verweis auf §|
|---|---|
| 00 Competitive (Creative Footprint) | §6 (Dietrich PESO + Enigma Full Potential) |
| 02 Brand Archetype | §2 (Pearson/Jung, Hogshead) |
| 03 Brand Interview | §1 (Aaker, Meyerson) + §4 (Card Sort) |
| 04 Trigger Analysis | §3 (Damasio, Zaltman, Trigger-Modell) |
| 05 Story Identity | §5 (Haller, Neuro-Color) |
| 06 Brand Universe | alle (Synthese) |

Skill 01 (Business Context) ist ein reines Discovery-Interview ohne externe
wissenschaftliche Basis und verweist nicht auf `methodology.md`.

---

## Versionierung

Diese Datei folgt derselben Versionierungs-Disziplin wie `artefact-templates.md`:

- **Patch:** Neue Quellen ergänzen, bestehende präzisieren
- **Minor:** Quellen entfernen oder neu kategorisieren
- **Major:** Methodische Kern-Annahmen ändern (z.B. anderes Trigger-Modell)

Aktuelle Version: **1.1** — §6 ergänzt (Dietrich PESO 2014 + Enigma Creative Footprint 2022) für Skill 00 v2.0 Alignment.

## Changelog

- **1.1 (April 2026):** §6 ergänzt (Dietrich PESO 2014, Enigma Creative Footprint 2022). Skill 00 ist nicht mehr methodology-frei, sondern referenziert §6 als Basis für die Full Potential Analyse mit 123 Datenpunkten in 5 Dimensionen. Verweise-Tabelle aktualisiert.
- **1.0 (April 2026):** Initiale Definition. §1–§5 (Aaker/Meyerson, Pearson/Hogshead, Damasio/Zaltman, Card Sort, Haller/Neuro-Color).
