---
name: lumen-business-context
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-business-context" eingibt,
  "/lumen1" oder "Starte Business Context Interview" sagt.

  Dieser Skill führt das LUMEN¹ Business Context Interview durch —
  40 Fragen in 8 Blöcken — und erstellt danach 01-business-context.md
  gemäss Schema 01 aus artefact-templates.md.

  Schemas, Layouts, Tokens: artefact-templates.md
  Dieser Skill hat keine externe methodische Quelle und verweist
  nicht auf methodology.md.

  Output:
  - 01-business-context.md (Schema 01)

  Version 1.4 — April 2026
---

# LUMEN¹ — Business Context Interview
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 01, Teil 7 Memory)
- `clients/[name]/` als Zielordner für den Output
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Dieser Skill ist ein reines Discovery-Interview und hat keine
wissenschaftliche Quelle. Er verweist nicht auf `methodology.md`.

---

## Verhaltensprinzipien

- Stelle IMMER nur eine Frage auf einmal. Niemals mehrere Fragen gleichzeitig.
- Warte auf die vollständige Antwort, bevor die nächste Frage folgt.
- Bestätige jede Antwort mit einem kurzen, wertschätzenden Satz (max. 1 Zeile).
- Stelle eine Vertiefungsfrage, wenn die Antwort sehr kurz ist (unter 2 Sätzen).
- Überspringe keine Fragen. Wenn der Nutzer "weiter" sagt, stelle die nächste.
- Halte den Ton professionell, neugierig und wertungsfrei.
- Führe intern eine Nummerierung mit (Frage X/40).

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/01-business-context.md` nicht: weiter mit
EINSTIEG, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 01 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## EINSTIEG

Begrüsse mit folgendem Text:

```
🦉 LUMEN¹ Business Context Interview von Owlist.

40 Fragen in 8 Blöcken. Plane 60–90 Minuten ein.
Du kannst jederzeit pausieren und später weitermachen.

Schreibe ausführlich in ganzen Sätzen. Je mehr Kontext du gibst,
desto genauer kann ich in den folgenden LUMEN²- und LUMEN³-Skills
arbeiten.

Bereit? Dann starten wir mit Block 1.
```

---

## BLOCK 1 — Du & Dein Business (F1–F4)

Blockansage: "**Block 1 von 8 — Du & dein Business**"

F1: Was genau machst du? Beschreibe dein Business so, als würdest du es einem klugen Fremden in 2 Minuten erklären.

F2: Was ist dein übergeordnetes Ziel für die nächsten 12–36 Monate — finanziell, zeitlich und persönlich?

F3: Was unterscheidet dich als Unternehmer oder Dienstleister von anderen in deinem Markt? Was macht dich besonders?

F4: Was sind deine grössten Stärken im Business — und wo weisst du, dass du Schwächen hast?

## BLOCK 2 — Zielgruppe & Markt (F5–F8)

Blockansage: "**Block 2 von 8 — Zielgruppe & Markt**"

F5: Wer ist dein idealer Kunde? Beschreibe ihn oder sie so konkret wie möglich: Branche, Rolle, Unternehmensgrösse, typische Herausforderungen.

F6: Was ist das grösste Problem oder der grösste Schmerzpunkt deiner Zielgruppe — in deren eigenen Worten?

F7: Welche Alternativen nutzt deine Zielgruppe heute, um dieses Problem zu lösen? (Wettbewerber, Eigenlösungen, gar nichts)

F8: Was sind die häufigsten Gründe, warum Interessenten "Nein" oder "Nicht jetzt" sagen?

## BLOCK 3 — Angebot & Geschäftsmodell (F9–F12)

Blockansage: "**Block 3 von 8 — Angebot & Geschäftsmodell**"

F9: Was ist dein Hauptangebot? Beschreibe es mit Leistungsumfang, Laufzeit, Preis und Zahlungsmodell.

F10: Welches konkrete, messbare Ergebnis versprichst du deinen Kunden?

F11: Warum ist dein Angebot für deinen Kunden der bessere Deal im Vergleich zur nächstbesten Alternative?

F12: Hast du neben deinem Kernangebot weitere Produkte? (Einstiegsangebote, Upsells, Abo-Modelle, Zusatzleistungen)

## BLOCK 4 — Kundengewinnung & Sichtbarkeit (F13–F16)

Blockansage: "**Block 4 von 8 — Kundengewinnung & Sichtbarkeit**"

F13: Wie gewinnst du aktuell deine Kunden? Welche Kanäle nutzt du?

F14: Welcher Kanal bringt dir die meisten und besten Leads?

F15: Was investierst du aktuell in Marketing — Zeit, Geld, Energie? Und wie zufrieden bist du mit dem Ergebnis?

F16: Hast du einen funktionierenden Prozess, der regelmässig Content oder Kampagnen produziert — oder passiert das eher sporadisch?

## BLOCK 5 — Vertrieb & Verkaufsprozess (F17–F20)

Blockansage: "**Block 5 von 8 — Vertrieb & Verkaufsprozess**"

F17: Wie sieht dein Verkaufsprozess aus — vom ersten Kontakt bis zum Abschluss? Beschreibe die einzelnen Schritte.

F18: Wie hoch ist deine Abschlussquote ungefähr? Unterscheidest du zwischen warmen und kalten Leads?

F19: Was sind die Top-3-Gründe, warum Menschen bei dir nicht kaufen?

F20: Wie gehst du mit Interessenten um, die nicht erscheinen oder nicht kaufen? Hast du einen Follow-up-Prozess?

## BLOCK 6 — Leistungserbringung & Kundenerfolg (F21–F24)

Blockansage: "**Block 6 von 8 — Leistungserbringung & Kundenerfolg**"

F21: Was passiert konkret, nachdem ein Kunde bei dir gekauft hat? Beschreibe den Ablauf Woche für Woche.

F22: Wie schnell erleben deine Kunden ihren ersten Erfolg? Und wie lange dauert es bis zum vollen Ergebnis?

F23: Welcher Anteil deiner Kunden erreicht das versprochene Ergebnis tatsächlich?

F24: Was würde brechen, wenn du morgen doppelt so viele Kunden hättest? Wo ist der Engpass in deiner Lieferung?

## BLOCK 7 — Kundenbindung, Finanzen & Team (F25–F32)

Blockansage: "**Block 7 von 8 — Kundenbindung, Finanzen & Team**"

F25: Wie lange bleiben deine Kunden im Durchschnitt bei dir — oder kaufen sie einmalig?

F26: Welche Möglichkeiten gibt es für deine Kunden, nach dem ersten Kauf weiterzumachen? (Folgeprodukte, Community, Betreuung)

F27: Wie hoch ist der durchschnittliche Kundenwert über die gesamte Zusammenarbeit hinweg?

F28: Holst du aktiv Feedback ein? Wenn ja, wie — und was hörst du am häufigsten?

F29: Wie hoch war dein Umsatz in den letzten 12 Monaten? Und wie viel Gewinn ist davon übrig geblieben?

F30: Welches Angebot trägt den grössten Anteil an deinem Umsatz?

F31: Weisst du, was dich ein neuer Kunde kostet (Akquisekosten)? Falls ja — wie hoch?

F32: Was sind deine grössten monatlichen Fixkosten?

## BLOCK 8 — Team, Systeme & KI-Status (F33–F40)

Blockansage: "**Block 8 von 8 — Team, Systeme & KI**"

F33: Arbeitest du alleine oder hast du ein Team? Wenn Team — wer macht was?

F34: Welche Aufgaben in deinem Business fressen die meiste Zeit — und welche davon könnten theoretisch automatisiert werden?

F35: Welche Tools und Systeme nutzt du aktuell? (CRM, Projektmanagement, Buchhaltung, E-Mail-Marketing, Social Media)

F36: Welche Prozesse hast du dokumentiert — und welche existieren nur in deinem Kopf?

F37: Welche KI-Tools nutzt du aktuell? (ChatGPT, Claude, Gemini, Perplexity, Copilot — oder noch gar keins)

F38: Wofür setzt du KI heute ein? Und wo denkst du: "Da müsste doch mehr gehen"?

F39: Was ist dein grösster Frust oder deine grösste Hürde im Umgang mit KI?

F40: Wenn die KI ab morgen wie ein erfahrener Geschäftspartner für dich arbeiten könnte — was wäre der erste Bereich, den du ihr übergeben würdest?

---

## OUTPUT ERSTELLEN

Nach Abschluss aller 40 Fragen bestätige:

```
Interview abgeschlossen. Alle 40 Fragen beantwortet.
Ich erstelle jetzt dein 01-business-context.md.
```

Lies Schema 01 aus `artefact-templates.md` Teil 1. Schreibe die Datei
nach `clients/[name]/outputs/01-business-context.md` mit folgendem Header:

```
# LUMEN¹ — Business Context
## [Projektname] | [Datum]
## Framework: LUMEN³ by Owlist
```

### Block-zu-Section Mapping (Pflicht)

Die 40 Fragen werden auf die vier Pflicht-Sections von Schema 01 verdichtet:

| Schema-Section | Gespeiste Blöcke |
|---|---|
| `## 1. Business & Person` | Block 1 (F1–F4), Block 8 Team-Teil (F33) |
| `## 2. Zielgruppe & Markt` | Block 2 (F5–F8) |
| `## 3. Angebot & Versprechen` | Block 3 (F9–F12), Block 6 (F21–F24), Block 7 Finanzen (F29–F32) |
| `## 4. Sichtbarkeit & Kundenfeedback` | Block 4 (F13–F16), Block 5 (F17–F20), Block 7 Kundenbindung (F25–F28) |

Schreibe jede Section als strukturierten Fliesstext, nicht als Q&A-Liste.

Danach die beiden letzten Pflicht-Sections:

- `## Brand-Strategische Insights` — 3–5 wichtigste Beobachtungen und
  Handlungsempfehlungen, die sich aus den Antworten ergeben
- `## Offene Fragen / Lücken` — was nicht beantwortet oder unklar war,
  wichtig für die folgenden LUMEN²-Skills
- `## Nächster Schritt` — Verweis auf `/lumen-archetype`

Die KI-Status-Fragen (F34–F40) fliessen in die `Brand-Strategische Insights`
ein, nicht in eine eigene Section.

---

## ABSCHLUSS-MELDUNG

```
LUMEN¹ Business Context abgeschlossen.

01-business-context.md — Schema 01, 40 Fragen verdichtet auf
die vier Pflicht-Sections, plus Insights und offene Lücken.

Weiter mit: /lumen-archetype — Brand Archetype Assessment
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

- Keine eigene Schema-Definition (kommt aus `artefact-templates.md` Teil 1)
- Keine wissenschaftliche Methodik — dies ist ein reines Discovery-Interview
- Keine Brand-Analyse oder -Empfehlung (das ist Aufgabe der LUMEN²-Skills)
- Keine Miro-Integration — dieser Skill erzeugt nur Markdown
- Keine Slides — Schema 01 hat kein definiertes Slide-Set
- Keine Dokumente entgegennehmen, die im Chat eingefügt werden — verweise
  auf `clients/[name]/input/`
- Schreibt niemals Memory-Inhalte in Kunden-Outputs (Markdown, Slides, Miro, PDF)
