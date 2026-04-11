# Skill 00 — Creative Footprint Full Potential Analyse

## Rekonstruktion der Datenpunkte (Review-Draft v0.2)

**Basis:** Enigma Creative Footprint Workshop (2022-05-03) für Thought Leader & Partner (später Owlist).
**Methodische Quelle:** Enigma Swiss — Full Potential Analyse, 5 Dimensionen (PESO + Assets-Erweiterung).
**Stand:** 2026-04-11 · v0.2 — nach Nutzer-Feedback auf Qualität reduziert, Phase 2 ergänzt.

---

## Änderungen gegenüber v0.1

- **123 kuratierte Datenpunkte** statt 139 (15 redundante/schwache Punkte entfernt)
- **Phase 2 "Visuelle Analyse"** neu hinzugefügt (4 Enigma-Module: Farbrad, Font-Tabelle, Namens-Archetypen, Tagline-Quadrant)
- **Dimensions-Gewichtung:** Datenpunkt-proportional fixiert (keine Gleichverteilung)
- **Benchmarks** (Campana Schott 50 etc.) raus — auf Nutzer-Wunsch
- **Ehrliche Positionierung:** Das Enigma-Original dokumentierte 139 Datenpunkte. LUMEN³ v2 arbeitet mit 123 kuratierten, redundanzfreien Datenpunkten in derselben 5-Dimensionen-Struktur. Schärfung, keine Abschwächung.

---

## Allgemeine Scoring-Regeln

- **Skala:** 0 / 1 / 2 pro Datenpunkt
  - **0** = nicht vorhanden, nicht messbar, oder explizit abwesend
  - **1** = vorhanden, aber schwach / unvollständig / ausbaufähig
  - **2** = vorhanden und gut ausgeführt / Best-Practice-Niveau
- **Normierung:** Rohsumme pro Dimension → auf 100 normiert → zum **Full Potential Score 0–100** zusammengeführt.
- **Technisch nicht erhebbar = 0** (nicht "N/A"), damit der Score vergleichbar bleibt.
- **Automatisierung:** Wo möglich extrahiert Playwright MCP die Werte. Wo nicht, führt Claude Sonnet die qualitative Bewertung nach dem Scoring-Kriterium aus.

---

## Dimensions-Verteilung (final)

| Dimension | Datenpunkte | Gewicht am Full Score |
|---|---|---|
| Assets | 54 | 44% |
| Paid Media | 8 | 6% |
| Earned Media | 17 | 14% |
| Shared Media | 14 | 11% |
| Owned Media | 30 | 25% |
| **Summe** | **123** | **100%** |

**Begründung der Gewichtung:** Proportional zur Datenpunkt-Anzahl, weil Enigma-Original Assets (60) deutlich mehr Gewicht gibt als jeder Medien-Dimension. Das spiegelt die strategische Kernthese: "Eine Marke ist zuerst in sich selbst stark, dann in ihrer Kommunikation."

---

# PHASE 1 — FULL POTENTIAL SCORING (123 Datenpunkte)

## 1. ASSETS (54 Datenpunkte)

### 1.1 Brand Evolution — 6 Datenpunkte · 11% von Assets

Misst, wie weit die Marke ihre strategische Entwicklung dokumentiert hat.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| A.BE.01 | Positionierungs-Statement öffentlich | Website-Scan (About, Manifesto) | 0 = keines · 1 = vorhanden aber generisch · 2 = präzise, differenzierend |
| A.BE.02 | Brand Vision dokumentiert | Website + öffentliche Quellen | 0 = keine · 1 = allgemein formuliert · 2 = spezifisch und datiert |
| A.BE.03 | Brand Mission dokumentiert | Website-Scan | 0 = keine · 1 = Standard-Formulierung · 2 = aktiv gelebt, konkret |
| A.BE.04 | Entwicklungs-Meilensteine sichtbar | About/Timeline/History | 0 = keine · 1 = 1–2 genannt · 2 = dokumentierte Timeline |
| A.BE.05 | Nachvollziehbare Brand-Geschichte | About-Tiefe | 0 = keine · 1 = Standard-Text · 2 = narrativ, persönlich |
| A.BE.06 | Konsistenz Kern-Botschaft über 3+ Kanäle | Website + 2 Social | 0 = divergent · 1 = teilweise · 2 = konsistent |

### 1.2 Why / How / What — 11 Datenpunkte · 20% von Assets

Basis: Simon Sinek *Start With Why* (2009). Misst Klarheit und Sichtbarkeit des Golden Circle.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| A.WHW.01 | WHY explizit formuliert | Website-Scan | 0 = keines · 1 = implizit · 2 = explizit, eigene Section |
| A.WHW.02 | WHY folgt "Um zu..." / "Wir glauben..."-Struktur | Text-Analyse | 0 = Produkt-Beschreibung · 1 = teilweise · 2 = echte Glaubensaussage |
| A.WHW.03 | WHY ist spezifisch, nicht generisch | Buzzword-Check | 0 = "unser Ziel ist..." · 1 = teilweise spezifisch · 2 = differenzierend |
| A.WHW.04 | HOW als Differenzierungs-Prozess formuliert | Methoden/Prozess-Seite | 0 = keine · 1 = Leistungsliste · 2 = eigener Prozess benannt |
| A.WHW.05 | HOW beschreibt 2–4 konkrete Prinzipien | Werte/Prinzipien-Seite | 0 = keine · 1 = 1 Prinzip · 2 = 2–4 klare Prinzipien |
| A.WHW.06 | WHAT klar benannt | Produkt/Service-Seite | 0 = unklar · 1 = Liste · 2 = strukturiert + Nutzen |
| A.WHW.07 | Golden-Circle-Reihenfolge in Kommunikation | Hero → Services → About-Flow | 0 = WHAT-first · 1 = gemischt · 2 = WHY-first |
| A.WHW.08 | WHY in Hero-Section der Homepage sichtbar | H1/Above-Fold | 0 = WHAT · 1 = HOW · 2 = WHY |
| A.WHW.09 | WHY in Tagline/Claim integriert | Logo-Area, Footer | 0 = keine Tagline · 1 = deskriptiv · 2 = WHY-basiert |
| A.WHW.10 | WHY in Recruiting/Karriere sichtbar | Karriere-Seite | 0 = keine · 1 = Standard · 2 = WHY-Zentrierung |
| A.WHW.11 | WHY konsistent in Founder-/Team-Kommunikation | LinkedIn Top-3 Profile | 0 = inkonsistent · 1 = teilweise · 2 = konsistent |

### 1.3 Neuromarketing — 9 Datenpunkte · 17% von Assets

Basis: Damasio, Zaltman, Hogshead Fascinate, 7 LUMEN3-Trigger. Misst bewusste Aktivierung emotionaler Muster.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| A.NM.01 | Primärer Trigger identifizierbar | Qualitative Analyse Hero + Tonalität | 0 = unklar · 1 = vermutbar · 2 = eindeutig |
| A.NM.02 | Sekundärer Trigger identifizierbar | Qualitative Analyse | 0 = unklar · 1 = vermutbar · 2 = eindeutig, ≠ Primary |
| A.NM.03 | Trigger visuell konsistent (Farbe, Bild) | Farbpalette vs. Trigger-Mapping | 0 = divergent · 1 = teilweise · 2 = konsistent |
| A.NM.04 | Trigger verbal konsistent (Tonalität) | Textanalyse Hero + Blog | 0 = divergent · 1 = teilweise · 2 = konsistent |
| A.NM.05 | Hero-Section 3-Sekunden-Test (emotionale Resonanz) | Screenshot-Review | 0 = neutral · 1 = erkennbar · 2 = stark |
| A.NM.06 | Somatic-Marker-aktivierende Bild- und Metaphern-Sprache | Hero-Image + Textanalyse | 0 = Stock/generisch · 1 = thematisch · 2 = emotional aufgeladen, konsistentes Metaphern-System |
| A.NM.07 | Trigger auch in FAQ/Support-Sprache | Support-Seite | 0 = sachlich-neutral · 1 = gemischt · 2 = Brand-konform |
| A.NM.08 | CTAs Trigger-konform (nicht generisch) | Button-Analyse | 0 = "Mehr erfahren" · 1 = teilweise spezifisch · 2 = Brand-Voice |
| A.NM.09 | Primary ≠ Secondary (kein Double Trigger) | Trigger-Analyse | 0 = Double · 1 = schwach getrennt · 2 = klar getrennt |

### 1.4 Brand Toolbox — 17 Datenpunkte · 31% von Assets

Die größte Kategorie — misst operative Ausstattung mit Design-Assets und Guidelines.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| A.BT.01 | Logo als SVG vorhanden | Download / Media-Kit | 0 = nur Pixel · 1 = PNG + unklar · 2 = SVG + Variants |
| A.BT.02 | Logo-Varianten (horizontal, vertikal, Icon) | Media-Kit | 0 = 1 Variante · 1 = 2 · 2 = 3+ |
| A.BT.03 | Logo-Schutzzone dokumentiert | Brand Guidelines | 0 = nein · 1 = erwähnt · 2 = definiert |
| A.BT.04 | Logo-Minimalgröße definiert | Brand Guidelines | 0 = nein · 1 = erwähnt · 2 = definiert |
| A.BT.05 | Primärfarbe mit Hex/RGB/CMYK/Pantone | Brand Guidelines | 0 = keine Codes · 1 = Hex only · 2 = alle 4 |
| A.BT.06 | Sekundärfarben-Palette (3–5 Farben) | Brand Guidelines | 0 = keine · 1 = 1–2 · 2 = 3–5 mit Rolle |
| A.BT.07 | Akzent- und Funktionsfarben definiert | Brand Guidelines | 0 = nein · 1 = teilweise · 2 = ja |
| A.BT.08 | Primär-Font mit Lizenz geregelt | CSS + Brand Guidelines | 0 = System-Font · 1 = Custom ohne Lizenz-Hinweis · 2 = Custom lizenziert |
| A.BT.09 | Sekundär-Font mit Lizenz | CSS + Guidelines | 0 = nein · 1 = teilweise · 2 = ja |
| A.BT.10 | Font-Hierarchie H1–H6 + Body definiert | CSS-Analyse | 0 = flach · 1 = teilweise · 2 = vollständige Typo-Skala |
| A.BT.11 | Icon-System konsistent (Stil, Strichstärke) | Icon-Audit | 0 = Mix · 1 = teilweise · 2 = ein System |
| A.BT.12 | Foto-Stil-Guide erkennbar | Bildanalyse Website | 0 = Stock-Mix · 1 = teilweise · 2 = eigener Stil |
| A.BT.13 | Illustration-Stil definiert (falls verwendet) | Illustration-Audit | 0 = nein · 1 = inkonsistent · 2 = konsistent |
| A.BT.14 | Brand-Templates vorhanden (PPT, Social, Letter) | Media-Kit | 0 = keine · 1 = 1 · 2 = 3+ |
| A.BT.15 | Brand Guidelines PDF/Online existiert | Öffentlich oder Press-Kit | 0 = nein · 1 = intern · 2 = öffentlich zugänglich |
| A.BT.16 | Voice & Tone Guidelines | Brand Guidelines | 0 = nein · 1 = erwähnt · 2 = mit Beispielen |
| A.BT.17 | Brand-Asset-Repository zentral/versioniert | Media-Kit / Brand Portal | 0 = keine · 1 = lose Ordner · 2 = zentrale Plattform |

### 1.5 Brand Story — 11 Datenpunkte · 20% von Assets

Misst die narrative Kraft und Konsistenz der Markenerzählung.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| A.BS.01 | 1-Satz-Essenz der Marke | Tagline / About | 0 = keine · 1 = generisch · 2 = differenzierend |
| A.BS.02 | Elevator Pitch (60–90 Sek.) | About-Page / Pitch-Video | 0 = keine · 1 = Standard · 2 = resonant |
| A.BS.03 | About-Page-Version (150–250 Wörter) | About-Seite | 0 = Kurz-Blurb · 1 = faktisch · 2 = narrativ |
| A.BS.04 | Gründungs-Geschichte erzählt | About / Timeline | 0 = keine · 1 = Daten · 2 = Story |
| A.BS.05 | Kunde als Held im Narrativ (nicht Firma) | Copy-Analyse | 0 = Firma-zentriert · 1 = gemischt · 2 = Kunde-zentriert |
| A.BS.06 | Konflikt/Pain-Point im Narrativ präsent | Copy | 0 = keine · 1 = benannt · 2 = aktiv bearbeitet |
| A.BS.07 | Transformation des Kunden sichtbar | Case Studies, Testimonials | 0 = nein · 1 = behauptet · 2 = bewiesen |
| A.BS.08 | Geografische/kulturelle Verankerung | About / Origin-Story | 0 = keine · 1 = erwähnt · 2 = identitätsstiftend |
| A.BS.09 | Story konsistent über Kanäle | Cross-Channel-Check | 0 = divergent · 1 = teilweise · 2 = konsistent |
| A.BS.10 | Story emotional bewegend | Textqualität, Rhythmus | 0 = faktisch · 1 = gemischt · 2 = bewegend |
| A.BS.11 | Story im Recruiting präsent | Karriere-Seite | 0 = keine · 1 = Benefits · 2 = WHY + Purpose |

---

## 2. PAID MEDIA (8 Datenpunkte)

Gleichgewichtete Sub-Dimensionen (je ~33%).

### 2.1 Channels — 3 Datenpunkte

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| P.CH.01 | Aktive Paid-Channels gesamt | Meta Ad Library, Google Ads Transparency | 0 = keine · 1 = 1 Channel · 2 = 2+ |
| P.CH.02 | Channel-Mix ausgewogen und zielgruppen-passend | Cross-Platform-Check + B2B/B2C-Match | 0 = monolithisch oder Mismatch · 1 = ok · 2 = zielgruppenadaptiv |
| P.CH.03 | Aktive Kampagnen im letzten Quartal | Ad Library-Timeline | 0 = keine · 1 = Einzelkampagne · 2 = kontinuierlich |

### 2.2 Tracking Setup — 3 Datenpunkte

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| P.TR.01 | Analytics installiert (GA4, Plausible, Matomo) | Network-Requests / Cookies | 0 = keine · 1 = Basis · 2 = mit Events |
| P.TR.02 | Conversion-Tracking über Funnel | Pixel/Events sichtbar | 0 = keine · 1 = Page-Views · 2 = Events |
| P.TR.03 | Attribution-Modell erkennbar | GTM Container, Blog-Hinweise | 0 = keine · 1 = Default · 2 = dokumentiert |

### 2.3 Funnel Coverage — 2 Datenpunkte

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| P.FC.01 | Funnel-Stage-Diversität (ToFu/MoFu/BoFu) | Ad-Library Formate + CTAs | 0 = nur eine Stage · 1 = zwei Stages · 2 = alle drei |
| P.FC.02 | Conversion-optimierte Ads (BoFu-Qualität) | CTA-Spezifität, Landing-Page-Match | 0 = keine · 1 = generisch · 2 = optimiert |

---

## 3. EARNED MEDIA (17 Datenpunkte)

### 3.1 Google News — 3 Datenpunkte · 19%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| E.GN.01 | Aktuelle News-Erwähnungen (letztes Quartal) | Google News Search | 0 = keine · 1 = 1–2 · 2 = 3+ |
| E.GN.02 | News-Quellen-Qualität | Tier-Analyse | 0 = Blogs · 1 = Fachportale · 2 = Tier-1 Medien |
| E.GN.03 | Sentiment der Erwähnungen | Qualitative Einschätzung | 0 = negativ · 1 = neutral · 2 = positiv |

### 3.2 Influencer — 5 Datenpunkte · 31%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| E.IN.01 | Aktuelle Influencer-Erwähnungen | Social-Search | 0 = keine · 1 = 1–2 · 2 = 3+ |
| E.IN.02 | Tier der Influencer | Follower-Check | 0 = Mikro (<10k) · 1 = Mid (10–100k) · 2 = Macro (100k+) |
| E.IN.03 | Relevanz zur Zielgruppe | Qualitative Bewertung | 0 = off-topic · 1 = teilweise · 2 = hohe Relevanz |
| E.IN.04 | Organische vs. bezahlte Mentions | Disclosure-Check (#ad) | 0 = nur bezahlt · 1 = gemischt · 2 = organisch |
| E.IN.05 | Cross-Plattform-Präsenz | Multi-Platform-Check | 0 = 1 Plattform · 1 = 2 · 2 = 3+ |

### 3.3 Media Corner — 3 Datenpunkte · 19%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| E.MC.01 | Press-Kit-Seite vorhanden | /presse, /media, /press | 0 = keine · 1 = Basis · 2 = vollständig |
| E.MC.02 | Aktuelle Press-Releases (letzte 6 Mon.) | Press-Seite | 0 = keine · 1 = 1 · 2 = 2+ |
| E.MC.03 | Media-Kontakt-Person benannt | Impressum / Press | 0 = keine · 1 = generisch · 2 = Name + Direktkontakt |

### 3.4 Social Proof — 6 Datenpunkte · 31%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| E.SP.01 | Testimonials auf Website | Testimonials-Section | 0 = keine · 1 = 1–2 · 2 = 3+ mit Bild/Name |
| E.SP.02 | Kunden-Case-Studies | Case-Study-Seite | 0 = keine · 1 = Logo-Wand · 2 = narrative Case Studies |
| E.SP.03 | Trustpilot/Google/Glassdoor Präsenz | Review-Plattform-Check | 0 = keine · 1 = Eintrag · 2 = aktiv gepflegt |
| E.SP.04 | Rating-Score ≥ 4.0/5 | Review-Aggregate | 0 = <3.5 · 1 = 3.5–4.0 · 2 = ≥4.0 |
| E.SP.05 | Review-Anzahl (Threshold 10+) | Review-Plattform | 0 = <5 · 1 = 5–10 · 2 = 10+ |
| E.SP.06 | Prominente Kunden-Logos sichtbar | Website | 0 = keine · 1 = 1–3 · 2 = 4+ mit Anerkennung |

---

## 4. SHARED MEDIA (14 Datenpunkte)

Kanonische Struktur: pro Kanal **3 Datenpunkte** (Aktivität · Reichweite · Brand-Konformität), außer TikTok (2).

### 4.1 Facebook — 3 Datenpunkte · 26%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| S.FB.01 | Aktivität (Frequenz + letzter Post) | Page-Scan | 0 = inaktiv (>60d) · 1 = sporadisch · 2 = regelmäßig |
| S.FB.02 | Reichweite + Engagement-Rate | Follower × Likes/Comments | 0 = <500 oder <1% ER · 1 = mittel · 2 = gut |
| S.FB.03 | Visuelle + verbale Brand-Konformität | Post-Galerie-Review | 0 = divergent · 1 = teilweise · 2 = konsistent |

### 4.2 Instagram — 3 Datenpunkte · 26%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| S.IG.01 | Aktivität (Feed + Stories/Reels) | Profil + Story-Highlights | 0 = inaktiv · 1 = nur Feed · 2 = Feed + Stories/Reels |
| S.IG.02 | Reichweite + Engagement-Rate | Follower × ER | 0 = <500 oder <1% · 1 = mittel · 2 = gut |
| S.IG.03 | Grid-Visual-Konsistenz | Grid-Preview | 0 = Mix · 1 = teilweise · 2 = kuratiert |

### 4.3 LinkedIn — 3 Datenpunkte · 22%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| S.LI.01 | Company-Page Aktivität | Page-Scan | 0 = inaktiv · 1 = selten · 2 = regelmäßig |
| S.LI.02 | Employee-Advocacy + Founder-Präsenz | Team-Profile Top 3 | 0 = keine · 1 = einzelne aktiv · 2 = Team-Bewegung |
| S.LI.03 | Content-Qualität (Thought Leadership vs. Promo) | Post-Analyse | 0 = nur Promo · 1 = gemischt · 2 = Insights |

### 4.4 Twitter/X — 3 Datenpunkte · 18%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| S.TW.01 | Account-Aktivität | Profil-Scan | 0 = inaktiv · 1 = selten · 2 = regelmäßig |
| S.TW.02 | Engagement + Response-Zeit | Replies/Retweets, Mention-Antworten | 0 = keines · 1 = Tage · 2 = Stunden + aktiv |
| S.TW.03 | Content-Diversität (Original vs. Re-Post) | Post-Mix | 0 = nur Re-Posts · 1 = gemischt · 2 = Original + Kurierung |

### 4.5 TikTok — 2 Datenpunkte · 8%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| S.TK.01 | Account + Content-Aktualität | Search + Feed | 0 = keiner · 1 = Bio only · 2 = aktiv <1 Mon |
| S.TK.02 | Content-Qualität (Format-Fit, Trends) | Video-Review | 0 = Re-Post · 1 = einfach · 2 = nativ TikTok-konform |

---

## 5. OWNED MEDIA (30 Datenpunkte)

### 5.1 Newsletter — 5 Datenpunkte · 17%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.NL.01 | Newsletter aktiv/sichtbar auf Website | Footer/Popup-Check | 0 = nein · 1 = Footer only · 2 = prominent |
| O.NL.02 | Opt-in niederschwellig | Feldanzahl | 0 = 5+ Felder · 1 = 2–4 · 2 = nur Email |
| O.NL.03 | Regelmäßige Aussendung (min. monatlich) | Archiv / Blog-Newsletter | 0 = keine · 1 = quartalsweise · 2 = monatlich+ |
| O.NL.04 | Mehrwert-Content (nicht nur Verkauf) | Newsletter-Inhalt | 0 = nur Promo · 1 = gemischt · 2 = Value-first |
| O.NL.05 | Double-Opt-In (DSGVO-konform) | Signup-Flow-Test | 0 = keiner · 1 = single · 2 = double |

### 5.2 Content Strategy — 6 Datenpunkte · 22%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.CS.01 | Content-Kalender erkennbar (Publikations-Rhythmus) | Blog-Timeline | 0 = sporadisch · 1 = unregelmäßig · 2 = regelmäßig |
| O.CS.02 | Topic-Cluster / Säulen definiert | Kategorie-Struktur | 0 = keine · 1 = grob · 2 = strukturiert |
| O.CS.03 | SEO-Integration im Content | H-Struktur, Meta, Keywords | 0 = nein · 1 = Basis · 2 = optimiert |
| O.CS.04 | Format-Diversität (Blog, Video, Podcast, Download) | Content-Typen-Audit | 0 = 1 Format · 1 = 2 · 2 = 3+ |
| O.CS.05 | Content-Tiefe (Longform vs. Listicles) | Wortzahl-Analyse | 0 = <500 · 1 = 500–1500 · 2 = 1500+ |
| O.CS.06 | Aktualität + Evergreen-Substanz | Publikations-Datum + Cornerstone-Check | 0 = >180 Tage oder keine Substanz · 1 = aktuell ODER Evergreen · 2 = beides |

### 5.3 Website Performance — 6 Datenpunkte · 20%

Erhoben via Lighthouse / PageSpeed Insights / Playwright-Performance-API.

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.WP.01 | Lighthouse Performance Score (Desktop + Mobile) | Lighthouse CLI | 0 = <60 · 1 = 60–79 · 2 = ≥80 |
| O.WP.02 | LCP (Largest Contentful Paint) | Core Web Vitals | 0 = >4s · 1 = 2.5–4s · 2 = ≤2.5s |
| O.WP.03 | CLS (Cumulative Layout Shift) | CWV | 0 = >0.25 · 1 = 0.1–0.25 · 2 = ≤0.1 |
| O.WP.04 | INP (Interaction to Next Paint) | CWV | 0 = >500ms · 1 = 200–500ms · 2 = ≤200ms |
| O.WP.05 | TTFB (Server-Response-Time) | Network | 0 = >1.5s · 1 = 600ms–1.5s · 2 = ≤600ms |
| O.WP.06 | Image-Optimization (WebP/AVIF, lazy-loading) | Source-Audit | 0 = keine · 1 = teilweise · 2 = vollständig |

### 5.4 SEO — 6 Datenpunkte · 20%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.SE.01 | Title-Tags + Meta-Descriptions auf Key-Pages | HTML-Audit | 0 = fehlen · 1 = teilweise · 2 = vollständig |
| O.SE.02 | Strukturierte Daten (Schema.org) | JSON-LD-Check | 0 = keine · 1 = Basis · 2 = umfassend |
| O.SE.03 | XML-Sitemap + robots.txt | `/sitemap.xml`, `/robots.txt` | 0 = fehlen · 1 = 1 von 2 · 2 = beide |
| O.SE.04 | Backlink-Profil (DR-Wert) | Ahrefs/SEMrush | 0 = DR<10 · 1 = DR 10–30 · 2 = DR>30 |
| O.SE.05 | Ranking für Core-Keywords | SERP-Check Top 3 Keywords | 0 = nicht rankend · 1 = Seite 2+ · 2 = Top 10 |
| O.SE.06 | Mobile-First-Indexing-ready | Mobile-Lighthouse | 0 = nein · 1 = teilweise · 2 = ja |

### 5.5 Mobile UX — 5 Datenpunkte · 17%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.MU.01 | Responsive Design über Breakpoints | Playwright Multi-Viewport | 0 = nein · 1 = teilweise · 2 = vollständig |
| O.MU.02 | Mobile Menu funktional | Playwright Touch-Simulation | 0 = broken · 1 = funktional · 2 = excellent |
| O.MU.03 | Touch-Targets ≥ 44×44 px | CSS-Audit | 0 = <32px · 1 = 32–44px · 2 = ≥44px |
| O.MU.04 | Font-Sizes auf Mobile lesbar | CSS-Audit | 0 = <14px · 1 = 14–16px · 2 = ≥16px |
| O.MU.05 | Forms auf Mobile nutzbar | Form-Audit | 0 = unbrauchbar · 1 = funktional · 2 = optimiert |

### 5.6 Website Security — 2 Datenpunkte · 7%

| ID | Datenpunkt | Messung | Scoring-Kriterium |
|---|---|---|---|
| O.WS.01 | HTTPS/SSL-Zertifikat gültig | SSL-Check | 0 = HTTP · 1 = selbstsigniert · 2 = gültiges Zertifikat |
| O.WS.02 | Security-Header (CSP, HSTS, X-Frame-Options) | Header-Audit (observatory.mozilla.org) | 0 = keine · 1 = 1–2 · 2 = 3+ |

---

## Berechnungs-Formel Phase 1

```
Roh-Score(Dimension) = Σ(Datenpunkte) / (Anzahl × 2) × 100

Full Potential Score = 
  Assets × 0.44 +
  Paid × 0.06 +
  Earned × 0.14 +
  Shared × 0.11 +
  Owned × 0.25
```

---

# PHASE 2 — VISUELLE ANALYSE (4 Enigma-Module)

Nach dem 123-Datenpunkt-Scoring folgt die **qualitative visuelle Analyse des Wettbewerbsumfelds**. Diese Module arbeiten nicht mit einem numerischen Score, sondern mit **Positionierungs-Karten**, die zeigen, wo der Markt überfüllt ist und wo strategische Lücken liegen. Das ist der Enigma-Original-Workshop-Teil "Brandanalyse" (Vormittag), der im ersten Refactor verloren gegangen war.

Alle 4 Module sind **wettbewerbs-relativ** — sie analysieren nicht einen einzelnen Player, sondern die Positionen aller im Scope der Analyse.

## Phase 2.1 — Farbanalyse (Farbrad)

**Methode:** Alle Primär- und Akzentfarben der Wettbewerber werden auf einem HSL-Farbkreis positioniert. Dichte-Cluster ("Crowded zones") vs. Lücken ("Potential zones") werden sichtbar.

**Mess-Ablauf:**
1. Aus jeder Playwright-Extraktion: Primary- und Accent-Hex extrahieren
2. Jeden Hex in HSL umrechnen (Hue 0–360°, Saturation, Lightness)
3. Nur Hue verwenden, auf einem Kreis plotten
4. Saturation und Lightness über Punktgröße / Füllung kodieren
5. Dichte-Analyse: pro 30°-Segment zählen — wo Cluster?

**Ausgabe:**
- SVG/PNG Farbrad mit allen Wettbewerber-Farben
- Markierung: 2–3 "Crowded zones" und 2–3 "Potential zones"
- Textbeschreibung: "Im Markt dominieren Blau und Dunkelgrün. Terrakotta, Gelb und kühles Neutral sind unbesetzt."

**Beispiel aus dem Enigma-Workshop:** In der Luftfahrtindustrie waren Rot, Mittelblau, Dunkelgrün dicht besetzt (Crowded). Pastell-Gelb, Violett, warmes Braun unbesetzt (Potential).

## Phase 2.2 — Schriftart-Analyse (Font-Tabelle)

**Methode:** Alle Wettbewerber-Fonts werden in einem 2D-Koordinatensystem positioniert. Das zeigt Dichte-Cluster im Typografie-Raum.

**Zwei Achsen:**
- **X-Achse:** Condensed ↔ Extended (Breite)
- **Y-Achse:** Light ↔ Bold (Gewicht)

**Drei Kategorien (Farbkodierung):**
- Serif
- Sans-serif
- Script / Display

**Mess-Ablauf:**
1. Aus Playwright-Extraktion: Primary Display Font + Body Font jedes Wettbewerbers
2. Manuelles Lookup der Font-Metadaten (Google Fonts API oder Fontshare):
   - Klassifikation (serif/sans/script)
   - Gewicht (100–900)
   - Breite (condensed/normal/extended) — falls nicht angegeben, visuell bestimmen
3. Position im 2D-Raster: (x = Breite, y = Gewicht)
4. Häufigkeits-Muster identifizieren

**Enigma-Original-Beobachtung:** "Zu oft verwendete Elemente" — Sans-serif Black-and-White, Slash-Akzente, Circular-Schnitte, Angular-Schnitte. Diese werden im Output als "vermeiden" markiert.

**Ausgabe:**
- 2D-Plot (SVG) mit allen Wettbewerber-Fonts
- "Font-Tabu-Liste": Elemente, die im Markt überstrapaziert sind
- Empfehlungs-Korridor: wo könnte eine eigene Typografie-Identität positioniert sein?

## Phase 2.3 — Namensanalyse (4 Namens-Archetypen)

**Methode:** Jeder Wettbewerber-Name wird einem der 4 Enigma-Archetypen zugeordnet. Das zeigt, welche Namensstrategien im Markt dominieren.

**4 Namens-Archetypen:**

| Archetyp | Definition | Beispiele aus dem Enigma-Workshop |
|---|---|---|
| **Familienname** | Nachname(n) des/der Gründer | Campana Schott, Sedlak & Partner |
| **Stimmungsvoll** | Evokative, emotionale Wörter | — |
| **Erfunden** | Künstliches Kunstwort ohne Alltagsbedeutung | Murakamy, Atrete |
| **Erlebnisorientiert** | Beschreibt Erfahrung/Wirkung, die die Marke erzeugt | — |

**Mess-Ablauf:**
1. Für jeden Wettbewerber: Name holen
2. Klassifikation nach Regel:
   - Enthält Nachname(n) → **Familienname**
   - Steht im Wörterbuch mit emotionaler Konnotation → **Stimmungsvoll**
   - Nicht im Wörterbuch, keine erkennbare Ableitung → **Erfunden**
   - Beschreibt eine Wirkung oder ein Erlebnis (z.B. "Flow", "Clear") → **Erlebnisorientiert**
3. Häufigkeits-Verteilung über Wettbewerber

**Ausgabe:**
- Balkendiagramm Verteilung der 4 Archetypen im Markt
- Strategische Aussage: "5 von 6 Wettbewerbern nutzen Familienname — ein erfundener oder erlebnisorientierter Name wäre im Markt unverwechselbar."

## Phase 2.4 — Tagline-Analyse (2D-Quadrant)

**Methode:** Jede Wettbewerber-Tagline wird auf zwei Achsen positioniert. Das zeigt, wo das tonale/semantische Feld überfüllt ist.

**Zwei Achsen:**
- **X-Achse:** Selbsterklärend ↔ Geheimnisvoll
- **Y-Achse:** Business ↔ Wissenschaft

**Mess-Ablauf:**
1. Für jeden Wettbewerber: Tagline extrahieren (Header, Footer, Meta-Title, Claim)
2. Claude Sonnet klassifiziert qualitativ:
   - Selbsterklärend (0) ↔ Geheimnisvoll (10): Wie direkt erschließt sich die Bedeutung?
   - Business (0) ↔ Wissenschaft (10): Pragmatischer Business-Ton vs. akademisch-reflexiver Ton?
3. Koordinaten-Paar pro Tagline
4. Plot als Scatter-Diagramm

**Enigma-Original-Beispiele:**
- "Leidenschaft für Zusammenarbeit" → niedrig X (selbsterklärend), niedrig Y (Business)
- "Wir stärken die Selbsterneuerungskraft Ihrer Organisation" → hoch Y (Wissenschaft), mittel X
- "Independent and neutral IT consulting from Switzerland" → sehr niedrig X (extrem selbsterklärend), niedrig Y
- "Everyone has a meaningful life with ease" → hoch X (geheimnisvoll), mittel Y

**Ausgabe:**
- 2D-Quadrant mit allen Wettbewerber-Taglines
- Cluster-Markierung
- Empfehlungs-Korridor: "Der Business-Selbsterklärend-Quadrant ist übersättigt. Eine Tagline im Wissenschaft-Geheimnisvoll-Quadrant wäre maximal differenzierend."

---

# PHASE 3 — SYNTHESE & POSITIONIERUNGS-LÜCKEN

Nach Phase 1 (Scoring) und Phase 2 (Visuelle Analyse) folgt die Zusammenführung:

1. **Score-Ranking** der Wettbewerber (Full Potential 0–100)
2. **Dimension-Profile** pro Wettbewerber (wo sind sie stark, wo schwach)
3. **Visuelle Lücken aus Phase 2** (Farbe, Font, Name, Tagline)
4. **Strategische Lücken-Hypothesen:** Wo ist der Markt unterbesetzt? Welche Position könnte die eigene Marke besetzen?
5. **Konkrete Handlungsimpulse** für Skill 01 (Business Context) und Skill 06 (Brand Universe)

---

# PHASE 4 — MARKDOWN-OUTPUT (Schema 00)

Der Skill schreibt `clients/[name]/outputs/00-competitive-analysis.md` nach dem erweiterten Schema 00 in `artefact-templates.md`. Die Struktur muss um Phase-2-Sections erweitert werden:

```markdown
# LUMEN¹ — Creative Footprint Full Potential Analyse
## [Projektname] | [Datum]
## Methodik: Enigma Creative Footprint (2022) + Owlist Asset-Erweiterung

## Markt-Übersicht
## Full Potential Ranking (Phase 1)
## Dimension-Profile pro Wettbewerber
### [Wettbewerber 1]
  - Full Score: XX/100
  - Assets: XX · Paid: XX · Earned: XX · Shared: XX · Owned: XX
  - Top-3 Stärken, Top-3 Schwächen
## Visuelle Analyse (Phase 2)
### Farbrad
### Schriftart-Tabelle
### Namens-Archetypen
### Tagline-Quadrant
## Positionierungs-Lücken
## Strategische Insights
## Nächster Schritt: /lumen-business-context
```

---

## Verbleibende offene Fragen für das Review

1. **Einzelne Datenpunkte:** Sind alle 123 inhaltlich korrekt? Fehlt etwas? Gib mir IDs, wo ich nachschärfen soll.
2. **Phase 2 Ablauf:** Sollen die 4 Module sequenziell oder parallel laufen? Meine Empfehlung: parallel, da alle unabhängig sind.
3. **Output-Format Phase 2:** SVG-Grafiken (automatisch generiert) oder Markdown-Tabellen? Meine Empfehlung: beides — Markdown für Lesbarkeit, SVG als Anhang für Präsentationen.
4. **Weitere Creative-Footprint-Module aus dem Enigma-Workshop** (Brand Deck, 7 Trigger Selbst-Positionierung, Golden Circle) sind in anderen LUMEN³-Skills abgedeckt (Skill 03, 04, 05) — nicht in Skill 00.

---

## Nächste Schritte nach Review-Freigabe

1. Skill 00 v2.0 neu schreiben (`skills/00-competitive-analysis.md`) mit Phase 1–4
2. `artefact-templates.md` Schema 00 um Phase-2-Sections erweitern
3. `methodology.md` um §6 ergänzen: Dietrich PESO (2014) + Enigma Creative Footprint (2022)
4. LUMEN3 Marketing Companion PDF an neue Skill-Realität anpassen (Kapitel II komplett neu)
5. Lizenz-Check der beiden GitHub-Repos und saubere Übernahme der nützlichen Bausteine (Python-Scripts, SEO-Checklisten)
