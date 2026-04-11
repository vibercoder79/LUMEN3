---
name: lumen-learn
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-learn" eingibt oder
  "Muster aus Memory analysieren" sagt.

  Helper-Skill ausserhalb der LUMEN³-Sequenz. Liest alle Memory-Dateien
  (clients/*/memory.md), gruppiert die Blöcke pro Skill, identifiziert
  wiederkehrende Themen und produziert Verbesserungs-Vorschläge pro Skill.

  Schreibt nie selbst in Skill-Dateien. Der Stratege entscheidet, was
  übernommen wird.

  Datenbasis-Schwelle: mindestens 10 Einträge pro Skill. Darunter keine
  Musteranalyse, nur Hinweis auf die unzureichende Datenbasis.

  Output: lumen3/learnings/YYYY-MM-DD-patterns.md (intern, kein Deliverable)

  Version 1.0 — April 2026
---

# LUMEN³ — Learn (Memory Pattern Analyzer)
## Interner Helper-Skill | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Teil 7 — Memory-Schema)
- `clients/*/memory.md` (mindestens eine valide Datei)
- Zielordner `lumen3/learnings/` für Output-Datei

Dieser Skill ist nicht Teil der LUMEN³-Sequenz. Er wird manuell vom
Strategen aufgerufen und produziert Vorschläge zur Skill-Verbesserung.
Die Ergebnisse fliessen niemals automatisch in Skills oder Kunden-Outputs.

---

## Verhaltensprinzipien

- Lies beide Felder jedes Blocks (strategisch UND intern). `/lumen-learn`
  gehört zu den wenigen Skills, die das interne Feld lesen dürfen.
- Der Output ist ein Arbeitsdokument für den Strategen, kein Deliverable.
- Zitiere Quellen präzise: welcher Kunde, welche Version, welches Datum.
- Unterscheide Einzelfall und Muster. Ein Einzelfall ist kein Muster.
- Schreibe niemals Änderungen in Skill-Dateien. Der Stratege entscheidet.
- Übernimm niemals den Wortlaut aus internen Feldern in den Output.
  Interne Felder dienen nur der Interpretation, nicht der Zitation.

---

## SCHRITT 0 — Datenbasis scannen

Suche alle Dateien im Glob `clients/*/memory.md`. Für jede Datei:

1. Lies alle H3-Blöcke gemäss Regex
   `^### (\d{4}-\d{2}-\d{2}) \| Skill (\d{2}) \| v(\d+) \| (\w+)$`
2. Parse Datum, Skill-Nummer, Version, Status
3. Lies strategisches und internes Feld separat
4. Speichere pro Block: Kunde, Datum, Skill, Version, Status, Dauer,
   strategisch, intern

Zeige dem Strategen eine Übersicht:

```
Gescannt: [N] Memory-Dateien über [M] Kunden.
Gesamt-Blöcke: [X]

Pro Skill:
  Skill 01:  [N] Einträge
  Skill 02:  [N] Einträge
  Skill 03:  [N] Einträge
  Skill 04:  [N] Einträge
  Skill 05:  [N] Einträge
  Skill 06:  [N] Einträge
```

---

## SCHRITT 1 — Datenbasis-Schwelle prüfen

Pro Skill separat prüfen:

- **<10 Einträge:** Keine Musteranalyse. Im Output erscheint nur eine Zeile:
  ```
  Skill [NN]: [N] Einträge vorhanden, ab 10 wird die Analyse stabil.
  Datenbasis noch zu klein für aussagekräftige Muster.
  ```
- **≥10 Einträge:** Weiter mit SCHRITT 2.

---

## SCHRITT 2 — Muster erkennen (nur Skills über Schwelle)

Für jeden Skill mit ≥10 Einträgen:

1. Gruppiere strategische Felder thematisch. Ein Thema gilt als Muster,
   wenn es in mindestens **drei unabhängigen Kunden-Sessions** auftaucht.
   Ein Thema in zwei Sessions bleibt Einzelfall.
2. Für jedes Muster: Wie oft tritt es auf? Bei welchen Kunden? Gibt es
   eine zeitliche Tendenz (zieht an, zieht ab)?
3. Lies interne Felder als Kontext — aber übernimm den Wortlaut niemals.
4. Formuliere pro Muster einen konkreten, handlungsorientierten
   Verbesserungs-Vorschlag für den betroffenen Skill.

Modell-Wahl: Sonnet für die thematische Gruppierung. Opus nur bei mehr
als 50 Blöcken pro Skill.

---

## SCHRITT 3 — Output schreiben

Schreibe `lumen3/learnings/YYYY-MM-DD-patterns.md` mit folgender Struktur:

```markdown
# LUMEN³ — Learn Patterns
## [Datum] | intern, nicht für Kunden

## Datenbasis
- Gescannt: [N] Kunden, [X] Memory-Blöcke gesamt
- Zeitraum: [frühestes Datum] bis [spätestes Datum]
- Schwelle: 10 Einträge pro Skill für Musteranalyse

## Skill [NN] — [Skill-Name]
**Einträge:** [N] (über Schwelle)

### Muster 1: [Titel]
**Vorkommen:** [X] von [N] Sessions, [K] unabhängige Kunden
**Quellen:** [Kunde A v1 2026-04-11], [Kunde B v2 2026-04-25], [Kunde C v1 2026-05-02]
**Beobachtung:** [Zusammenfassung, keine Zitate aus internem Feld]
**Verbesserungs-Vorschlag:** [Konkrete Handlungsempfehlung]

### Muster 2: ...

## Skill [NN] — [Skill-Name]
**Einträge:** [N] (unter Schwelle, keine Analyse)

---

## Offene Fragen an den Strategen
- [Frage 1, wenn Interpretation unklar ist]
- [Frage 2]
```

Der Stratege liest das Output-File, bewertet die Vorschläge und entscheidet
manuell, welche in Skill-Updates einfliessen.

---

## ABSCHLUSS-MELDUNG

```
LUMEN³ Learn abgeschlossen.

Datenbasis: [N] Kunden, [X] Memory-Blöcke gesamt
Über Schwelle (≥10): Skills [Liste]
Unter Schwelle (<10): Skills [Liste]

Muster gefunden: [Gesamtzahl]
Vorschläge: [Gesamtzahl]

Output:
lumen3/learnings/[Datum]-patterns.md — Arbeitsdokument für den Strategen

Nächster Schritt: Lies die Muster und entscheide manuell, welche in
Skill-Updates einfliessen. /lumen-learn übernimmt nichts selbst.
```

---

## Was dieser Skill explizit NICHT tut

- Schreibt nicht selbst in Skill-Dateien. Der Stratege entscheidet.
- Interpretiert Einzelfälle nicht als Muster. Schwelle: drei unabhängige
  Kunden pro Thema.
- Analysiert keine Skills unter 10 Einträgen. Datenbasis zu klein.
- Übernimmt den Wortlaut interner Felder niemals in den Output.
- Produziert kein Kunden-Deliverable. Der Output liegt in `lumen3/learnings/`,
  nie in `clients/[name]/outputs/`.
- Löscht oder verändert keine Memory-Dateien. Memory bleibt append-only.
