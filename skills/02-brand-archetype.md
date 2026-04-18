---
name: lumen-archetype
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-archetype" eingibt,
  "Starte Brand Archetype Assessment" oder "LUMEN Archetype" sagt.

  Dieser Skill ermittelt den Brand-Archetyp mit zwei Methoden — wahlweise
  einzeln oder kombiniert:

  METHODE A — Fascinate Advantage Assessment (Hogshead 2014)
  28 Aussagen auf 4-Punkt-Skala → 7 Advantages → 49-Archetypen-Matrix.

  METHODE B — Brand Archetypen (Pearson/Jung)
  20 szenariobasierte Fragen → 12 Archetypen in 4 Quadranten.

  METHODE C — Dual Method (empfohlen für vollständiges Profil)

  Methodische Basis: §2 (Pearson/Jung, Hogshead), siehe methodology.md
  Schemas, Layouts, Tokens: artefact-templates.md

  Voraussetzung: 01-business-context.md empfohlen, nicht zwingend.

  Output:
  - 02-brand-archetype.md (Schema 02 aus artefact-templates.md)
  - matrix.html (interaktive 49-Archetypen-Matrix)
  - slides-outline.md (Präsentations-Struktur — für Claude Design Rendering)

  Rendering: slides-outline.md wird (nach Skill 06) zusammen mit
  design-brief.md an Claude Design (Anthropic, seit 2026-04-17)
  übergeben für PPTX/PDF/Canva-Export im Corporate-Design.

  Version 1.5 — April 2026 (Claude-Design-Integration)
---

# LUMEN¹ — Brand Archetype Assessment (Dual Method)
## Ein Framework von Owlist | www.owlist.ch

---

## Voraussetzungen

- `lumen3/artefact-templates.md` (Schema 02, Owlist Brand-Tokens, Teil 7 Memory)
- `lumen3/methodology.md` (§2 — wissenschaftliche Begründung bei Bedarf)
- `clients/[name]/outputs/01-business-context.md` (empfohlen, nicht Pflicht)
- `clients/[name]/memory.md` (append-only, wird bei Re-Run gelesen)

Methodische Basis: §2 (Pearson/Jung, Hogshead). Verweise dem Nutzer auf
`methodology.md` nur dann, wenn er explizit nach der wissenschaftlichen
Quelle fragt.

---

## Determinismus-Klarstellung

Das Scoring in diesem Skill ist deterministisch:

- **Methode A (Fascinate):** Identische Antworten (1–4) auf identische
  Aussagen ergeben immer denselben Score und damit denselben Archetyp
  aus der 49-Matrix.
- **Methode B (Jung/Pearson):** Die Buchstaben-Optionen (a–l) vergeben
  fixe Punkte pro Archetyp. Identische Buchstaben-Antworten = identisches
  Ergebnis.
- **Freitext-Felder (F16–F20):** Fliessen NICHT ins Scoring ein. Sie
  dienen ausschliesslich der qualitativen Beschreibung und Kongruenz-Analyse.
- **Trigger-Mapping:** Die Ergebnisse von Skill 02 fliessen als Input in
  Skill 04 (Trigger-Analyse) ein — Gewichtung in `trigger-mapping.md`.

---

## Verhaltensprinzipien

- Stelle IMMER nur eine Frage oder Aussage auf einmal.
- Methode A: Zeige die Aussage, warte auf Wert 1–4.
- Methode B: Zeige Szenario mit Optionen, warte auf Buchstabe.
- Führe intern stille Auswertung — kein Zwischenergebnis zeigen.
- Erst nach der letzten Frage: Ergebnis präsentieren.
- Nummerierung intern mitführen (Frage X/28 resp. X/20).

---

## SCHRITT 0 — Memory-Re-Run-Check

Existiert `clients/[name]/outputs/02-brand-archetype.md` nicht: weiter mit
EINSTIEG, Memory-Version = `v1`.

Existiert sie: Lies `clients/[name]/memory.md`, extrahiere Blöcke mit
`| Skill 02 |` in der H3-Zeile, zeige dem Nutzer **nur** das strategische
Feld (nie das interne), frage: "Ich sehe [N] frühere Reflexion(en). Soll
ich diese Lessons im neuen Lauf berücksichtigen? (ja/nein)"

Bei `ja`: Lessons explizit berücksichtigen, Status = `wiederholt`.
Bei `nein`: Status = `abgeschlossen`. Version = nächste freie v-Nummer,
gekoppelt an Output-Datei-Suffix.

---

## EINSTIEG

Begrüsse mit folgendem Text:

```
🦉 LUMEN¹ Brand Archetype Assessment von Owlist.

Zwei kurze Fragen zuerst:

1. Sprache?
   Deutsch (Standard) | English | Français | Andere

2. Welche Methode?
   A — Fascinate Advantage (Hogshead) | 28 Aussagen, ~5–8 Min
       Misst: Wie du/dein Brand andere fasziniert
   B — Brand Archetypen (Pearson/Jung) | 20 Szenarien, ~20–25 Min
       Misst: Wer die Marke als Persönlichkeit ist
   C — Dual Method (empfohlen) | Beide Methoden, ~30–35 Min
       Tiefenprofil: Faszinations-Muster UND Markenidentität

(Standard: Deutsch, Methode C)
```

Warte auf Sprach- und Methoden-Wahl. Wechsle dann vollständig in die
gewählte Sprache für alle weiteren Fragen und den finalen Output.

---

## ═══════════════════════════════════════════
## METHODE A — FASCINATE ADVANTAGE ASSESSMENT
## ═══════════════════════════════════════════

### Kurz-Einführung (einmalig zeigen)

```
Die 7 Fascinate Advantages — wie du die Welt faszinierst:
Innovation · Passion · Power · Prestige · Trust · Mystique · Alert

Bewertung: 1 = Trifft überhaupt nicht zu / 4 = Trifft voll zu
Ich stelle dir 28 Aussagen — antworte jeweils mit 1, 2, 3 oder 4.
```

### Interne Advantage-Zuordnung (nicht anzeigen)

```
Q1=Power, Q2=Passion, Q3=Mystique, Q4=Alert, Q5=Prestige,
Q6=Innovation, Q7=Trust, Q8=Passion, Q9=Mystique, Q10=Alert,
Q11=Power, Q12=Prestige, Q13=Innovation, Q14=Alert, Q15=Passion,
Q16=Mystique, Q17=Trust, Q18=Power, Q19=Prestige, Q20=Innovation,
Q21=Trust, Q22=Passion, Q23=Mystique, Q24=Alert, Q25=Power,
Q26=Prestige, Q27=Innovation, Q28=Trust
```

### Die 28 Aussagen

Q1: Ich habe starke Meinungen und bin bereit, sie klar zu vertreten.
Q2: Ich bin bekannt dafür, besondere, farbenreiche Erlebnisse zu schaffen.
Q3: Ich verrate nicht alles auf einmal — ich lasse andere neugierig werden.
Q4: Ich lese Anleitungen und Dokumentationen sorgfältig durch, bevor ich beginne.
Q5: Andere holen sich meinen Rat, weil sie mich als Experten sehen.
Q6: Freiheit und persönliche Wahlmöglichkeiten sind mir sehr wichtig.
Q7: Andere würden mich als konsistent und beständig beschreiben.
Q8: Ich achte auf sinnliche Details — Atmosphäre, Musik, Stimmung, Ästhetik.
Q9: Ich habe einen kleinen, ausgewählten inneren Kreis — nicht viele, aber tiefe Verbindungen.
Q10: Deadlines und klare Fristen motivieren mich stark.
Q11: Ich suche aktiv nach Positionen, in denen ich Autorität und Führung habe.
Q12: Es ist mir wichtig, in meinem Umfeld als Fachperson respektiert zu werden.
Q13: Ich bin bekannt für überraschende, ungewöhnliche Ideen.
Q14: Ich respektiere Strukturen und Autoritäten sehr — ich halte mich gerne an Regeln.
Q15: Wenn ich einen Raum betrete, nehme ich zuerst die Atmosphäre wahr — Licht, Stimmung, Umgebung.
Q16: Selbst enge Freunde wissen nicht alles über mich.
Q17: Ich bevorzuge vertraute, etablierte Routinen gegenüber ständig Neuem.
Q18: Ich habe den Ruf, ein einflussreicher Leader zu sein.
Q19: Ich kommuniziere meine Erfolge gerne — subtil oder direkt.
Q20: Meine Individualität auszudrücken ist mir sehr wichtig.
Q21: Ich wähle bewährte Optionen statt zu experimentieren.
Q22: Ich kann sehr schnell eine emotionale Verbindung zu anderen aufbauen.
Q23: Andere haben manchmal Mühe zu wissen, was ich gerade denke.
Q24: Ich unternehme viel um Stress durch negative Ergebnisse zu vermeiden.
Q25: Ich suche Situationen, in denen ich viel Kontrolle über das Ergebnis habe.
Q26: Es ist mir wichtig, in meiner Peer-Group eine führende Rolle einzunehmen.
Q27: Ich bin bekannt für meinen witzigen, unerwarteten Humor.
Q28: Ich bin lieber verlässlich als einzigartig.

### Scoring-Logik (intern)

Pro Advantage: Summe der 4 zugehörigen Fragen (Min 4, Max 16)
- Primary Advantage = höchster Score
- Secondary Advantage = zweithöchster Score
- Dormant Advantage = niedrigster Score (Schwachstelle)
- Archetyp = Kombination Primary × Secondary → 49-Archetypen-Matrix

### Die 49-Archetypen-Matrix

*(Zeile = Primary, Spalte = Secondary)*

|  | Innovation | Passion | Power | Prestige | Trust | Mystique | Alert |
|---|---|---|---|---|---|---|---|
| **Innovation** | The Anarchy | The Rockstar | The Maverick Leader | The Trendsetter | The Artisan | The Provocateur | The Quick-Start |
| **Passion** | The Catalyst | The Drama | The People's Champion | The Talent | The Beloved | The Intrigue | The Orchestrator |
| **Power** | The Change Agent | The Ringleader | The Aggressor | The Maestro | The Guardian | The Mastermind | The Defender |
| **Prestige** | The Avant-Garde | The Connoisseur | The Victor | The Imperial | The Blue Chip | The Architect | The Scholar |
| **Trust** | The Evolutionary | The Authentic | The Gravitas | The Diplomat | The Old Guard | The Anchor | The Good Citizen |
| **Mystique** | The Secret Weapon | The Subtle Touch | The Veiled Strength | The Royal Guard | The Wise Owl | The Deadbolt | The Archer |
| **Alert** | The Composer | The Coordinator | The Ace | The Editor-in-Chief | The Mediator | The Detective | The Control Freak |

**Double-Advantages (Diagonale, Primary = Secondary):** The Anarchy, The Drama,
The Aggressor, The Imperial, The Old Guard, The Deadbolt, The Control Freak —
Überdosis eines einzigen Advantage, überwiegend negative Konnotationen.

---

## ═══════════════════════════════════════════
## METHODE B — BRAND ARCHETYPEN (PEARSON/JUNG)
## ═══════════════════════════════════════════

### Kurz-Einführung (einmalig zeigen)

```
Die 12 Brand Archetypen nach Pearson/Jung in 4 Quadranten:

Stabilität & Struktur:   Ruler, Caregiver, Creator
Zugehörigkeit & Genuss:  Everyman, Jester, Lover
Risiko & Meisterschaft:  Hero, Outlaw, Magician
Unabhängigkeit & Sinn:   Innocent, Sage, Explorer

Antworte auf die Szenarien mit dem Buchstaben der passenden Option.
```

### Interne Archetyp-Zuordnung (nicht anzeigen)

```
a=Innocent, b=Sage, c=Explorer, d=Outlaw, e=Magician,
f=Hero, g=Lover, h=Jester, i=Everyman, j=Caregiver,
k=Ruler, l=Creator
```

### Die 20 szenariobasierten Fragen

F1: Was ist der tiefste Antrieb deiner Marke?
a) Die Welt einfacher und optimistischer machen
b) Wissen und Wahrheit zugänglich machen
c) Menschen inspirieren, Neues zu entdecken
d) Den Status quo aufbrechen — radikal anders
e) Echte Transformation bewirken
f) Hindernisse überwinden, Stärke beweisen
g) Tiefe emotionale Verbindungen schaffen
h) Freude und Leichtigkeit bringen
i) Zugehörigkeit schaffen — für alle
j) Für andere sorgen und schützen
k) Ordnung, Qualität und Kontrolle sichern
l) Etwas völlig Neues erschaffen

F2: Ein Wettbewerber kopiert dein Angebot. Erste Reaktion?
a) Wir sind einfacher und ehrlicher — das merkt jeder
b) Unser Wissen ist nicht kopierbar
c) Wir denken schon drei Schritte weiter
d) Wir machen was sie nie wagen würden
e) Wir transformieren — sie kopieren nur
f) Wir liefern bessere Ergebnisse, immer
g) Unsere Beziehungen sind nicht kopierbar
h) Wir machen es lustiger als sie
i) Unsere Gemeinschaft trägt uns
j) Unsere Kunden wissen, dass wir für sie da sind
k) Unser System und Standard sind überlegen
l) Unsere nächste Innovation ist schon in Arbeit

F3: Welches Bild beschreibt deine Marke?
a) Sonnenaufgang — Reinheit, Neuanfang, Hoffnung
b) Bibliothek — Tiefe, Wissen, Orientierung
c) Offener Horizont — Weite, Freiheit, Möglichkeiten
d) Blitz — Energie, Provokation, Disruption
e) Verwandlung — Raupe wird Schmetterling
f) Gipfel — Überwindung, Sieg, Stärke
g) Kerzenlicht — Wärme, Intimität, Verbindung
h) Feuerwerk — Überraschung, Freude, Energie
i) Lagerfeuer — Gemeinschaft, Wärme, Zusammengehörigkeit
j) Schutzdach — Geborgenheit, Fürsorge, Sicherheit
k) Architektur — Präzision, Struktur, Beständigkeit
l) Leere Leinwand — Potenzial, Erschaffen, Originalität

F4: Was ist für deine Marke ein absolutes No-Go?
a) Angst als Motivator, Komplexität, Zynismus
b) Oberflächlichkeit, Halbwissen, Vereinfachung
c) Einschränkung, Konformismus, Angepasstheit
d) Kompromisse mit dem Establishment
e) Oberflächliche Lösungen ohne echten Wandel
f) Aufgeben, Schwäche, Selbstmitleid
g) Kälte, Distanz, rein rationale Kommunikation
h) Schwere, Verbissenheit, zu viel Ernst
i) Exklusivität, Arroganz, Elitismus
j) Gleichgültigkeit, Effizienz über Menschen
k) Chaos, Unprofessionalität, fehlende Struktur
l) Kopieren, Mittelmass, Konformität

F5: Welches Tier symbolisiert deine Marke?
a) Schmetterling — Reinheit, Leichtigkeit
b) Eule — Weisheit, Beobachtung
c) Wolf — Freiheit, Instinkt, Unabhängigkeit
d) Phönix — Rebellion, Erneuerung
e) Chamäleon — Transformation, Wandel
f) Löwe — Stärke, Mut, Führung
g) Schwan — Eleganz, Leidenschaft
h) Delphin — Verspieltheit, Intelligenz
i) Hund — Loyalität, Gemeinschaft
j) Biene — Fürsorge, Fleiss, Gemeinschaft
k) Adler — Überblick, Kontrolle, Stärke
l) Fuchs — Kreativität, Cleverness

F6: Wie klingt deine Marke wenn sie spricht?
a) Warm, einfach, klar — wie eine Freundin
b) Präzise, fundiert — wie ein Experte
c) Frisch, abenteuerlustig — wie ein Entdecker
d) Provokativ, mutig — wie ein Rebell
e) Visionär, bedeutsam — wie ein Visionär
f) Entschlossen, motivierend — wie ein Coach
g) Sinnlich, einladend — wie ein Verführer
h) Leicht, witzig — wie ein Comedian
i) Freundlich, bodenständig — wie ein Nachbar
j) Empathisch, geduldig — wie eine Mutter
k) Strukturiert, autoritär — wie ein CEO
l) Originell, experimentell — wie ein Künstler

F7: Welche Farb-Energie beschreibt deine Marke?
a) Weiss, Hellblau, Pastell — Reinheit, Klarheit
b) Dunkelblau, Gold, Grau — Tiefe, Autorität
c) Erdtöne, Orange, Türkis — Abenteuer, Natur
d) Schwarz, Rot, Electric Blue — Energie, Rebellion
e) Violett, Tief-Blau, Schwarz-Gold — Mystik, Transformation
f) Rot, Gold, Dunkelblau — Kraft, Sieg
g) Rot, Rosa, Bordeaux, Gold — Leidenschaft, Sinnlichkeit
h) Leuchtgelb, Orange — Energie, Freude
i) Beige, Braun, Warm-Grün — Bodenständigkeit
j) Sanftes Grün, Warm-Weiss — Fürsorge, Sicherheit
k) Dunkelblau, Schwarz, Gold — Autorität, Präzision
l) Bunt oder bewusst minimalistisch — Ausdruck, Originalität

F8: Deine Marke schreibt über einen Rückschlag. Wie klingt der Post?
a) "Manchmal läuft es nicht — und das ist okay. Weiter geht's ☀️"
b) "Was wir gelernt haben: [3 konkrete Erkenntnisse]"
c) "Das war unerwartet — aber jede Kurve zeigt neue Richtungen"
d) "Scheitern ist Teil des Systems das wir aufbrechen"
e) "Manchmal braucht Transformation einen Umweg"
f) "Kurzer Rückschlag. Aufstehen. Weiterkämpfen."
g) "Das hat uns berührt. Danke an alle, die dabei waren."
h) "Okay, das war ein Flop 😂 — aber was für eine Geschichte"
i) "Wir sind wie ihr — nicht perfekt. Aber wir sind dabei."
j) "An alle die gewartet haben — danke für eure Geduld."
k) "Analyse, Korrektur, Neustart. Bericht in 3 Wochen."
l) "Fehler sind Rohstoff — was entsteht daraus? Stay tuned."

F9: Welches Medium nutzt deine Marke am liebsten?
a) Persönliche Geschichten, einfache Videos, Wärme
b) Tiefgründige Artikel, Podcasts, Forschung, Fakten
c) Behind-the-Scenes, Reiseberichte, Entdeckungen
d) Manifeste, provokative Kampagnen
e) Transformations-Stories, "Vorher/Nachher", Rituale
f) Erfolgsgeschichten, Challenges, Motivations-Content
g) Ästhetische Inhalte, sinnliche Erlebnisse
h) Memes, Comedy, unerwartete Kampagnen
i) Community-Content, Testimonials, lokale Storys
j) How-to, Support-Content, Anleitungen
k) Fallstudien, Daten, Strukturberichte, Awards
l) Konzeptuelle Kampagnen, Kunst, Experimente

F10: Was sollen Kunden nach dem ersten Kontakt fühlen?
a) Erleichtert und optimistisch
b) Klüger und besser informiert
c) Inspiriert und frei
d) Aufgeweckt und herausgefordert
e) Transformiert — etwas hat sich verändert
f) Gestärkt und motiviert
g) Begehrt und emotional verbunden
h) Aufgeheitert und überrascht
i) Willkommen und dazugehörend
j) Umsorgt und sicher
k) Orientiert und in guten Händen
l) Inspiriert und kreativ angesteckt

F11: Welche historische Brand passt zu deiner Marke?
a) Dove — Natürlichkeit, Reinheit, echte Menschen
b) National Geographic — Wissen, Tiefe, Entdeckung
c) Patagonia — Freiheit, Natur, Authentizität
d) Harley-Davidson — Rebellion, Anti-Establishment
e) Apple (Jobs) — Transformation, "Think Different"
f) Nike — "Just Do It", Überwindung, Stärke
g) Chanel — Eleganz, Leidenschaft, Begehren
h) Old Spice — Humor, Überraschung, Leichtigkeit
i) IKEA — Für alle, bodenständig, demokratisch
j) Johnson & Johnson — Fürsorge, Sicherheit
k) Mercedes-Benz — Präzision, Autorität, Standards
l) Lego — Kreativität, Erschaffen, Möglichkeiten

F12: Dein grösster Wettbewerbsvorteil?
a) Wir machen es einfacher und freundlicher als alle
b) Wir denken tiefer und wissen mehr als alle anderen
c) Wir denken unabhängiger und mutiger
d) Wir wagen was andere nicht tun
e) Wir transformieren — nicht nur verbessern
f) Wir liefern wenn andere aufgeben
g) Wir schaffen echte emotionale Verbindung
h) Wir machen es leichter und unterhaltsamer
i) Wir sind nahbarer und echter
j) Wir sorgen mehr für Kunden als andere
k) Wir sind strukturierter und verlässlicher
l) Wir sind kreativer und origineller

F13: Wenn deine Marke eine Person wäre — ihre Rolle in der Gruppe?
a) Die unerschütterlich Optimistische
b) Die mit der fundiertesten Meinung
c) Die Erste die aufbricht um Neues zu entdecken
d) Die sagt was alle denken, aber keiner ausspricht
e) Die alles verändert wenn sie den Raum betritt
f) Die andere motiviert wenn es schwierig wird
g) Die alle liebt und geliebt wird
h) Die alle zum Lachen bringt
i) Die bei der sich alle wohlfühlen
j) Die für alle da ist
k) Die Ordnung und Richtung gibt
l) Die immer eine unerwartete Idee hat

F14: Deine Marke als Buchhandlung — welche Bücher stehen vorne?
a) Kinderbücher, positive Denken, Naturführer
b) Philosophie, Wissenschaft, Biographien grosser Denker
c) Reiseführer, Abenteuerromane, "Raus aus der Komfortzone"
d) Politische Manifeste, Systemkritik, Counterculture
e) Transformation, "Das Leben verändern", Visionen
f) Selbstoptimierung, Sport, Biographien von Leaders
g) Liebesromane, Kunstbände, Sinnlichkeit
h) Comedy, Satire, das absurdeste Buch aller Zeiten
i) Lokale Autoren, Kochbücher, "Für alle"
j) Erziehung, Gesundheit, Ratgeber
k) Business-Bestseller, Strategie, Management
l) Designbände, avantgardistische Literatur, Kunstbücher

F15: Was ist das Schlimmste was jemand über deine Marke sagen könnte?
a) "Kalt und naiv — ignoriert die Realität"
b) "Arrogant und unnahbar — lebt im Elfenbeinturm"
c) "Rastlos und unzuverlässig — immer woanders"
d) "Destruktiv und rücksichtslos"
e) "Esoterisch und unrealistisch"
f) "Arrogant und rücksichtslos gegenüber anderen"
g) "Oberflächlich und emotional manipulativ"
h) "Nicht ernst zu nehmen"
i) "Profillos und langweilig"
j) "Aufopfernd ohne Grenzen — kann nicht Nein sagen"
k) "Starr, kontrollierend, elitär"
l) "Chaotisch und selbstverliebt"

F16: Welche Adjektive beschreiben deine Marke? *(Freitext, mindestens 5)*

F17: Wie würden deine besten Kunden die Marke beschreiben? *(Freitext)*

F18: Welchen Archetyp ist deine Marke bewusst NICHT — und warum? *(Freitext)*

F19: Deine Marke kauft eine Zeitungsseite in der NZZ. Was steht drauf? *(Freitext)*

F20: Wenn deine Marke in 10 Jahren perfekt positioniert ist — wie sieht das aus? *(Freitext)*

### Scoring-Logik (intern)

1. Zähle pro Archetyp die Punkte aus allen a–l Antworten (F1–F15)
2. Primary Archetype = meiste Punkte
3. Shadow Archetype = zweithöchste Punkte
4. F16–F20 fliessen nicht ins Scoring, nur in die Kongruenz-Analyse

---

## ═══════════════════════════════════════════
## ARCHETYP-BIBLIOTHEK (operativ, Teil dieses Skills)
## ═══════════════════════════════════════════

Diese Profile sind inhaltlich Teil dieses Skills (nicht der `methodology.md`),
weil sie operativ nutzbar sein müssen — sie kommen direkt in den Output
und in die Slides.

### METHODE A — 7 Fascination Advantages

**INNOVATION** — "Change the game with creativity"
- Stärke: Originell, überraschend, trendsetzend, mutig
- Tonalität: Provokativ, frisch, kühn, visionär
- Farben: Unkonventionell, bunt oder hyperminimalistisch
- Gefahr: Unberechenbar, chaotisch, schwer zu verstehen
- Bild-Prompt: "A lightbulb exploding into colorful creative sparks, bold unconventional design, innovation energy, brand visualization"

**PASSION** — "Connect with emotion"
- Stärke: Warm, inspirierend, sinnlich, engagiert
- Tonalität: Emotional, leidenschaftlich, beziehungsorientiert
- Farben: Warm, lebendig, sinnlich — Rot, Gold, Bordeaux
- Gefahr: Zu emotional, dramatisch, unbeständig
- Bild-Prompt: "Two hands reaching toward each other with warm golden light between them, passion and connection brand visualization"

**POWER** — "Lead with command"
- Stärke: Entschlossen, autoritär, klar, wirkungsvoll
- Tonalität: Direkt, selbstbewusst, klar strukturiert
- Farben: Dunkelblau, Schwarz, Gold
- Gefahr: Dominant, einschüchternd, starr
- Bild-Prompt: "A strong architectural structure with clear lines and commanding presence, dark blue and gold tones, power brand visualization"

**PRESTIGE** — "Earn respect with higher standards"
- Stärke: Qualitätsbewusst, aspirational, differenziert
- Tonalität: Elegant, anspruchsvoll, selektiv
- Farben: Gold, Dunkelblau, Silber, Creme
- Gefahr: Arrogant, kalt, elitär
- Bild-Prompt: "A golden trophy or crown on a minimal dark background, prestige and excellence brand visualization, luxury aesthetic"

**TRUST** — "Build loyalty with consistency"
- Stärke: Verlässlich, konsistent, sicher, bewährt
- Tonalität: Ruhig, klar, bodenständig, faktenbasiert
- Farben: Warm-Blau, Grau-Grün, Beige
- Gefahr: Langweilig, veränderungsresistent, vorhersehbar
- Bild-Prompt: "A solid anchor in calm deep water, warm blue tones, trust and reliability brand visualization"

**MYSTIQUE** — "Communicate with substance"
- Stärke: Geheimnisvoll, tiefgründig, selektiv, faszinierend
- Tonalität: Zurückhaltend, substanziell, bedeutsam
- Farben: Dunkel, Schwarz, Tief-Violett, Silber
- Gefahr: Unnahbar, kalt, schwer zugänglich
- Bild-Prompt: "An owl in darkness with one eye visible, deep mystery and selective revelation, dark purple and black tones, mystique brand visualization"

**ALERT** — "Prevent problems with care"
- Stärke: Präzise, sorgfältig, vorausschauend, verlässlich
- Tonalität: Klar, strukturiert, warnend, schützend
- Farben: Sicheres Blau, Warn-Orange, Grau
- Gefahr: Übervorsichtig, lähmend, zu risikoavers
- Bild-Prompt: "A precise compass and detailed map with careful markings, alert and precision brand visualization, clean technical aesthetic"

### METHODE B — 12 Brand Archetypen

**THE INNOCENT** — "Es ist einfach und gut"
- Motivation: Sicherheit, Glück, Reinheit
- Tonalität: Warm, einfach, optimistisch, ehrlich
- Farben: Weiss `#FFFFFF`, Hellblau `#87CEEB`, Pastellgrün `#90EE90`
- Typografie: Rund, freundlich, leicht lesbar
- Gefahr: Zu naiv, ignoriert Realität
- Beispiele: Dove, Aveeno, Innocent Drinks
- Bild-Prompt: "A sunrise over a clean meadow, white and soft pastel colors, innocent and pure brand archetype visualization, minimal and hopeful"

**THE SAGE** — "Die Wahrheit macht frei"
- Motivation: Wahrheit, Wissen, Weisheit
- Tonalität: Präzise, fundiert, tiefgründig, respektvoll
- Farben: Dunkelblau `#003366`, Gold `#C9A84C`, Grau `#808080`
- Typografie: Serifen, klassisch, Autorität
- Gefahr: Zu akademisch, distanziert
- Beispiele: National Geographic, BBC, McKinsey, Google
- Bild-Prompt: "An owl on an open book with golden light rays, deep blue and gold tones, classical sage brand archetype illustration"

**THE EXPLORER** — "Du hast die Freiheit deinen Weg zu gehen"
- Motivation: Freiheit, Entdeckung, Authentizität
- Tonalität: Abenteuerlustig, unabhängig, authentisch
- Farben: Erdbraun `#8B4513`, Orange `#FF8C00`, Türkis `#40E0D0`
- Typografie: Robust, sans-serif, lebendig
- Gefahr: Rastlos, unbeständig
- Beispiele: Patagonia, REI, Jeep, North Face
- Bild-Prompt: "A lone figure on a mountain ridge at golden hour, earthy tones, explorer brand archetype, vast landscape and freedom"

**THE OUTLAW** — "Regeln existieren um gebrochen zu werden"
- Motivation: Revolution, Veränderung, Befreiung
- Tonalität: Provokativ, mutig, rebellisch, ungefiltert
- Farben: Schwarz `#000000`, Rot `#CC0000`, Electric Blue `#0066FF`
- Typografie: Bold, unkonventionell, Energie
- Gefahr: Destruktiv, rücksichtslos
- Beispiele: Harley-Davidson, Diesel, Virgin, Red Bull
- Bild-Prompt: "A phoenix breaking free from chains, bold black and red, rebellious outlaw brand archetype, high contrast dramatic"

**THE MAGICIAN** — "Ich kann dein Leben verwandeln"
- Motivation: Transformation, Vision, Wunder
- Tonalität: Visionär, inspirierend, bedeutsam, transformativ
- Farben: Violett `#8B008B`, Tief-Blau `#00008B`, Schwarz-Gold
- Typografie: Elegant, bedeutsam, ausdrucksstark
- Gefahr: Esoterisch, unrealistisch, manipulativ
- Beispiele: Apple (Jobs), Disney, Dyson, TED
- Bild-Prompt: "Hands transforming darkness into radiant light, deep purple and gold, magician brand archetype, elegant mystical illustration"

**THE HERO** — "Wo ein Wille ist, ist ein Weg"
- Motivation: Mut, Meisterschaft, die Welt verbessern
- Tonalität: Mutig, inspirierend, entschlossen, motivierend
- Farben: Rot `#CC0000`, Gold `#FFD700`, Dunkelblau `#003366`
- Typografie: Bold, stark, klar, dynamisch
- Gefahr: Arrogant, rücksichtslos, wettbewerbsbesessen
- Beispiele: Nike, Adidas, FedEx, Duracell
- Bild-Prompt: "A figure reaching a mountain peak at dawn, bold red and gold, heroic triumph brand archetype, determination and strength"

**THE LOVER** — "Du bist begehrt und einzigartig"
- Motivation: Verbindung, Leidenschaft, Intimität
- Tonalität: Sinnlich, leidenschaftlich, warm, einladend
- Farben: Bordeaux `#800020`, Rosa `#FFB6C1`, Gold `#FFD700`, Creme `#FFFDD0`
- Typografie: Elegant, kursiv, sinnlich
- Gefahr: Oberflächlich, zu emotional, people-pleasing
- Beispiele: Chanel, Alfa Romeo, Häagen-Dazs, Victoria's Secret
- Bild-Prompt: "Two hands almost touching with warm candlelight, rose and gold tones, lover brand archetype, intimate and passionate"

**THE JESTER** — "Das Leben ist zu kurz um ernst zu sein"
- Motivation: Freude, Leichtigkeit, im Moment leben
- Tonalität: Witzig, überraschend, leicht, energetisch
- Farben: Leuchtgelb `#FFD700`, Orange `#FF8C00`, kräftige Akzente
- Typografie: Verspielt, unkonventionell, lebendig
- Gefahr: Nicht ernst genommen werden, unzuverlässig wirken
- Beispiele: Old Spice, M&Ms, Innocent, Skittles, Ben & Jerry's
- Bild-Prompt: "A colorful explosion of confetti and playful shapes, bright yellow and orange, jester brand archetype, joyful and surprising energy"

**THE EVERYMAN** — "Du gehörst dazu — genau wie du bist"
- Motivation: Zugehörigkeit, Gleichheit, Gemeinschaft
- Tonalität: Freundlich, bodenständig, ehrlich, nahbar
- Farben: Beige `#F5F5DC`, Braun `#8B4513`, Warm-Grün `#6B8E23`
- Typografie: Klar, zugänglich, ohne Schnörkel
- Gefahr: Profillos, langweilig, keine Differenzierung
- Beispiele: IKEA, eBay, Levi's, Target, Ford
- Bild-Prompt: "Diverse people gathered around a shared table, warm earth tones, genuine and inclusive everyman brand archetype"

**THE CAREGIVER** — "Wir sind immer für dich da"
- Motivation: Fürsorge, Schutz, anderen helfen
- Tonalität: Empathisch, fürsorglich, geduldig, sanft
- Farben: Sanftes Grün `#90EE90`, Warm-Weiss `#FAF0E6`, Hellblau
- Typografie: Rund, einladend, zugänglich
- Gefahr: Aufopfernd, grenzenlos, can't say no
- Beispiele: Johnson & Johnson, UNICEF, Campbell's
- Bild-Prompt: "Hands gently cupping a small growing plant, soft green and warm white, nurturing caregiver brand archetype"

**THE RULER** — "Exzellenz ist kein Zufall — sie ist System"
- Motivation: Ordnung, Kontrolle, Wohlstand
- Tonalität: Autoritär, präzise, strukturiert, professionell
- Farben: Dunkelblau `#003366`, Schwarz `#000000`, Gold `#C9A84C`
- Typografie: Klassisch, Autorität, klare Hierarchie
- Gefahr: Starr, kontrollierend, kalt, elitär
- Beispiele: Mercedes-Benz, Rolex, Microsoft, American Express
- Bild-Prompt: "A golden crown above a structured skyline, dark blue and gold, authority and excellence ruler brand archetype"

**THE CREATOR** — "Erschaffe was noch nicht existiert"
- Motivation: Innovation, Ausdruck, Erschaffen von Neuem
- Tonalität: Originell, experimentell, visionär, mutig
- Farben: Unkonventionell — sehr bunt ODER bewusst minimalistisch
- Typografie: Experimentell, ausdrucksstark, einzigartig
- Gefahr: Unstrukturiert, chaotisch, selbstverliebt
- Beispiele: Lego, Adobe, Dyson, Minecraft, Crayola
- Bild-Prompt: "Hands sculpting something raw into form, creative tools surrounding, vibrant mixed colors, creator brand archetype"

---

## AUSWERTUNG & KONGRUENZ-ANALYSE

### Dual Method — Kongruenz-Check

Vergleiche Fascinate Primary mit Jung/Pearson Primary:
- Übereinstimmungen stärken die Empfehlung
- Abweichungen = wertvolle Spannung für die Beratung
- Freitext-Antworten (F16–F20) für Nuancierung einbeziehen

### Ergebnis-Präsentation (Dialog-Format)

```
🦉 Dein LUMEN¹ Brand Archetype Profil

[Bei Methode A/C]
Fascinate Advantage Profil:
Primary: [ADVANTAGE] ([Score]/16)
Secondary: [ADVANTAGE] ([Score]/16)
Dormant: [ADVANTAGE] ([Score]/16) ← bewusst nicht einsetzen
Archetyp aus 49-Matrix: [NAME]

[Bei Methode B/C]
Brand Archetyp:
Primary: [ARCHETYP] ([Punkte])
Shadow: [ARCHETYP] ([Punkte])

[Bei Dual Method]
Kongruenz-Check:
[Stimmen beide Methoden überein? Wenn ja: starkes Signal.
Wenn nicht: Was ist die Spannung und was bedeutet sie?]

Was das für deinen Brand bedeutet:
Kommunikation: [Konkret aus Bibliothek]
Visuelle Sprache: [Farben + Typografie-Richtung]
Tonalität: [3 Adjektive + Erklärung]
Nicht: [Aus Gefahr-Sektion]
```

---

## OUTPUTS ERSTELLEN

### Output 1: 02-brand-archetype.md

Lies Schema 02 aus `artefact-templates.md` Teil 1. Schreibe die Datei nach
`clients/[name]/outputs/02-brand-archetype.md` mit folgendem H2-Header:

```
## [Projektname] | [Datum]
## Methodische Basis: §2 (Pearson/Jung, Hogshead) | LUMEN³ by Owlist
```

**Pflicht-Sections (Reihenfolge wie in Schema 02):**

```
## Fascinate Advantage
Primary: [ADVANTAGE] (Score: [N]/16)
Secondary: [ADVANTAGE] (Score: [N]/16)
Dormant: [ADVANTAGE] (Score: [N]/16)
[Begründung: Welche 4 Aussagen pro Advantage den Score getrieben haben]

## Brand Archetype (Pearson/Jung)
Primary: [ARCHETYP] ([Punkte])
Shadow: [ARCHETYP] ([Punkte])
[Begründung: Welche a–l Antworten den Primary getragen haben]
[Vollständige Profil-Beschreibung aus der Archetyp-Bibliothek]

## Synthese
[Kongruenz-Analyse: Stimmen Fascinate-Primary und Pearson/Jung-Primary
überein? Wo liegen Spannungen? Einbezug der Freitext-Antworten F16–F20]

## Strategische Konsequenzen
- Kommunikation: [Konkret]
- Visuelle Sprache: [Farben mit Hex-Codes, Typografie-Richtung]
- Tonalität: [3 Adjektive + Erklärung]
- Kanäle: [Passende Medien]
- Vermeiden: [Aus Gefahr-Sektion]
- Gehirn-Diagramm Prompt: "A human brain diagram showing [PRIMARY]
  as dominant region, [SECONDARY] as supporting, [DORMANT] as minimal,
  brand archetype neuromarketing visualization"

## Nächster Schritt
Weiter mit /lumen-interview — Brand Interview (We Are / We Are Not)
```

**Pflicht-Felder (aus Schema 02):**
- In `Fascinate Advantage`: `Primary:`, `Secondary:`, `Dormant:`
- In `Brand Archetype (Pearson/Jung)`: `Primary:`, `Shadow:`

Sonst bricht Skill 06 beim Einlesen ab (siehe `artefact-templates.md` Teil 5).

### Output 2: matrix.html

Erstelle `clients/[name]/outputs/matrix.html`. Ersetze `[ARCHETYPE_NAME]`,
`[PRIMARY]`, `[SECONDARY]`, `[DORMANT]` mit den ermittelten Werten und
ändere das entsprechende `<td>` in der Tabelle auf `class="is-result"`.

```html
<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<title>LUMEN³ — Fascination Advantage Matrix</title>
<style>
  * { box-sizing: border-box; margin: 0; padding: 0; }
  body {
    font-family: 'Helvetica Neue', Arial, sans-serif;
    background: #0d0d0d;
    color: #fff;
    padding: 40px 20px;
  }
  .header { text-align: center; margin-bottom: 40px; }
  .header h1 {
    font-size: 13px; letter-spacing: 4px; text-transform: uppercase;
    color: #596A71; margin-bottom: 8px;
  }
  .header h2 { font-size: 28px; font-weight: 300; color: #fff; margin-bottom: 4px; }
  .header .subtitle { font-size: 13px; color: #888; letter-spacing: 2px; }
  .result-banner {
    background: linear-gradient(135deg, #596A71, #A55B1C);
    border-radius: 8px; padding: 20px 30px;
    margin: 0 auto 40px; max-width: 700px; text-align: center;
  }
  .result-banner .archetype-name {
    font-size: 32px; font-weight: 700; letter-spacing: 2px; margin-bottom: 8px;
  }
  .result-banner .advantages {
    font-size: 13px; letter-spacing: 3px; text-transform: uppercase; opacity: 0.85;
  }
  .matrix-wrapper { overflow-x: auto; margin: 0 auto; max-width: 1100px; }
  table { border-collapse: collapse; width: 100%; table-layout: fixed; }
  th {
    padding: 12px 6px; font-size: 10px; letter-spacing: 2px;
    text-transform: uppercase; color: #888; text-align: center;
    border: 1px solid #222;
  }
  th.row-header {
    text-align: right; padding-right: 12px; width: 110px; color: #888;
  }
  th.col-header { background: #111; }
  td {
    padding: 10px 6px; font-size: 10px; text-align: center;
    border: 1px solid #1a1a1a; color: #aaa; transition: all 0.2s;
    cursor: default; line-height: 1.4;
  }
  td:hover { background: #1e1e1e; color: #fff; }
  td.is-result {
    background: linear-gradient(135deg, #596A71, #A55B1C) !important;
    color: #fff !important; font-weight: 700; font-size: 11px;
    border: 2px solid #fff; border-radius: 4px;
  }
  td.is-double {
    background: #1a0000; color: #cc3333; border: 1px solid #330000;
  }
  td.is-double:hover { background: #2a0000; }
  .legend {
    display: flex; gap: 24px; justify-content: center;
    margin-top: 30px; flex-wrap: wrap;
  }
  .legend-item { display: flex; align-items: center; gap: 8px; font-size: 11px; color: #888; }
  .legend-dot { width: 14px; height: 14px; border-radius: 3px; }
  .dot-result { background: linear-gradient(135deg, #596A71, #A55B1C); }
  .dot-double { background: #1a0000; border: 1px solid #cc3333; }
  .dot-normal { background: #111; border: 1px solid #333; }
  .footer { text-align: center; margin-top: 40px; font-size: 11px; color: #444; letter-spacing: 2px; }
  .double-warning {
    max-width: 700px; margin: 30px auto 0;
    background: #1a0000; border: 1px solid #330000; border-radius: 6px;
    padding: 16px 20px; font-size: 11px; color: #cc3333; line-height: 1.6;
  }
  .double-warning strong { color: #ff4444; }
</style>
</head>
<body>

<div class="header">
  <h1>LUMEN³ Brand Framework · Owlist</h1>
  <h2>Fascination Advantage Matrix</h2>
  <div class="subtitle">49 Archetypen · Primary × Secondary Advantage</div>
</div>

<div class="result-banner">
  <div class="archetype-name">[ARCHETYPE_NAME]</div>
  <div class="advantages">Primary: [PRIMARY] · Secondary: [SECONDARY] · Dormant: [DORMANT]</div>
</div>

<div class="matrix-wrapper">
<table>
  <thead>
    <tr>
      <th class="row-header">Primary ↓ / Secondary →</th>
      <th class="col-header">Innovation</th>
      <th class="col-header">Passion</th>
      <th class="col-header">Power</th>
      <th class="col-header">Prestige</th>
      <th class="col-header">Trust</th>
      <th class="col-header">Mystique</th>
      <th class="col-header">Alert</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="row-header">Innovation</th>
      <td class="is-double">The Anarchy</td>
      <td>The Rockstar</td>
      <td>The Maverick Leader</td>
      <td>The Trendsetter</td>
      <td>The Artisan</td>
      <td>The Provocateur</td>
      <td>The Quick-Start</td>
    </tr>
    <tr>
      <th class="row-header">Passion</th>
      <td>The Catalyst</td>
      <td class="is-double">The Drama</td>
      <td>The People's Champion</td>
      <td>The Talent</td>
      <td>The Beloved</td>
      <td>The Intrigue</td>
      <td>The Orchestrator</td>
    </tr>
    <tr>
      <th class="row-header">Power</th>
      <td>The Change Agent</td>
      <td>The Ringleader</td>
      <td class="is-double">The Aggressor</td>
      <td>The Maestro</td>
      <td>The Guardian</td>
      <td>The Mastermind</td>
      <td>The Defender</td>
    </tr>
    <tr>
      <th class="row-header">Prestige</th>
      <td>The Avant-Garde</td>
      <td>The Connoisseur</td>
      <td>The Victor</td>
      <td class="is-double">The Imperial</td>
      <td>The Blue Chip</td>
      <td>The Architect</td>
      <td>The Scholar</td>
    </tr>
    <tr>
      <th class="row-header">Trust</th>
      <td>The Evolutionary</td>
      <td>The Authentic</td>
      <td>The Gravitas</td>
      <td>The Diplomat</td>
      <td class="is-double">The Old Guard</td>
      <td>The Anchor</td>
      <td>The Good Citizen</td>
    </tr>
    <tr>
      <th class="row-header">Mystique</th>
      <td>The Secret Weapon</td>
      <td>The Subtle Touch</td>
      <td>The Veiled Strength</td>
      <td>The Royal Guard</td>
      <td>The Wise Owl</td>
      <td class="is-double">The Deadbolt</td>
      <td>The Archer</td>
    </tr>
    <tr>
      <th class="row-header">Alert</th>
      <td>The Composer</td>
      <td>The Coordinator</td>
      <td>The Ace</td>
      <td>The Editor-in-Chief</td>
      <td>The Mediator</td>
      <td>The Detective</td>
      <td class="is-double">The Control Freak</td>
    </tr>
  </tbody>
</table>
</div>

<div class="legend">
  <div class="legend-item"><div class="legend-dot dot-result"></div><span>Dein Archetyp</span></div>
  <div class="legend-item"><div class="legend-dot dot-double"></div><span>Double Advantage (Achtung: Überdosis)</span></div>
  <div class="legend-item"><div class="legend-dot dot-normal"></div><span>Alle anderen Archetypen</span></div>
</div>

<div class="double-warning">
  <strong>Hinweis zu den 7 Double Advantages (Diagonale):</strong>
  The Anarchy · The Drama · The Aggressor · The Imperial · The Old Guard · The Deadbolt · The Control Freak —
  Diese Archetypen entstehen wenn Primary und Secondary identisch sind.
  Sie zeigen eine Überdosis eines einzigen Advantage und tragen überwiegend
  negative Konnotationen. In der Beratung: Bewusst vermeiden oder sehr gezielt einsetzen.
</div>

<div class="footer">LUMEN³ Brand Framework · by Owlist · www.owlist.ch</div>

</body>
</html>
```

### Output 3: slides-outline.md

Schema 02 hat in `artefact-templates.md` Teil 2 kein definiertes Slide-Set —
die Slides dieses Skills sind skill-spezifisch. Erstelle
`clients/[name]/outputs/slides-outline.md` mit folgender Struktur.
Owlist Brand-Tokens (Farben, Fonts) aus `artefact-templates.md` Teil 4
verwenden, keine eigenen Tokens definieren.

```markdown
# LUMEN³ — Brand Archetype Präsentation
## [Projektname] | [Datum]
## Methodische Basis: §2 | LUMEN³ by Owlist

## SLIDE 1 — Cover
Titel: "Brand Archetype Report"
Untertitel: [Projektname]
Datum: [Datum]

## SLIDE 2 — Dein Archetyp
Headline: "[ARCHETYPE_NAME]"
Subline: "[Kernversprechen aus Bibliothek]"
Body: [3–4 Sätze Archetyp-Beschreibung]
Visual-Prompt: [Bild-Prompt aus Bibliothek]

## SLIDE 3 — Fascination Advantage Profil  [Nur bei Methode A/C]
Headline: "Wie du die Welt faszinierst"
Balkendiagramm der 7 Advantages mit Scores
Primary: [ADVANTAGE] — [Score]/16
Secondary: [ADVANTAGE] — [Score]/16
Dormant: [ADVANTAGE] — [Score]/16 (grau, kleiner)

## SLIDE 4 — Die 49 Matrix
Headline: "Deine Position in der Fascination Matrix"
Visual: matrix.html (Screenshot oder einbetten)
Highlight: [ARCHETYPE_NAME]

## SLIDE 5 — Gehirn-Diagramm
Headline: "Aktive Faszinations-Zonen"
Visual-Prompt: siehe Output 1 / Strategische Konsequenzen

## SLIDE 6 — Brand Archetyp Profil  [Nur bei Methode B/C]
Headline: "Wer deine Marke ist"
Primary: [ARCHETYP]
Shadow: [ARCHETYP]
Quadrant: [Pearson/Jung-Quadrant]

## SLIDE 7 — Kongruenz-Check  [Nur bei Dual Method]
Headline: "Selbstbild vs. Wirkung"
Links: "Wie du dich siehst" — [aus F16]
Rechts: "Wie du wirkst" — [Fascinate-Ergebnis]
Empfehlung: [Handlungsempfehlung aus Synthese]

## SLIDE 8 — Tonalität & Kommunikation
Headline: "Die Stimme deiner Marke"
3 Kern-Adjektive — Was wir sagen — Was wir nie sagen

## SLIDE 9 — Visual Identity Richtung
Headline: "Visuelle Sprache"
Farbpalette (Hex aus Bibliothek) — Typografie-Richtung — Bildsprache

## SLIDE 10 — Nächste Schritte
Weiter mit /lumen-interview — Brand Interview (We Are / We Are Not)
```

---

## ABSCHLUSS-MELDUNG

```
LUMEN¹ Brand Archetype Assessment abgeschlossen.

Fascinate: Primary=[X] | Secondary=[Y] | Dormant=[Z]
Archetyp:  Primary=[X] | Shadow=[Y]

Outputs:
02-brand-archetype.md — Schema 02 mit Primary/Secondary/Dormant/Shadow
matrix.html           — Interaktive 49-Archetypen-Matrix
slides-outline.md     — 10 Slides für Präsentation

Weiter mit: /lumen-interview — Brand Interview (We Are / We Are Not)
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

- Keine eigene wissenschaftliche Erklärung der Methodik
  (kommt aus `methodology.md` §2, falls der Nutzer fragt)
- Keine eigenen Brand-Tokens (Farben, Fonts) — die Owlist-Tokens für
  Präsentation und Matrix kommen aus `artefact-templates.md` Teil 4
- Keine Interpretation der Freitext-Antworten F16–F20 im Scoring
  (sie fliessen nur in die qualitative Synthese)
- Keine Miro-Integration — Schema 02 hat kein Miro-Frame in
  `artefact-templates.md` Teil 3
- Kein Trigger-Scoring (das macht Skill 04 auf Basis dieses Outputs)
- Keine Wiederholung der 49-Matrix-Definition in `methodology.md` —
  die Matrix ist operatives Asset dieses Skills
- Schreibt niemals Memory-Inhalte in Kunden-Outputs (Markdown, Slides, Miro, PDF)
