---
title: "LUMEN³ Setup-Anleitung"
subtitle: "Von GitHub-Clone bis zum ersten Skill-Durchlauf — für komplette Einsteiger"
author: "Tobias Schmidt · Owlist GmbH"
date: "April 2026"
---

# LUMEN³ Setup-Anleitung
## Von GitHub-Clone bis zum ersten Skill-Durchlauf

**Für komplette Einsteiger:** Diese Anleitung nimmt dich an die Hand — Schritt für Schritt. Du brauchst keine Vorkenntnisse in Claude Code, Terminal oder Git. Plane 30–45 Minuten für das komplette Setup ein.

**Voraussetzungen:**

- Ein Mac (macOS 12 oder neuer) oder Windows-PC (Windows 10/11)
- Eine Internet-Verbindung
- Ein GitHub-Account (kostenlos, in 2 Minuten erstellt)
- Ein Claude-Account bei Anthropic (kostenlos, Pro-Abo für volle Leistung empfohlen)

\newpage

# Inhalt

1. Überblick: Was machen wir?
2. Schritt 1 — Claude Code installieren
3. Schritt 2 — GitHub-Account und Zugriff einrichten
4. Schritt 3 — Das LUMEN³-Repository klonen
5. Schritt 4 — Terminal öffnen und in das Verzeichnis wechseln
6. Schritt 5 — Claude Code starten
7. Schritt 6 — Die MCP-Server installieren (Playwright, Miro)
8. Schritt 7 — Optional: OpenRouter API-Key für Skill 05
9. Schritt 8 — Erster Durchlauf: `/lumen-strategist`
10. Troubleshooting: Die häufigsten Probleme
11. Was tun, wenn etwas nicht funktioniert?

\newpage

# 1. Überblick: Was machen wir?

Am Ende dieser Anleitung hast du:

- **Claude Code** auf deinem Computer installiert
- **Das LUMEN³-Framework** aus GitHub heruntergeladen
- **Drei optionale MCP-Server** (Playwright, Miro, OpenRouter) eingerichtet
- **Einen ersten Skill-Durchlauf** mit `/lumen-strategist` gestartet

Wenn du schon Claude Code installiert hast, kannst du Schritt 1 überspringen. Wenn du schon mit GitHub arbeitest, kannst du Schritt 2 überspringen. Wenn du unsicher bist, mach alle Schritte von oben bis unten durch.

**Wichtig:** LUMEN³ ist kein eigenständiges Programm, das du mit einem Doppelklick startest. Es ist eine **Sammlung von Skill-Dateien**, die Claude Code lädt und ausführt. Du startest also immer Claude Code im LUMEN³-Verzeichnis — und Claude Code kennt dann die Skills.

\newpage

# 2. Schritt 1 — Claude Code installieren

**Claude Code** ist das Kommandozeilen-Tool von Anthropic, mit dem du mit Claude interagierst. Es gibt drei Versionen:

- **CLI** (Terminal) — die offizielle Variante, läuft auf macOS, Linux, Windows
- **Desktop-App** (Mac & Windows) — grafische Oberfläche
- **Web-App** (claude.ai/code) — browserbasiert
- **IDE-Extensions** (VS Code, JetBrains) — integriert in Entwickler-Tools

Für LUMEN³ empfehlen wir die **Desktop-App für Mac oder Windows**, weil sie den einfachsten Einstieg bietet.

## 2.1 — Installation auf dem Mac

1. Öffne deinen Browser und gehe zu **https://claude.com/code**
2. Klicke auf „Download for Mac" (Du landest im Download-Bereich)
3. Die Datei `Claude-Code.dmg` wird in deinen Download-Ordner geladen
4. Öffne die heruntergeladene Datei mit einem Doppelklick
5. Ziehe das **Claude-Code-Symbol** in den **Programme-Ordner**
6. Öffne Claude Code aus dem Programme-Ordner (oder über Spotlight: ⌘ + Leertaste, dann „Claude Code" tippen)
7. Beim ersten Start musst du dich mit deinem Anthropic-Account anmelden (dasselbe Konto wie bei claude.ai)

**Erster Hinweis:** Wenn macOS sagt „Claude Code kann nicht geöffnet werden, weil es von einem unbekannten Entwickler stammt", gehe in die **Systemeinstellungen → Datenschutz & Sicherheit** und klicke dort auf „Trotzdem öffnen". Anthropic ist ein vertrauenswürdiger Entwickler — das Warnfenster ist eine Standard-Sicherheitsmaßnahme von Apple.

## 2.2 — Installation auf Windows

1. Öffne deinen Browser und gehe zu **https://claude.com/code**
2. Klicke auf „Download for Windows"
3. Die Datei `Claude-Code-Setup.exe` wird heruntergeladen
4. Öffne die Datei mit einem Doppelklick
5. Folge dem Installations-Assistenten: „Weiter" → „Ich stimme zu" → „Installieren"
6. Nach der Installation startet Claude Code automatisch
7. Melde dich mit deinem Anthropic-Account an

**Windows-Hinweis:** Wenn Windows Defender eine Warnung zeigt, klicke auf „Weitere Informationen" → „Trotzdem ausführen".

## 2.3 — Erste Anmeldung

Nach dem Start siehst du einen leeren Claude-Code-Eingabebereich. Hier kannst du später deine Fragen eintippen oder Skill-Befehle starten. Oben rechts siehst du dein Profilbild (wenn du angemeldet bist).

**Teste die Installation:** Tippe einen einfachen Befehl ein, z. B. „Zeig mir dein Datum". Wenn Claude antwortet, funktioniert die Installation.

\newpage

# 3. Schritt 2 — GitHub-Account und Zugriff einrichten

## 3.1 — GitHub-Account erstellen (nur falls du noch keinen hast)

1. Gehe zu **https://github.com**
2. Klicke oben rechts auf „Sign up"
3. Gib deine E-Mail-Adresse ein
4. Wähle ein Passwort
5. Wähle einen Benutzernamen
6. Bestätige die E-Mail, die GitHub dir schickt

Das kostet nichts und dauert 2 Minuten. GitHub ist eine Plattform für Code-Projekte — LUMEN³ wird dort als Open-Source-Framework gepflegt (oder als privates Repo, falls dein LUMEN³-Zugang begrenzt ist).

## 3.2 — Zugang zum LUMEN³-Repository

Es gibt zwei mögliche Fälle:

**Fall A: LUMEN³ ist öffentlich.** Dann kannst du es direkt klonen, ohne weitere Zugriffsrechte.

**Fall B: LUMEN³ ist privat.** Dann brauchst du eine Einladung vom Repository-Besitzer (Owlist). Du bekommst eine E-Mail mit einem Einladungs-Link. Klicke darauf und akzeptiere die Einladung. Danach hast du Lese-Zugriff auf das Repository.

## 3.3 — Git installieren (falls nicht vorhanden)

„Git" ist das Kommandozeilen-Tool, das Code von GitHub auf deinen Computer herunterlädt. Auf modernen Macs ist es meistens bereits installiert. Auf Windows musst du es separat installieren.

**Mac — Prüfen, ob Git installiert ist:**

1. Öffne das **Terminal** (in den Dienstprogrammen oder über Spotlight: ⌘ + Leertaste → „Terminal")
2. Tippe: `git --version` und drücke Enter
3. Wenn eine Versionsnummer angezeigt wird (z. B. `git version 2.43.0`), ist Git installiert
4. Wenn nicht, erscheint ein Dialog „Command Line Developer Tools werden benötigt". Klicke auf „Installieren" — das dauert 5–10 Minuten.

**Windows — Git installieren:**

1. Gehe zu **https://git-scm.com/download/win**
2. Der Download beginnt automatisch
3. Öffne die heruntergeladene Datei und folge dem Installer
4. Standardeinstellungen sind okay — einfach immer „Next" klicken
5. Nach der Installation: Öffne die **Eingabeaufforderung** (cmd) oder **PowerShell** und tippe `git --version`

\newpage

# 4. Schritt 3 — Das LUMEN³-Repository klonen

„Klonen" heißt: Eine komplette Kopie des Repositorys von GitHub auf deinen Computer herunterladen. Du machst das ein einziges Mal. Danach hast du alle LUMEN³-Dateien lokal.

## 4.1 — Entscheide, wo du das Repository speichern willst

**Empfehlung:** Lege einen Ordner `~/Projekte/` oder `~/Documents/GitHub/` an und klone das Repository dort hinein. Der Pfad sollte keine Leerzeichen und keine Umlaute enthalten.

Für diese Anleitung gehen wir davon aus, dass du es in `~/Documents/GitHub/` klonst.

## 4.2 — Den Klon-Befehl ausführen

**Mac:**

1. Öffne das **Terminal** (⌘ + Leertaste → „Terminal")
2. Tippe folgende Befehle nacheinander, jeweils mit Enter bestätigen:

```bash
mkdir -p ~/Documents/GitHub
cd ~/Documents/GitHub
git clone https://github.com/vibercoder79/LUMEN3.git
```

Der letzte Befehl lädt alle Dateien herunter. Das dauert 10–60 Sekunden je nach Internet-Geschwindigkeit.

**Windows:**

1. Öffne die **Eingabeaufforderung** (Windows-Taste → „cmd" → Enter)
2. Tippe:

```cmd
cd %USERPROFILE%\Documents
mkdir GitHub
cd GitHub
git clone https://github.com/vibercoder79/LUMEN3.git
```

**Hinweis:** Die genaue Repository-URL (`https://github.com/vibercoder79/LUMEN3.git`) hängt davon ab, wo LUMEN³ gehostet ist. Frage deinen Ansprechpartner bei Owlist, falls die URL nicht stimmt.

## 4.3 — Was wurde heruntergeladen?

Nach dem Klonen hast du einen neuen Ordner `lumen3` in `~/Documents/GitHub/`. Darin findest du:

```
lumen3/
├── CLAUDE.md                 ← globale Regeln
├── artefact-templates.md     ← Schemas und Layouts
├── methodology.md            ← wissenschaftliche Quellen
├── trigger-mapping.md        ← Scoring-Regeln
├── README.md                 ← Einführung
└── .claude/
    └── skills/               ← die 9 LUMEN³-Skills
        ├── lumen-strategist/
        ├── 00-competitive-analysis/
        ├── 01-business-context/
        ├── 02-brand-archetype/
        ├── 03-brand-interview/
        ├── 04-trigger-analysis/
        ├── 05-story-identity/
        ├── 06-brand-universe/
        └── lumen-learn/
```

Das ist dein LUMEN³-Arbeitsverzeichnis. Alle Skills liegen unter `.claude/skills/`.

\newpage

# 5. Schritt 4 — Terminal öffnen und in das Verzeichnis wechseln

Das Terminal (oder „Eingabeaufforderung" auf Windows) ist das zentrale Werkzeug, mit dem du Claude Code startest. Wenn du noch nie mit dem Terminal gearbeitet hast — keine Sorge. Du brauchst nur drei Befehle.

## 5.1 — Terminal öffnen

**Mac:**

- Drücke ⌘ + Leertaste
- Tippe „Terminal"
- Drücke Enter

Ein schwarzes oder weißes Fenster öffnet sich mit einer Eingabezeile. Du bist jetzt im Terminal.

**Windows:**

- Drücke die Windows-Taste
- Tippe „cmd" oder „PowerShell"
- Drücke Enter

## 5.2 — In das LUMEN³-Verzeichnis wechseln

Im Terminal gibst du ein:

**Mac:**

```bash
cd ~/Documents/GitHub/lumen3
```

**Windows:**

```cmd
cd %USERPROFILE%\Documents\GitHub\lumen3
```

Drücke Enter. Du bist jetzt im LUMEN³-Verzeichnis. Das erkennst du daran, dass die Eingabezeile sich ändert — sie zeigt jetzt den neuen Pfad an, z. B.:

```
~/Documents/GitHub/lumen3 $
```

## 5.3 — Verifizieren, dass du richtig bist

Tippe:

```bash
ls
```

(auf Windows: `dir`)

Du solltest eine Liste mit den LUMEN³-Dateien sehen — mindestens `CLAUDE.md`, `artefact-templates.md`, `methodology.md`, `trigger-mapping.md`, `README.md` und einen versteckten Ordner `.claude`.

Wenn du **nur deinen Home-Ordner** oder etwas anderes siehst, hast du einen falschen `cd`-Befehl eingegeben. Versuche es nochmal mit dem genauen Pfad.

\newpage

# 6. Schritt 5 — Claude Code starten

Jetzt kommt der entscheidende Schritt: Du startest Claude Code **genau in diesem Verzeichnis**. Das ist wichtig — Claude Code lädt die Skills aus dem Ordner, in dem du es startest.

## 6.1 — Claude Code im LUMEN³-Verzeichnis starten

Im Terminal (du bist immer noch im Verzeichnis `~/Documents/GitHub/lumen3`) tippe einfach:

```bash
claude
```

Drücke Enter.

**Was passiert:** Claude Code startet im aktuellen Verzeichnis. Es liest die `CLAUDE.md`-Datei (die globalen Regeln), sieht den `.claude/skills/`-Ordner und weiß, dass hier LUMEN³ liegt. Du siehst eine Begrüßung wie:

```
Welcome to Claude Code. Type your question or command.
Loaded skills: lumen-strategist, lumen-competitive, ...
```

**Falls das nicht funktioniert:** Wenn `claude` nicht als Befehl erkannt wird, ist die Desktop-App von Claude Code nicht im System-PATH installiert. Dann kannst du Claude Code auch aus der Desktop-App starten und dort das Verzeichnis manuell auswählen:

1. Öffne die Claude-Code-Desktop-App
2. Klicke auf „Open Folder" oder das Ordner-Symbol
3. Navigiere zu `Documents/GitHub/lumen3`
4. Bestätige

Claude Code erkennt dann automatisch das LUMEN³-Framework.

## 6.2 — Die Skills prüfen

Sobald Claude Code gestartet ist, tippe:

```
/help
```

Claude zeigt dir eine Liste aller verfügbaren Skills. Wenn du dort `lumen-strategist`, `lumen-competitive`, `lumen-business-context`, `lumen-archetype`, `lumen-interview`, `lumen-trigger`, `lumen-story` und `lumen-universe` siehst, sind die Skills korrekt geladen.

Falls die Liste leer ist oder die LUMEN-Skills fehlen: Schließ Claude Code, stelle sicher, dass du im richtigen Verzeichnis bist (`pwd` auf Mac, `cd` auf Windows zeigt dir das aktuelle Verzeichnis), und starte Claude Code erneut.

\newpage

# 7. Schritt 6 — Die MCP-Server installieren

LUMEN³ nutzt drei externe Komponenten, die als **MCP-Server** (Model Context Protocol) eingebunden werden:

- **Playwright MCP** — Für Wettbewerbs-Analyse (Skill 00)
- **Miro MCP** — Für visuelle Boards (Skills 00, 03, 05, 06)
- **OpenRouter API** — Für Neuro-Color-Recherche (Skill 05, optional)

Alle drei sind **optional**. Skills laufen auch ohne sie — nur bestimmte Features fallen dann weg.

## 7.1 — Playwright MCP installieren

Playwright ist ein headless Browser, mit dem Skill 00 Wettbewerber-Websites automatisch besucht und analysiert.

Im Claude-Code-Terminal (also in Claude selbst, nicht im System-Terminal) tippe:

```
claude mcp add playwright -- npx -y @playwright/mcp@latest
```

Drücke Enter. Claude lädt den Playwright-MCP-Server herunter und installiert ihn. Das dauert 1–3 Minuten.

**Wichtig:** Wenn der Befehl fehlschlägt, hast du wahrscheinlich kein `npx` installiert. Das gehört zu Node.js. Gehe auf **https://nodejs.org**, lade die LTS-Version herunter und installiere sie. Danach den obigen Befehl erneut versuchen.

**Verifizieren:** Im Claude-Code-Terminal tippe `claude mcp list` — du solltest `playwright` in der Liste sehen.

## 7.2 — Miro MCP installieren

Miro ist eine Online-Whiteboard-Plattform. LUMEN³ nutzt sie, um Brand-Analysen visuell zu spiegeln.

Im Claude-Code-Terminal:

```
claude mcp add --scope user --transport http miro https://mcp.miro.com
```

Drücke Enter. Beim ersten Einsatz wirst du aufgefordert, dich bei Miro anzumelden (kostenloser Account ausreichend) und LUMEN³ Zugriff zu gewähren. Folge dem OAuth-Dialog im Browser.

**Verifizieren:** `claude mcp list` sollte auch `miro` anzeigen.

## 7.3 — OpenRouter API-Key (optional, für Skill 05)

Skill 05 kann Perplexity Sonar Pro für Neuro-Color-Recherche nutzen. Dafür brauchst du einen OpenRouter-API-Key. Das ist **optional** — ohne Key läuft Skill 05 mit statischen Haller-Farben, was für die meisten Fälle ausreicht.

**Falls du die Live-Recherche nutzen willst:**

1. Gehe zu **https://openrouter.ai**
2. Erstelle einen Account (kostenlos)
3. Gehe zu *Keys* und erstelle einen neuen API-Key
4. Kopiere den Key (er beginnt mit `sk-or-v1-...`)
5. Öffne eine Datei `.env` im LUMEN³-Verzeichnis (falls noch nicht vorhanden, erstelle sie)
6. Füge eine Zeile hinzu: `OPENROUTER_API_KEY=sk-or-v1-deinKey`
7. Speichere die Datei

**Sicherheitshinweis:** Die `.env`-Datei ist in `.gitignore` eingetragen. Sie wird nicht zu GitHub hochgeladen, auch wenn du später eigene Änderungen pushst. Trotzdem: Teile den Key niemals und committe ihn niemals versehentlich.

\newpage

# 8. Schritt 7 — Erster Durchlauf: `/lumen-strategist`

Jetzt kommt der Moment der Wahrheit. Du startest deinen ersten Skill.

## 8.1 — Den Orchestrator aufrufen

Im Claude-Code-Terminal (im LUMEN³-Verzeichnis) tippe:

```
/lumen-strategist
```

Drücke Enter.

## 8.2 — Was passiert

Der `lumen-strategist`-Skill startet. Er prüft zuerst intern den Projekt-Zustand:

- Gibt es eine `.lumen-session`-Datei? (Nein, beim ersten Lauf)
- Gibt es einen `clients/`-Ordner? (Nein, beim ersten Lauf)
- Welche Skills sind verfügbar? (Alle 8 LUMEN³-Skills plus `lumen-learn`)

Dann begrüßt er dich:

```
🦉 Ich bin dein Brand Strategist für dieses Projekt.

Ich sehe keine laufende Session. Lass uns ein neues Projekt starten.

Wie heißt der Kunde, für den du arbeiten willst?
```

## 8.3 — Ein Projekt anlegen

Antworte mit dem Namen des Kunden (oder dir selbst, wenn du die eigene Marke analysieren willst). Beispiel:

```
Nordlicht Coaching GmbH
```

Der Strategist legt eine neue Session an:

- Erstellt den Ordner `clients/nordlicht-coaching/`
- Legt die Datei `.lumen-session` im Root an, die den Kunden-Namen speichert
- Fragt nach der bevorzugten Sprache (Deutsch / Englisch)
- Schlägt den ersten sinnvollen Skill vor — meistens `/lumen-competitive` oder, wenn du das überspringen willst, `/lumen-business-context`

## 8.4 — Dem vorgeschlagenen Skill folgen

Wenn du das erste Mal LUMEN³ benutzt, **folge den Vorschlägen**. Der Orchestrator kennt die Abhängigkeiten zwischen den Skills besser als du (noch).

Ein typischer Ablauf für einen vollständigen Erstdurchlauf:

1. `/lumen-competitive` — 3–7 Wettbewerber analysieren (60–120 Min)
2. `/lumen-business-context` — 40 Fragen zum Kunden (60–90 Min)
3. `/lumen-archetype` — 28 Aussagen + 20 Szenarien für Archetyp (30–45 Min)
4. `/lumen-interview` — 72 Adjektive sortieren (30–45 Min)
5. `/lumen-trigger` — automatisches Trigger-Scoring (5 Min)
6. `/lumen-story` — Golden Circle + Hedgehog + Dante + Neuro-Color (40–60 Min)
7. `/lumen-universe` — automatische Brand-Universe-Synthese (10–15 Min)

**Gesamt-Zeit:** 3–5 Stunden für einen vollständigen Durchlauf. Du kannst jederzeit pausieren — die Session bleibt erhalten, solange die `.lumen-session`-Datei existiert.

\newpage

# 9. Troubleshooting: Die häufigsten Probleme

## Problem 1: „claude: command not found"

**Mac/Linux:** Claude Code ist installiert, aber nicht im System-PATH. Zwei Lösungen:

1. **Einfacher Weg:** Starte Claude Code aus der Desktop-App, nicht aus dem Terminal. Du kannst in der Desktop-App das Projekt-Verzeichnis manuell auswählen.
2. **Profi-Weg:** Füge Claude Code manuell zum PATH hinzu. Die genaue Methode hängt von deinem Shell (bash/zsh) ab. Konsultiere die Claude-Code-Dokumentation.

## Problem 2: „/lumen-strategist" wird nicht erkannt

Claude Code hat die Skills nicht geladen. Drei mögliche Ursachen:

1. **Falsches Verzeichnis:** Du bist nicht im `lumen3/`-Root, sondern in einem Unterverzeichnis oder ganz woanders. Prüfe mit `pwd` (Mac) oder `cd` (Windows) ohne Argumente.
2. **Fehlende `.claude/skills/`:** Der Ordner existiert nicht oder ist leer. Prüfe mit `ls .claude/skills/`. Wenn nichts angezeigt wird, ist das Repository nicht vollständig geklont. Klone es erneut.
3. **Alte Claude-Code-Version:** Die Skills-Unterstützung ist in älteren Versionen möglicherweise anders. Update Claude Code auf die neueste Version.

## Problem 3: Playwright-Installation schlägt fehl

Meistens wegen fehlendem Node.js. Installiere Node.js LTS von **https://nodejs.org**, dann im Terminal:

```bash
npx -y @playwright/mcp@latest
```

Wenn das funktioniert, kannst du es in Claude Code erneut versuchen.

## Problem 4: Miro-OAuth schlägt fehl

Browser-Cookies und Session-Probleme. Melde dich auf **https://miro.com** neu an, dann im Claude-Code-Terminal den MCP-Befehl erneut ausführen.

## Problem 5: Ein Skill bricht mit einer Fehlermeldung ab

Die häufigste Ursache ist, dass eine Vorgänger-Datei fehlt oder das Schema nicht passt. Beispiel: Du startest `/lumen-trigger`, aber `02-brand-archetype.md` existiert noch nicht. Lösung: Erst den Vorgänger-Skill laufen lassen.

Der `/lumen-strategist` zeigt dir immer den korrekten nächsten Schritt. Wenn du unsicher bist, starte ihn und folge seinem Vorschlag.

## Problem 6: Die Session ist weg

Wenn du Claude Code neu startest, findest du die Session wieder über die `.lumen-session`-Datei im Root. Solange diese Datei existiert, kann der Orchestrator dort weitermachen, wo du aufgehört hast.

**Falls du die Datei versehentlich gelöscht hast:** Du kannst sie manuell wiederherstellen. Öffne sie in einem Text-Editor und schreibe:

```
client_name: nordlicht-coaching
language: de
last_skill: 04-trigger-analysis
```

Passe die Werte an deinen Stand an.

\newpage

# 10. Was tun, wenn etwas nicht funktioniert?

**Drei-Schritte-Regel:**

1. **Lies die Fehlermeldung sorgfältig.** Claude Code gibt meistens klare Hinweise, was falsch ist.
2. **Starte den `lumen-strategist`.** Er prüft den Projekt-Zustand und schlägt eine Lösung vor.
3. **Frag Claude direkt.** In Claude Code kannst du jederzeit natürlichsprachlich fragen, z. B. „Warum funktioniert mein /lumen-competitive nicht?"

**Wenn nichts hilft:**

- Prüfe das README des LUMEN³-Repositorys. Dort gibt es meistens Hinweise zu bekannten Problemen.
- Stelle eine Frage im GitHub-Issue-Tracker des Repositorys.
- Kontaktiere Owlist direkt (info@owlist.ch).

\newpage

# 11. Zusammenfassung — Das musst du dir merken

1. **Claude Code ist das Werkzeug, LUMEN³ ist das Framework.** Du startest Claude Code immer im LUMEN³-Verzeichnis.
2. **GitHub-Clone einmal, danach lokal arbeiten.** Du klonst das Repository nur einmal. Updates holst du dir mit `git pull`.
3. **Der Einstiegspunkt ist immer `/lumen-strategist`.** Dieser Orchestrator kennt den Projekt-Zustand und schlägt den nächsten Schritt vor.
4. **MCP-Server sind optional.** Playwright und Miro machen den Prozess reicher, sind aber nicht zwingend.
5. **Sessions bleiben erhalten.** Du kannst jederzeit pausieren und später weitermachen, solange `.lumen-session` existiert.
6. **Die Skills-Ausführung ist sequenziell.** Du kannst nicht Skill 04 starten, ohne vorher Skill 02 und 03 durchlaufen zu haben. Der Orchestrator verhindert das.
7. **Outputs werden unter `clients/[name]/outputs/` gespeichert.** Dort findest du alle Markdown-Dateien und Slide-Sets deines Brand-Projekts.

Viel Erfolg mit deinem ersten LUMEN³-Durchlauf! 🦉

---

**LUMEN³ Setup-Anleitung**
© 2026 Owlist GmbH · Tobias Schmidt · www.owlist.ch
Version 1.0 · April 2026
