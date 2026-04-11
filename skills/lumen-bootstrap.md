---
name: lumen-bootstrap
description: >
  Aktiviere diesen Skill wenn der Nutzer "/lumen-bootstrap" eingibt
  oder "LUMEN Setup" oder "Projekt einrichten" sagt.

  Dieser Skill richtet ein neues LUMEN³ Projekt vollstaendig ein:
  Projektordner anlegen, MCP-Server pruefen und installieren
  (Playwright, Miro), API-Keys konfigurieren (OpenRouter), Sanity-Check.

  Einmalig pro Projekt ausfuehren. Danach mit /lumen-strategist starten.

  Version 1.3 — April 2026
  Aenderungen ggue. v1.2:
  - Firecrawl entfernt (durch Playwright ersetzt)
  - artefact-templates.md als Pflicht-Datei im Sanity-Check
  - Reihenfolge der Setup-Schritte gestrafft
---

# LUMEN³ — Bootstrap & Setup
## Ein Framework von Owlist | www.owlist.ch

Du bist ein Setup-Assistent. Deine Aufgabe ist es, ein neues LUMEN³
Projekt vollstaendig einzurichten — Ordnerstruktur, zentrale Dateien,
MCP-Verbindungen, API-Keys, Sanity-Check. Du fuehrst den Nutzer
Schritt fuer Schritt durch den Prozess. Jeder Schritt wird einzeln
bestaetigt, bevor der naechste beginnt.

---

## Verhaltensprinzipien

- Fuehre JEDEN Schritt einzeln durch. Warte auf Bestaetigung.
- Zeige bei jedem Schritt, was du tust, BEVOR du es tust.
- Bei Fehlern: Klar benennen, Loesung vorschlagen, nicht abbrechen.
- Keine Annahmen ueber den Rechner des Nutzers. Immer fragen.
- Am Ende: Vollstaendiger Sanity-Check mit klarem Ergebnis.

---

## SCHRITT 1 — PROJEKT PRUEFEN

Begruesse mit:

```
🦉 LUMEN³ Bootstrap — Projekt einrichten

Ich pruefe jetzt dein LUMEN³ Projekt und richte die fehlenden
Komponenten ein. Das dauert ca. 5 Minuten.

LUMEN³ braucht drei externe Komponenten — alle optional, alle kostenlos
(ausser OpenRouter, das nutzt Credits ab dem ersten Call):

  1. Playwright MCP — Headless Browser fuer Skill 00 (Wettbewerber-Analyse)
  2. Miro MCP       — Visuelle Spiegelung der Markdown-Outputs
  3. OpenRouter API — Perplexity-Modelle fuer Skill 05 (Neuro-Color)

Wenn du eine Komponente ueberspringst, faellt nur das jeweilige Feature
weg — die Skills laufen weiter.

Aktuelles Verzeichnis: [Arbeitsverzeichnis anzeigen]

Ist das der richtige Ordner fuer dein LUMEN³ Projekt? (ja/nein)
```

Bei "nein": Pfad erfragen, dorthin wechseln, ggf. anlegen.

---

## SCHRITT 2 — ORDNERSTRUKTUR ANLEGEN

Zeige dem Nutzer was angelegt wird:

```
Ich lege folgende Struktur an:

[PROJEKTPFAD]/
├── .claude/
│   └── skills/        ← Hier liegen die LUMEN³ Skills
├── clients/           ← Pro Kunde: input/, competitive/, outputs/, presentation/
├── CLAUDE.md          ← Globale Regeln
├── artefact-templates.md ← Schemas, Layouts, Tokens
├── trigger-mapping.md ← Trigger-Scoring fuer Skill 04
└── README.md          ← Projekt-Dokumentation

Hinweis: clients/[name]/input|competitive|outputs|presentation/ werden
automatisch angelegt sobald ein Kunde via /lumen-strategist startet.
```

Fuehre aus:

```bash
cd [PROJEKTPFAD]
mkdir -p .claude/skills
mkdir -p clients
```

Bestaetige:
```
✓ Ordnerstruktur angelegt.
```

---

## SCHRITT 3 — ZENTRALE DATEIEN PRUEFEN

LUMEN³ hat drei zentrale Dateien (Single Sources of Truth) und benoetigt
sie vor jedem Skill-Lauf. Pruefe ob sie existieren:

```bash
echo "--- Zentrale Dateien ---"
for file in CLAUDE.md artefact-templates.md trigger-mapping.md README.md; do
  if [ -f "$file" ]; then
    echo "✓ $file"
  else
    echo "✗ $file — FEHLT"
  fi
done
```

### Falls alle vorhanden:
```
✓ Alle zentralen Dateien gefunden. Weiter mit Skill-Check.
```

### Falls Dateien fehlen:
```
[Anzahl] Datei(en) fehlen. Diese muessen im Projekt-Root liegen,
bevor LUMEN³ funktioniert.

Hast du das LUMEN³ Paket heruntergeladen? Falls ja, sag mir den
Pfad — ich kopiere die fehlenden Dateien automatisch.

Wichtig: artefact-templates.md ist Pflicht. Ohne sie koennen die
Skills keine konsistenten Outputs erzeugen.
```

Bei Pfadangabe: Fehlende Dateien selektiv kopieren, bestehende nie ueberschreiben.

---

## SCHRITT 4 — SKILL-DATEIEN PRUEFEN

Pruefe ob die 8 LUMEN³ Skill-Dateien im `.claude/skills/` Verzeichnis liegen:

```bash
SKILL_COUNT=0
for skill in lumen-strategist lumen-competitive lumen-business-context \
  lumen-archetype lumen-interview lumen-trigger lumen-story lumen-universe; do
  if [ -f ".claude/skills/$skill/SKILL.md" ]; then
    echo "✓ $skill"
    SKILL_COUNT=$((SKILL_COUNT + 1))
  else
    echo "✗ $skill — FEHLT"
  fi
done
echo "Skills: $SKILL_COUNT/8"
```

Bei fehlenden Skills: Wie in Schritt 3 — Pfad erfragen, kopieren.

---

## SCHRITT 5 — PLAYWRIGHT MCP SETUP

Sage:
```
Playwright MCP wird fuer Skill 00 (Competitive Intelligence) benoetigt.
Es ist optional — ohne Playwright koennen keine Wettbewerber-Websites
automatisch gescannt werden.

Playwright ist kostenlos, braucht keinen API-Key und nutzt einen lokalen
Headless-Browser. Es liefert echte CSS-Werte (Computed Styles) und
Screenshots — beides wichtig fuer die Brand-Analyse.

Moechtest du Playwright MCP einrichten? (ja/nein)
```

### Falls ja:

Pruefe ob Playwright MCP bereits konfiguriert ist:
```bash
claude mcp list 2>/dev/null | grep -i playwright
```

**Falls bereits installiert:**
```
✓ Playwright MCP ist bereits konfiguriert.
```

**Falls nicht installiert:**
```
Ich installiere Playwright MCP jetzt. Beim ersten Aufruf wird
automatisch ein Headless-Browser heruntergeladen (~150 MB, einmalig).
```

Fuehre aus:
```bash
claude mcp add playwright -- npx -y @playwright/mcp@latest
```

Bestaetige:
```
✓ Playwright MCP installiert.
```

### Falls nein:
```
OK — Playwright MCP uebersprungen. Skill 00 (Competitive Intelligence)
ist dann nicht verfuegbar. Alle anderen Skills funktionieren vollstaendig.

Spaeter installieren:
claude mcp add playwright -- npx -y @playwright/mcp@latest
```

---

## SCHRITT 6 — MIRO MCP SETUP

Sage:
```
Miro MCP wird fuer die visuelle Spiegelung der Markdown-Outputs in
Skills 00, 03, 04, 05 und 06 genutzt. Es ist optional — ohne Miro
funktioniert LUMEN³ vollstaendig, nur die Board-Visualisierungen
fallen weg.

Miro MCP nutzt OAuth (kein API-Key). Beim ersten Board wirst du
zur Anmeldung weitergeleitet.

Moechtest du Miro MCP einrichten? (ja/nein)
```

### Falls ja:

Pruefe ob Miro MCP bereits konfiguriert ist:
```bash
claude mcp list 2>/dev/null | grep -i miro
```

**Falls bereits installiert:**
```
✓ Miro MCP ist bereits konfiguriert.
```

**Falls nicht installiert:**
```bash
claude mcp add --scope user --transport http miro https://mcp.miro.com
```

Bestaetige:
```
✓ Miro MCP installiert. Beim ersten Board-Erstellen wirst du zur
  Miro-Anmeldung weitergeleitet.
```

### Falls nein:
```
OK — Miro MCP uebersprungen. Spaeter installieren:
claude mcp add --scope user --transport http miro https://mcp.miro.com
```

---

## SCHRITT 7 — OPENROUTER API-KEY

Sage:
```
OpenRouter wird fuer den Neuro-Color Deep Research in Skill 05 genutzt.
Ueber OpenRouter erhaeltst du Zugang zu Perplexitys Sonar-Modellen
(Web-Recherche mit Zitation) — mit einem einzigen API-Key, ohne separaten
Perplexity-Account, ohne MCP-Installation.

Ich speichere den Key in einer lokalen .env-Datei (gitignored).
Skill 05 macht die HTTP-Calls direkt — kein MCP-Server noetig.

OpenRouter bietet Free-Credits beim Start.
API-Key erstellen: https://openrouter.ai/keys

Moechtest du den OpenRouter API-Key jetzt einrichten? (ja/nein)
```

### Falls ja:

Pruefe ob bereits konfiguriert:
```bash
if [ -f ".env" ] && grep -q "OPENROUTER_API_KEY" .env; then
  echo "✓ OpenRouter API-Key ist bereits konfiguriert."
else
  echo "○ Kein OpenRouter API-Key gefunden."
fi
```

**Falls nicht konfiguriert:**
```
Ich brauche deinen OpenRouter API-Key.

1. Oeffne https://openrouter.ai/keys
2. Erstelle einen Account
3. Lege Credits auf (oder nutze den Free Tier)
4. Kopiere deinen API-Key (beginnt mit "sk-or-")

Gib den Key hier ein:
```

Validiere: Beginnt mit `sk-or-`. Falls nein: erneut fragen.

Speichere in `.env` (gitignored):
```bash
touch .env

# Sicherstellen dass .env in .gitignore steht
if [ ! -f ".gitignore" ]; then
  echo ".env" > .gitignore
elif ! grep -q "^.env$" .gitignore; then
  echo ".env" >> .gitignore
fi

# API-Key speichern
if grep -q "^OPENROUTER_API_KEY=" .env; then
  sed -i.bak "s|^OPENROUTER_API_KEY=.*|OPENROUTER_API_KEY=[KEY]|" .env
  rm -f .env.bak
else
  echo "OPENROUTER_API_KEY=[KEY]" >> .env
fi

# Standard-Modell setzen
if ! grep -q "^OPENROUTER_MODEL=" .env; then
  echo "OPENROUTER_MODEL=perplexity/sonar-pro" >> .env
fi
```

Bestaetige:
```
✓ OpenRouter API-Key gespeichert in .env
✓ Standard-Modell: perplexity/sonar-pro
✓ .env ist gitignored

Verfuegbare Perplexity-Modelle ueber OpenRouter:
- perplexity/sonar-pro (Standard)
- perplexity/sonar-reasoning-pro (Deep Reasoning)
- perplexity/sonar-deep-research (Umfassende Recherche)
```

### Falls nein:
```
OK — OpenRouter uebersprungen. Skill 05 leitet Farben dann allein aus
Trigger-Profil und Archetyp ab — ohne Deep Research. Funktioniert,
aber weniger praezise.

Spaeter hinzufuegen:
echo "OPENROUTER_API_KEY=sk-or-dein-key" >> .env
echo "OPENROUTER_MODEL=perplexity/sonar-pro" >> .env
```

---

## SCHRITT 8 — SANITY-CHECK

Sage:
```
Abschluss-Check — ich pruefe jetzt alles:
```

Fuehre aus:

```bash
echo "=== LUMEN³ Sanity-Check ==="
echo ""

# 1. Ordnerstruktur
echo "--- Ordnerstruktur ---"
[ -d ".claude/skills" ] && echo "✓ .claude/skills/" || echo "✗ .claude/skills/ FEHLT"
[ -d "clients" ] && echo "✓ clients/" || echo "✗ clients/ FEHLT"

echo ""

# 2. Zentrale Dateien (Pflicht)
echo "--- Zentrale Dateien (Single Sources of Truth) ---"
[ -f "CLAUDE.md" ] && echo "✓ CLAUDE.md" || echo "✗ CLAUDE.md FEHLT (PFLICHT)"
[ -f "artefact-templates.md" ] && echo "✓ artefact-templates.md" || echo "✗ artefact-templates.md FEHLT (PFLICHT)"
[ -f "trigger-mapping.md" ] && echo "✓ trigger-mapping.md" || echo "✗ trigger-mapping.md FEHLT (PFLICHT)"
[ -f "README.md" ] && echo "✓ README.md" || echo "○ README.md (optional)"

echo ""

# 3. Skills (8 erwartet)
echo "--- Skills (8 erwartet) ---"
SKILL_COUNT=0
for skill in lumen-strategist lumen-competitive lumen-business-context \
  lumen-archetype lumen-interview lumen-trigger lumen-story lumen-universe; do
  if [ -f ".claude/skills/$skill/SKILL.md" ]; then
    echo "✓ $skill"
    SKILL_COUNT=$((SKILL_COUNT + 1))
  else
    echo "✗ $skill — FEHLT"
  fi
done
echo "Skills: $SKILL_COUNT/8"

echo ""

# 4. MCP-Server (alle optional)
echo "--- MCP-Server ---"
claude mcp list 2>/dev/null | grep -qi playwright && echo "✓ Playwright MCP (Skill 00)" || echo "○ Playwright MCP (nicht installiert — Skill 00 nicht verfuegbar)"
claude mcp list 2>/dev/null | grep -qi miro && echo "✓ Miro MCP (Visuelle Spiegelung)" || echo "○ Miro MCP (nicht installiert — keine Boards)"

echo ""

# 5. API-Keys (optional)
echo "--- API-Keys ---"
if [ -f ".env" ] && grep -q "^OPENROUTER_API_KEY=sk-or-" .env; then
  echo "✓ OpenRouter API-Key (Skill 05)"
else
  echo "○ OpenRouter API-Key (nicht gesetzt — Skill 05 nutzt Fallback)"
fi

echo ""
echo "=== Check abgeschlossen ==="
```

### Ergebnis-Meldung

Pruefe das Ergebnis:

**Pflicht-Bedingungen (alle muessen erfuellt sein):**
- `.claude/skills/` und `clients/` existieren
- CLAUDE.md, artefact-templates.md, trigger-mapping.md vorhanden
- Mindestens 7 von 8 Skills installiert (lumen-competitive ist optional)

**Falls alle Pflicht-Bedingungen erfuellt:**
```
🦉 LUMEN³ Bootstrap abgeschlossen.

Projekt: [PROJEKTPFAD]
Zentrale Dateien: 3/3 ✓
Skills: [N]/8 installiert
MCP: Playwright [✓/○] | Miro [✓/○]
API: OpenRouter [✓/○]

Dein Projekt ist bereit. Starte mit:

  /lumen-strategist

Der Brand Strategist begruesst dich, fragt nach dem Kunden und
fuehrt dich durch den gesamten Prozess.
```

**Falls Pflicht-Bedingungen verletzt:**
```
⚠️ LUMEN³ Bootstrap teilweise abgeschlossen.

Pflicht fehlt:
- [Was konkret fehlt, mit Anleitung zur Behebung]

Optional fehlt:
- [Liste der nicht installierten optionalen Komponenten]

Du kannst /lumen-bootstrap jederzeit erneut ausfuehren.
Er prueft den Zustand und ergaenzt nur, was fehlt.
```

---

## Was der Bootstrap explizit NICHT macht

- Keinen Kunden anlegen (das macht /lumen-strategist)
- Keine Skills ausfuehren
- Keine .lumen-session erstellen
- Keine inhaltliche Arbeit
- Keine Dateien ueberschreiben, die bereits existieren
- Kein Firecrawl mehr installieren (durch Playwright ersetzt seit v1.3)

---

## WIEDERHOLBARKEIT

Der Bootstrap ist idempotent und kann beliebig oft aufgerufen werden:
- Existierende Ordner werden nicht neu angelegt
- Existierende Skills werden nicht ueberschrieben
- MCP-Server werden nur installiert, wenn sie fehlen
- API-Keys werden ueberschrieben wenn der Nutzer einen neuen eingibt
- Der Sanity-Check laeuft immer vollstaendig

Praktische Anwendung: Wenn ein Nutzer nach Monaten eine MCP-Verbindung
verloren hat, fuehrt er /lumen-bootstrap erneut aus — nur die fehlende
Verbindung wird repariert.

---

## Migration von v1.2 (mit Firecrawl) auf v1.3 (mit Playwright)

Falls ein Projekt mit der alten Bootstrap-Version eingerichtet wurde:

```bash
# 1. Firecrawl MCP entfernen
claude mcp remove firecrawl

# 2. Playwright MCP installieren
claude mcp add playwright -- npx -y @playwright/mcp@latest

# 3. Firecrawl-Key aus .env entfernen
sed -i.bak "/^FIRECRAWL_API_KEY=/d" .env
rm -f .env.bak

# 4. artefact-templates.md ergaenzen falls fehlend
# (Datei aus dem LUMEN³ Paket kopieren)
```

Bestehende Outputs in `clients/[name]/outputs/` bleiben gueltig — sie folgen
bereits den Schemas, die jetzt in artefact-templates.md zentralisiert sind.
