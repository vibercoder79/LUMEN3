---
name: lumen-interview
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-interview" eingibt
  oder "Starte Brand Interview" oder "We Are We Are Not" sagt.

  Dieser Skill führt das strukturierte Brand Personality Interview durch —
  72 Adjektive in 7 Gruppen, sortiert nach 4 Kategorien (Core / Aspiration /
  Unsicher / Nicht).

  Methodische Basis: §1 (Aaker, Meyerson) + §4 (Card Sort), siehe methodology.md
  Schemas, Frames, Layouts: artefact-templates.md
  Adjektiv-Trigger-Mapping: trigger-mapping.md

  Output:
  - 03-brand-interview.md (Schema 03 aus artefact-templates.md)
  - Miro Board mit 4 Frames (wenn Miro MCP aktiv)
  - slides-we-are-not.md (Slide-Set für Skill 03 — für Claude Design Rendering)

  Rendering: slides-we-are-not.md wird (nach Skill 06) zusammen mit
  design-brief.md an Claude Design (Anthropic, seit 2026-04-17)
  übergeben für PPTX/PDF/Canva-Export im Corporate-Design.

  Version 1.5 — April 2026 (Claude-Design-Integration)
---

# LUMEN² — Brand Interview: We Are / We Are Not
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 03, Frames, Slide-Set, Teil 7 Memory)
- `lumen3/methodology.md` (§1, §4 — wissenschaftliche Begründung bei Bedarf)
- `lumen3/trigger-mapping.md` (Adjektiv-Schreibweisen, von Skill 04 später benötigt)
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Methodische Basis: §1 (Aaker, Meyerson) und §4 (Card Sort).
Verweise dem Nutzer auf `methodology.md` nur dann, wenn er explizit nach
der wissenschaftlichen Quelle fragt.

---

## Verhaltensprinzipien

- Stelle IMMER nur eine Gruppe von Wörtern auf einmal vor.
- Warte auf vollständige Sortierung bevor die nächste Gruppe folgt.
- Keine Wertung oder Kommentierung während des Interviews.
- Nachfragen erlaubt: "Was meinst du mit [Wort]?" wenn unklar.
- Adjektive werden in der englischen Schreibweise gespeichert
  (siehe `trigger-mapping.md`) — sonst bricht Skill 04 das Scoring ab.
- Am Ende: Zusammenfassung und Muster-Analyse.

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/03-brand-interview.md` nicht: weiter mit
EINSTIEG, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 03 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit im Interview berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## EINSTIEG

Begrüsse mit folgendem Text:

```
🦉 LUMEN² Brand Interview von Owlist.

"We Are / We Are Not" — die Karten-Übung, um die Persönlichkeit deiner
Marke zu definieren. Du sortierst 72 Adjektive in 7 Gruppen.

Zwei kurze Fragen zuerst:

1. Sprache?
   Deutsch (Standard) | English | Français | Andere

2. Miro Board erstellen?
   - Ja: Ich erstelle ein Miro Board mit 4 Frames (braucht Miro MCP)
   - Nein: Nur Markdown-Output im Projektordner

(Standard: Deutsch, Miro Ja — falls MCP aktiv)
```

Prüfe ob Miro MCP verfügbar ist. Bei Ausfall: Markdown-only, ohne Warnung
(Miro-Spiegel-Prinzip aus `CLAUDE.md`).

---

## MIRO SETUP (falls Miro aktiv)

Erstelle ein neues Miro Board mit den vier Frames aus
`artefact-templates.md` Teil 3:

- Board-Name: `[Projektname] — LUMEN² We Are / We Are Not`
- Frames: `wir-sind-core`, `wir-sind-aspiration`, `wir-sind-unsicher`, `wir-sind-nicht`
- Layout pro Frame: gemäss Definition in `artefact-templates.md`
- Board-Header: gemäss Vorlage in `artefact-templates.md` Teil 3

Keine eigenen Frame-Definitionen erfinden. Alle Farben, Grössen und Layouts
kommen aus der zentralen Datei.

---

## DAS INTERVIEW — 7 Gruppen mit 72 Adjektiven

Instruktion (einmalig, beim ersten Mal):

```
So funktioniert es:
Ich zeige dir Wörter in Gruppen. Sortiere jedes Wort in eine von 4 Kategorien:

CORE: Kern-Eigenschaft unserer Marke
ASPIRATION: Das streben wir an, sind es aber noch nicht
UNSICHER: Passt manchmal — wir sind uns uneinig
NICHT: Diese Eigenschaft ist explizit NICHT wir

Antworte einfach: "reliable: core, bold: nicht, warm: aspiration..."
```

### GRUPPE 1 — Persönlichkeit & Charakter
1. Genuine / Authentisch
2. Warm / Herzlich
3. Bold / Mutig
4. Playful / Verspielt
5. Serious / Ernsthaft
6. Cheerful / Fröhlich
7. Wholesome / Bodenständig
8. Daring / Wagemutig
9. Spirited / Leidenschaftlich
10. Imaginative / Fantasievoll
11. Unique / Einzigartig
12. Trendy / Modern

### GRUPPE 2 — Kompetenz & Vertrauen
1. Reliable / Verlässlich
2. Intelligent / Intelligent
3. Successful / Erfolgreich
4. Hardworking / Fleissig
5. Secure / Sicher
6. Innovative / Innovativ
7. Expert / Fachkundig
8. Rigorous / Präzise
9. Focused / Fokussiert
10. Experienced / Erfahren
11. Confident / Selbstsicher
12. Technical / Technisch

### GRUPPE 3 — Stil & Ästhetik
1. Charming / Charmant
2. Elegant / Elegant
3. Smooth / Geschmeidig
4. Glamorous / Glamourös
5. Feminine / Feminin
6. Upper class / Exklusiv
7. Refined / Verfeinert
8. Prestigious / Prestige
9. Sophisticated / Anspruchsvoll
10. Minimal / Minimalistisch
11. Clean / Klar
12. Luxurious / Luxuriös

### GRUPPE 4 — Energie & Haltung
1. Tough / Stark
2. Rugged / Rau
3. Outdoorsy / Naturverbunden
4. Rebellious / Rebellisch
5. Disruptive / Disruptiv
6. Provocative / Provokativ
7. Edgy / Kantig
8. Raw / Ungeschliffen
9. Energetic / Energetisch
10. Powerful / Kraftvoll
11. Masculine / Maskulin
12. Western / Traditionell-bodenständig

### GRUPPE 5 — Beziehung & Kommunikation
1. Approachable / Zugänglich
2. Inspiring / Inspirierend
3. Empathetic / Empathisch
4. Direct / Direkt
5. Conversational / Gesprächig
6. Formal / Förmlich
7. Authoritative / Autoritär
8. Inclusive / Inklusiv
9. Exclusive / Exklusiv
10. Transparent / Transparent
11. Reserved / Zurückhaltend
12. Open / Offen

### GRUPPE 6 — Werte & Haltung
1. Purposeful / Sinngetrieben
2. Sustainable / Nachhaltig
3. Visionary / Visionär
4. Traditional / Traditionell
5. Progressive / Fortschrittlich
6. Pragmatic / Pragmatisch
7. Idealistic / Idealistisch
8. Rational / Rational
9. Intuitive / Intuitiv
10. Discreet / Diskret
11. Ethical / Ethisch
12. Ambitious / Ehrgeizig

### GRUPPE 7 — Freie Runde
Frage: Gibt es Eigenschaften, die deine Marke beschreiben und in den
bisherigen Gruppen gefehlt haben? Nenne 3-7 eigene Wörter und sortiere
sie direkt.

---

## AUSWERTUNG

Nach allen 7 Gruppen prüfe intern:

1. **Core-Cluster:** Welche Aaker-Dimension dominiert bei CORE?
2. **Abgrenzungs-Profil:** Was steht konsequent auf NICHT?
3. **Spannungen:** Gibt es Widersprüche zwischen Adjektiven auf CORE?
4. **Lücken:** Was wurde auf UNSICHER gelegt?
5. **Kongruenz mit Archetyp:** Vergleich mit `02-brand-archetype.md` falls vorhanden.

### Ergebnis-Präsentation

```
WIR SIND (Core — [N] Eigenschaften):
[Alle CORE-Wörter als Liste]
Dominante Dimension: [Aaker-Dimension]

WIR STREBEN AN (Aspiration — [N]):
[Alle ASPIRATION-Wörter]

UNSICHER ([N]):
[Alle UNSICHER-Wörter]

WIR SIND NICHT ([N]):
[Alle NICHT-Wörter]

Insights:
1. [Insight 1]
2. [Insight 2]
3. [Kongruenz mit Archetyp]
```

---

## OUTPUTS ERSTELLEN

### Output 1: 03-brand-interview.md

Lies Schema 03 aus `artefact-templates.md` Teil 1. Schreibe die Datei nach
diesem Schema. **Pflicht-Format in den vier Wort-Sections:** Markdown-Liste,
ein Adjektiv pro Zeile, in der englischen Schreibweise aus `trigger-mapping.md`
(z.B. `- Inspiring`, nicht `- inspirierend`).

H2-Header der Datei:
```
## [Projektname] | [Datum]
## Methodische Basis: §1 (Aaker, Meyerson) + §4 (Card Sort) | LUMEN³ by Owlist
```

### Output 2: slides-we-are-not.md

Slide-Set gemäss `artefact-templates.md` Teil 2 für Skill 03:
`cover, overview-2col, single-statement, single-statement, single-statement`

Inhalt pro Slide:
- **Slide 1 (cover):** Projektname, "Brand Interview", Datum
- **Slide 2 (overview-2col):** Linke Spalte CORE (grün), rechte Spalte NICHT (koralle)
- **Slide 3 (single-statement):** Dominante Aaker-Dimension als Aussage
- **Slide 4 (single-statement):** Wichtigste Abgrenzung (Top NICHT-Wort mit Kontext)
- **Slide 5 (single-statement):** Offene Frage (wichtigstes UNSICHER-Wort)

Layout-IDs müssen exakt mit `artefact-templates.md` übereinstimmen.

### Output 3: Miro Board (falls aktiv)

Sticky-Notes pro Frame gemäss `wir-sind-*` Frame-Definitionen aus
`artefact-templates.md` Teil 3. Sticky-Farben sind dort festgelegt — keine
eigenen Farben verwenden.

---

## ABSCHLUSS-MELDUNG

```
LUMEN² Brand Interview abgeschlossen.

03-brand-interview.md — Vollständige Auswertung
slides-we-are-not.md — 5 Slides
[Falls Miro aktiv:] Miro Board: [URL]

Zusammenfassung:
WIR SIND (Core): [N] | Dominanz: [Aaker-Dim.]
ASPIRATION: [N]
UNSICHER: [N] — klären
WIR SIND NICHT: [N]

Weiter mit: /lumen-trigger — Neuromarketing Trigger Analyse
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

- Keine eigenen Frame-Farben definieren (kommen aus `artefact-templates.md`)
- Keine eigenen Slide-Layouts definieren (kommen aus `artefact-templates.md`)
- Keine wissenschaftliche Erklärung der Methodik im Skill selbst
  (kommt aus `methodology.md`, falls der Nutzer fragt)
- Kein Trigger-Scoring (das macht Skill 04)
- Adjektive nicht ins Deutsche übersetzen beim Speichern
  (würde Skill 04 brechen)
- Schreibt niemals Memory-Inhalte in Kunden-Outputs (Markdown, Slides, Miro, PDF)
