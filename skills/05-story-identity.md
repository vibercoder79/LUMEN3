---
name: lumen-story
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-story" eingibt,
  "Story Identity Tonality", "Golden Circle" oder "WHY HOW WHAT" sagt.

  Dieser Skill hat zwei Teile:

  TEIL A — Golden Circle (WHY / HOW / WHAT)
  Geführtes Purpose-Discovery-Interview. Destilliert das finale WHY
  Statement, HOW und WHAT der Marke über Peaks-&-Valleys-Stories,
  Hedgehog Validation und Focus Lab Stress Test.

  TEIL B — Story, Identity, Tonalität, Neuro-Color
  Liest Outputs aus Skills 01–04 und destilliert: Brand Story (3 Versionen),
  Identity-Statement, Tonalitäts-Profil, Sprach-Regeln und eine Neuro-Color
  Farb-Empfehlung basierend auf §5 und dem Primary Trigger aus Skill 04.

  Methodische Basis: §5 (Haller, Neuro-Color) für Farb-Empfehlung;
  Sinek Golden Circle + Dante Labs Positioning Framework als operativer
  Kern von Teil A und B. Details: methodology.md
  Schemas, Frames, Layouts: artefact-templates.md

  Optionale externe Komponente: OpenRouter API (Perplexity Sonar) für
  Live-Recherche aktueller Neuro-Color-Studien. Läuft ohne Key weiter —
  Fallback auf statische Ableitung aus Trigger-Profil + §5.

  Voraussetzung für Teil B (alle empfohlen, keiner zwingend):
  01-business-context.md, 02-brand-archetype.md, 03-brand-interview.md,
  04-trigger-analysis.md
  Falls nicht vorhanden: Nur Teil A durchführen.

  Output:
  - 05-story-identity.md (Schema 05 aus artefact-templates.md)
  - slides-story.md (Slide-Set für Skill 05)
  - Miro Board: Golden Circle Frame + Story/Tonality Frame (falls aktiv)

  Version 1.4 — April 2026
---

# LUMEN² — Story, Identity, Tonality
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 05, Slide-Set, Owlist-Tokens)
- `lumen3/methodology.md` (§5 — Haller, Neuro-Color, bei Bedarf)
- `clients/[name]/outputs/04-trigger-analysis.md` (**Pflicht** für Neuro-Color)
- `clients/[name]/outputs/01-business-context.md` bis `03-brand-interview.md`
  (empfohlen für Teil B)
- `OPENROUTER_API_KEY` in `.env` (optional — nur für Live-Recherche)
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Methodische Basis: §5 (Haller, Neuro-Color) für die Farb-Empfehlung.
Der operative Kern von Teil A ist Sinek Golden Circle + Dante Labs
Positioning — diese Quellen stehen nicht in `methodology.md` (weil sie
als Workshop-Methoden gelten, nicht als peer-reviewed Framework) und
werden als Kern-Content direkt in diesem Skill gehalten.

---

## Verhaltensprinzipien

- Stelle IMMER nur eine Frage auf einmal.
- Warte auf vollständige Antwort bevor weitergemacht wird.
- Stelle "What"-Fragen (nicht "Why" — wirkt anklagend).
- Halte Stille aus — nicht füllen, warten.
- Interne Themen-Analyse nach jeder Story still durchführen.
- Keine Wertung während des Interviews.
- Am Ende: WHY Statement in 3 Iterationen gemeinsam verfeinern.

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/05-story-identity.md` nicht: weiter mit
EINSTIEG, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 05 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## EINSTIEG

```
🦉 LUMEN² Story & Identity Workshop von Owlist.

Drei Fragen zuerst:

1. Sprache?
   Deutsch (Standard) | English | Français | Andere

2. Miro Board?
   - Bestehend: URL eingeben (z.B. vom We Are/Not Board)
   - Neu erstellen
   - Kein Miro

3. LUMEN²-Outputs vorhanden?
   Ich prüfe automatisch ob 01–04 im outputs/-Ordner liegen.
   Falls ja: Ich lese sie als Kontext für Teil B.
   Falls nein: Nur Teil A (Golden Circle) wird durchgeführt.
```

Miro MCP Fallback: Bei Ausfall läuft der Skill ohne Warnung weiter
(Miro-Spiegel-Prinzip aus `CLAUDE.md`).

OpenRouter Fallback: Fehlt der Key, läuft Teil B weiter — die Farb-Empfehlung
basiert dann auf statischer Ableitung aus Primary Trigger + §5 (Haller).

---

## ═══════════════════════════════════════════
## TEIL A — GOLDEN CIRCLE (WHY / HOW / WHAT)
## ═══════════════════════════════════════════

### A1 — Vorbereitung

```
Der Golden Circle — von INNEN nach AUSSEN:
WHY  — Warum existiert die Marke? (spricht das Herz an)
HOW  — Wie tut sie es einzigartig? (zeigt den Weg)
WHAT — Was bietet sie an? (beweist den Glauben)

Das WHY wird nicht erfunden — es wird entdeckt.
Es steckt in deinen Geschichten.

Ich führe dich durch 8 Story-Fragen + WHY-Drafting + Validierung.
Antworte so konkret und persönlich wie möglich.
```

### A2 — Story Discovery (Peaks & Valleys)

Stelle diese Fragen nacheinander — immer nur eine:

**STORY 1 — Prägende Person:** "Denke an eine Person die dich zu dem
gemacht hat, wer du heute bist. Was genau hat diese Person getan —
nicht wer sie war, sondern was sie tat?"

**STORY 2 — Intrinsische Motivation:** "Erinnere dich an einen Moment
in deiner Arbeit wo du gedacht hättest: Das hätte ich auch kostenlos
gemacht. Was ist da passiert?"

**STORY 3 — Schlechtester Tag:** "Was war dein schlechtester Tag im
Business — und warum hat er dich so tief getroffen? Was steht dahinter?"

**STORY 4 — Früheste Freude:** "Was ist deine früheste konkrete positive
Erinnerung? So früh wie möglich — Kindheit, Schule, Familie?"

**STORY 5 — Wirkungsmoment:** "Wann hattest du das Gefühl, wirklich
einen Unterschied gemacht zu haben — für jemanden? Was ist passiert?"

**STORY 6 — Widerstandsmoment:** "Wann hast du dich gegen das 'So macht
man das' gewehrt? Was hat dich dazu gebracht?"

**STORY 7 — Energiequelle:** "Bei welcher Tätigkeit verlierst du das
Zeitgefühl? Was genau tust du dabei?"

**STORY 8 — Nachtgedanke:** "Welches Problem oder welche Ungerechtigkeit
beschäftigt dich immer wieder — hält dich nachts wach?"

Nach jeder Story: kurz bestätigen, intern Themen notieren. Nicht
kommentieren oder werten — nur zuhören.

### A3 — Themen-Identifikation (intern, dann zeigen)

Suche nach Themen die in 2+ Stories auftauchen. Finde den "goldenen Faden".

```
Ich habe folgende Themen in deinen Geschichten gefunden:
Thema 1: [Name] — taucht auf in Stories [X, Y, Z]
Thema 2: [Name] — taucht auf in Stories [X, Y]
[...]

Ein Thema scheint besonders zu leuchten: [THEMA]

Stimmt das für dich? Was würdest du anders gewichten?
```

### A4 — WHY Statement Entwicklung

Format: "To _____ so that _____"
- Erste Lücke: Dein Beitrag (die Handlung)
- Zweite Lücke: Deine Wirkung (der Unterschied)

**3 Iterationen gemeinsam:**

Version 1 (erster Entwurf basierend auf Themen).
Version 2 (verfeinert nach Feedback).
Version 3 (Finaler Kandidat).

Validation-Check (intern) für die finale Version:
- Unter 15 Wörter?
- Jargon-frei?
- Könnte ein Konkurrent das sagen? (sollte NEIN sein)
- Emotional?
- In Gründungsgeschichten verankert?

### A5 — HOW (Einzigartiger Ansatz)

"Das WHY erklärt warum ihr existiert. Das HOW erklärt wie ihr es
einzigartig tut. Was sind 3 Dinge die ihr grundlegend anders macht
als andere in eurem Bereich — nicht was ihr tut, sondern wie?"

Destilliere zu 3 HOW-Aussagen.

### A6 — WHAT (Beweis des Glaubens)

"Das WHAT ist der konkrete Beweis für euer WHY. Was bietet ihr an —
Produkte, Services, Leistungen — die euer WHY beweisen?"

### A7 — Hedgehog Validation (Collins)

Drei Fragen (Bewertung 1–10 pro Kreis):

1. "Wofür brennt ihr wirklich? Nicht was ihr brennen WOLLT — was
   tatsächlich eure Energie gibt?"
2. "Worin könnt ihr wirklich hervorragend sein? Nicht was ihr gut könnt —
   wo liegt genuines Exzellenz-Potential?"
3. "Was treibt euer wirtschaftliches Modell an? Die eine Grösse mit dem
   grössten Einfluss auf eure Wirtschaftlichkeit?"

Sweet Spot beschreiben. Prüfe: Stimmt der Sweet Spot mit dem WHY überein?

### A8 — Focus Lab Stress Test

4 Elemente:
- **Insight:** "Welches bedeutungsvolle Problem existiert ihr um zu verändern?"
- **Impact:** "Welches positive Ergebnis schafft ihr — für wen?"
- **Fit:** "Was macht euren Purpose glaubwürdig — was nur IHR liefern könnt?"
- **Proofs:** "Nennt 3–5 konkrete Handlungen die beweisen, dass es ernst gemeint ist."

Stress-Test-Fragen:
- Könnte ein Konkurrent das sagen? (sollte NEIN sein)
- Könnt ihr es nächstes Quartal beweisen?
- Leitet es Kundenservice-Entscheidungen an?
- Leitet es Produkt-Entscheidungen an?

### A9 — Anti-Pattern Check (intern)

Prüfe still, ob das WHY Statement folgende Fallen vermeidet:
- Beginnt mit WHAT (beschreibt Produkte statt Glauben)
- Verwechselt WHY mit Profit ("Mehrwert maximieren")
- Erfunden statt entdeckt (keine Story-Verbindung)
- Generisch (könnte jede Firma sagen)
- Purpose Washing (nicht lebbar)

Red-Flag-Wörter die NICHT erscheinen sollten: "Best", "Excellence",
"Quality", "Maximize", "Optimize", "Leverage", "Stakeholders",
"Solutions", "Industry-leading".

### A10 — Golden Circle Abschluss-Präsentation

```
Euer Golden Circle:

WHY:  "To [BEITRAG] so that [WIRKUNG]"
HOW:  1. [HOW 1]  2. [HOW 2]  3. [HOW 3]
WHAT: [Angebote als WHY-Beweis]

Mission (was ihr täglich tut):
"[Aktionsorientiert, Gegenwartsform, 1 Satz]"

Vision (die Zukunft die ihr baut):
"[Aspirational, Zukunftsform, 1 Satz]"

Hedgehog Sweet Spot: [Beschreibung]
Focus Lab Validation: [PASSED / NEEDS REFINEMENT]
```

---

## ═══════════════════════════════════════════
## TEIL B — STORY, IDENTITY, TONALITY, NEURO-COLOR
## ═══════════════════════════════════════════

Lese automatisch folgende Dateien (falls vorhanden):
- `01-business-context.md`
- `02-brand-archetype.md`
- `03-brand-interview.md`
- `04-trigger-analysis.md` (**Pflicht** für Farb-Empfehlung)

Kombiniere mit den Ergebnissen aus Teil A.

### B1 — Brand Story (3 Versionen)

**Version 1 — 1-Satz-Essenz:** Basiert auf WHY Statement + Primary
Trigger + Archetype. "[Firmenname] [Verb] [Für wen] [Warum es wichtig
ist]." Max. 20 Wörter. Keine Buzzwords.

**Version 2 — Elevator Pitch (30 Sekunden / 3–4 Sätze):**
- Satz 1: Wer wir sind (WHY-basiert)
- Satz 2: Wer unsere Kunden sind und welches Problem sie haben
- Satz 3: Wie wir es einzigartig lösen (HOW)
- Satz 4: Einladung / Call to Action

**Version 3 — About-Page (200–250 Wörter):**
Held der Geschichte ist der KUNDE (nicht die Marke). Struktur:
Problem/Spannung → Wendepunkt (Gründungsgeschichte) → Weg/Ansatz (HOW)
→ Transformation des Kunden → Einladung.

### B2 — Brand Identity Profil

Synthese aus Skill 02 (Archetype) + 03 (We Are/Not) + 04 (Trigger) + Teil A (WHY):

**3 Kern-Adjektive:** Das Destillat aller Inputs — die drei Wörter die
alles zusammenfassen.

**Charakter-Beschreibung:** "Wenn [Markenname] eine Person wäre, dann
wäre sie..." (5–6 Sätze: Persönlichkeit, Verhalten, Werte, Auftritt)

**Positioning Statement (Dante Labs Framework):**
```
For    [Zielkunde]
Who    [Bedürfnis/Wunsch]
[Markenname] is a [Kategorie]
That   [Hauptnutzen]
Unlike [Wettbewerber]
Because [Grund zum Glauben]
```

### B3 — Tonalität (Brand Voice)

**5 Schreibstil-Adjektive:** Präzise Beschreibung der Markenstimme.

**Schreibregeln:**
- Du/Sie? (Entscheid mit Begründung)
- Satzlänge: Kurz/Mittel/Lang — mit Beispiel
- Aktiv oder Passiv? (Standard: Aktiv)
- Zahlen und Fakten: Wie einsetzen
- Humor: Erlaubt/Verboten — in welchem Kontext

**5 Beispielsätze "SO klingt die Marke":** Echte Beispiel-Headlines oder Intro-Sätze.

**5 Gegenbeispiele "SO klingt sie NICHT":** Konkrete Negativbeispiele.

**Wort-Verbote:** Liste von Wörtern die nie verwendet werden (basierend auf
NICHT-Wörtern aus Skill 03 + Anti-Pattern-Check aus Teil A).

### B4 — Neuro-Color Farb-Empfehlung

**Methodische Basis: §5 (Haller, Neuro-Color), siehe `methodology.md`**

Dieser Schritt erzeugt eine Farb-Empfehlung, die auf Trigger-Profil
(Skill 04) und kultureller Farbpsychologie basiert — nicht auf Bauchgefühl.

**Schritt 1: Trigger-Basis einlesen**

Lies aus `04-trigger-analysis.md`:
- Primary Trigger + Score
- Secondary Trigger + Score
- Dormant Trigger

Wenn `04-trigger-analysis.md` fehlt: Ableitung aus Skill 02
(Primary Advantage → Trigger-Mapping via `trigger-mapping.md`).
Wenn auch das fehlt: Skill-Abbruch mit Hinweis, zuerst Skill 02 oder 04
laufen zu lassen.

**Schritt 2: Live-Recherche (optional, nur wenn OPENROUTER_API_KEY vorhanden)**

Frage Perplexity Sonar Pro via OpenRouter API nach aktuellen Studien:

```
POST https://openrouter.ai/api/v1/chat/completions
Headers: Authorization: Bearer $OPENROUTER_API_KEY
Model: perplexity/sonar-pro
Prompt: "Neuromarketing studies on color associations with
[PRIMARY_TRIGGER] and [SECONDARY_TRIGGER] 2020-2026. Cite sources.
Return hex code recommendations for primary and secondary brand color
with psychological reasoning."
```

Antwort als "Live-Research"-Block in die Empfehlung einfliessen lassen,
Quellen explizit nennen. Bei API-Fehler: Fallback auf Schritt 3 ohne
Warnung (Orchestrator-Prinzip — kein Abbruch bei externem Service).

**Schritt 3: Statische Ableitung aus §5 (immer)**

Unabhängig von der Live-Recherche: Leite eine Farb-Empfehlung aus
Haller (§5) + Primary/Secondary Trigger ab:

| Trigger | Typische Haller-Farbfamilie | Psychologische Wirkung |
|---|---|---|
| PASSION | Warm: Rot, Koralle, Terracotta | Emotionale Aktivierung, Wärme |
| INNOVATION | Bold: Electric Blue, Magenta, Limone | Neugier, Disruption |
| PRESTIGE | Tief: Dunkelblau, Gold, Bordeaux | Status, Exzellenz |
| POWER | Kontrast: Schwarz, Rot, Stahl | Klarheit, Dominanz |
| TRUST | Beständig: Warm-Blau, Grün, Beige | Verlässlichkeit, Ruhe |
| MYSTIQUE | Dunkel: Violett, Anthrazit, Silber | Selektivität, Tiefe |
| ALERT | Klar: Sicheres Blau, Warn-Orange, Grau | Präzision, Sorgfalt |

**Schritt 4: Kulturkontext prüfen**

Frage den Nutzer: "In welchen Kulturräumen operiert die Marke primär?
(Europa / Nordamerika / Asien / MENA / andere)"

Passe die Empfehlung an Haller-Hinweise auf kulturelle Farb-Assoziationen an
(z.B. Rot = Liebe in Europa vs. Glück in China).

**Schritt 5: Konkrete Empfehlung**

```
Farb-Empfehlung (Neuro-Color) für [Markenname]:

Primary Color:    [Hex] — [Begründung aus Trigger + §5]
Secondary Color:  [Hex] — [Begründung]
Accent Color:     [Hex] — [Begründung]
Background Light: [Hex]
Background Dark:  [Hex]

Kulturkontext: [Relevante Hinweise aus Haller §5]
[Falls Live-Recherche aktiv: Zusatz-Belege aus Perplexity Sonar]
```

### B5 — Sprach-Regeln (konsolidiert)

Fasse die Regeln aus B3 zu einem kompakten Regel-Set zusammen:
Anrede, Satzlänge, Aktiv/Passiv, Humor-Regeln, Wort-Verbote,
gewünschte vs. verbotene Formate.

### B6 — Visuelle Sprache (optional, nach Nächster Schritt)

Typografie-Charakter (Headline / Body / Accent) und Bildsprache
(5 × "wir zeigen" / 5 × "wir zeigen nie") bleiben als optionaler Block
erhalten. Sie sind nicht Pflicht-Section von Schema 05, aber operativ
nützlich als Übergang zu Skill 06.

Mood Board Prompt (für Midjourney/DALL-E/Claude):
```
Create a mood board for [Markenname].
Visual direction: [3–5 Adjektive].
Color palette: [Hex-Codes aus B4].
Imagery: [Beschreibung der Bildwelt].
Typography feeling: [Charakter].
Overall mood: [Atmosphäre].
Reference brands aesthetically similar: [2–3 Brands].
```

---

## MIRO BOARD BEFÜLLEN (falls aktiv)

Erstelle oder ergänze zwei Frames. Frame-IDs und Rahmen-Farben sind
spezifisch zu Skill 05 und stehen nicht in `artefact-templates.md` Teil 3
— sie werden hier inline definiert, weil der Miro-Spiegel für Skill 05
noch nicht im zentralen Frame-Katalog gelistet ist. (TODO: Aufnahme in
`artefact-templates.md` Teil 3 bei nächstem Minor-Bump.)

### Frame 1 — GOLDEN CIRCLE

- Grösse: 900×900px
- Rahmen-Farbe: `#4A90D9`
- Layout: 3 konzentrische Rechtecke (innen nach aussen)
  - Innerstes (200×200px, `#1B4F8A`): "WHY" + WHY Statement (klein, italic)
  - Mittleres Ring (`#2E75C3`): "HOW" + HOW 1/2/3
  - Äusserstes Ring (`#74B3CE`): "WHAT" + Angebote
- Darunter 3 Sticky Notes: Mission (gelb), Vision (grün), Hedgehog Sweet Spot (orange)

### Frame 2 — BRAND STORY & TONALITY

- Grösse: 900×1200px
- Rahmen-Farbe: Owlist Primary `#596A71` aus `artefact-templates.md` Teil 4
- Bereich 1 — Brand Story: Sticky (dunkelgrau) mit 1-Satz-Essenz + Sticky (mittelgrau) mit Elevator Pitch
- Bereich 2 — Identity: 3 grosse Sticky Notes mit Kern-Adjektiven, Charakter, Positioning
- Bereich 3 — Tonality: Sticky (hellgrün) "SO klingt die Marke", Sticky (hellrot) "SO klingt sie NICHT", Sticky (violett) Wort-Verbote
- Bereich 4 — Neuro-Color: Sticky mit Farbpalette (Hex) + Kulturkontext-Hinweis

---

## OUTPUTS ERSTELLEN

### Output 1: 05-story-identity.md

Lies Schema 05 aus `artefact-templates.md` Teil 1. Schreibe die Datei nach
`clients/[name]/outputs/05-story-identity.md` mit folgendem Header:

```
## [Projektname] | [Datum]
## Methodische Basis: §5 (Haller, Neuro-Color) + Sinek Golden Circle + Dante Labs | LUMEN³ by Owlist
```

**Pflicht-Sections (Reihenfolge wie in Schema 05):**

```
## Story-Kern
[WHY Statement, Story-Verbindung aus Teil A,
 + Brand Story in 3 Versionen aus Teil B1]

## Identity-Statement
[3 Kern-Adjektive + Charakter-Beschreibung + Positioning Statement aus B2]

## Tonalitäts-Profil
[5 Schreibstil-Adjektive + 5 Beispielsätze + 5 Gegenbeispiele aus B3]

## Farb-Empfehlung (Neuro-Color)
[Primary/Secondary/Accent/Background Hex + Begründung aus B4
 + Kulturkontext-Hinweis
 + Falls Live-Recherche aktiv: Perplexity-Quellen]

## Sprach-Regeln
[Konsolidierte Regeln + Wort-Verbote aus B5]

## Nächster Schritt
Weiter mit /lumen-universe — Brand Universe (Synthese)
```

Optionale Sections (nach den Pflicht-Sections, vor `Nächster Schritt`):
`## Golden Circle` (vollständiger Teil-A-Output für den Kunden),
`## Visuelle Sprache` (Typografie + Bildsprache + Mood Board Prompt aus B6).

### Output 2: slides-story.md

Slide-Set gemäss `artefact-templates.md` Teil 2 für Skill 05:
`cover, single-statement, grid-3x2, grid-3x2`

Layout-IDs müssen exakt mit `artefact-templates.md` übereinstimmen.

Inhalt pro Slide:
- **Slide 1 (cover):** Projektname, "Story & Identity", Datum
- **Slide 2 (single-statement):** WHY Statement als grosse Aussage
- **Slide 3 (grid-3x2):** 6 Tokens — 3 Kern-Adjektive + Primary Color + Headline-Typografie + 1-Satz-Essenz
- **Slide 4 (grid-3x2):** 6 Tokens — Mission + Vision + 3 Beispielsätze + Wort-Verbote + Secondary Color + Mood Board Prompt

### Output 3: Miro Board Update (falls aktiv)

Board-URL zurückgeben. Neue Frames bestätigen.

---

## ABSCHLUSS-MELDUNG

```
LUMEN² Story & Identity abgeschlossen.

Ergebnisse:
WHY:              "To [BEITRAG] so that [WIRKUNG]"
3 Kern-Adjektive: [Wort 1] · [Wort 2] · [Wort 3]
Tonalität:        [5 Adjektive]
Neuro-Color:      Primary [Hex] · Secondary [Hex]
Live-Recherche:   [Aktiv / Fallback auf §5]

Outputs:
05-story-identity.md — Schema 05, alle 5 Pflicht-Sections
slides-story.md       — 4 Slides (cover + 3× grid/single-statement)
[Falls Miro aktiv:] Golden Circle + Story Frames auf [Board-URL]

Weiter mit: /lumen-universe — Brand Universe (Synthese)
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

- Keine eigene Erklärung von Haller oder Neuro-Color im Skill selbst
  (kommt aus `methodology.md` §5, falls der Nutzer fragt)
- Keine eigenen Schema-Definitionen (Schema 05 aus `artefact-templates.md`)
- Keine eigenen Slide-Layouts (kommen aus `artefact-templates.md` Teil 2)
- Kein Abbruch bei fehlendem OPENROUTER_API_KEY — Fallback auf §5 ohne Warnung
- Kein Abbruch bei Miro-MCP-Ausfall — Markdown-only läuft weiter
- Keine Empfehlung ohne Trigger-Basis — wenn weder Skill 02 noch Skill 04
  vorhanden sind, wird die Farb-Empfehlung abgelehnt, nicht erfunden
- Keine Interpretation der Peaks-&-Valleys-Stories während des Interviews
  (still mitschreiben, nicht kommentieren)
- Schreibt niemals Memory-Inhalte in Kunden-Outputs (Markdown, Slides, Miro, PDF)
