---
name: awt-content
description: >
  Content-Marketing-Orchestrator für AWT Finanz GmbH. Orchestriert
  Keyword-Recherche, Blog-Artikel-Erstellung und Newsletter-Workflows
  durch Kombination von claude-blog, seo-geo-claude-skills und marketingskills.
  Verwende diesen Skill wenn der Nutzer "awt-content", "blog schreiben",
  "keyword recherche", "newsletter erstellen", "artikel AWT", "content AWT",
  "Versicherung Blog" oder "Finanzierung Artikel" erwähnt.
user-invokable: true
argument-hint: "[keyword|blog|newsletter] <thema>"
metadata:
  version: "1.0.0"
  author: "AWT Finanz GmbH"
---

# AWT Content — Marketing-Orchestrator

Orchestriert drei Content-Workflows für AWT Finanz GmbH durch Kombination
von `claude-blog`, `seo-geo-claude-skills` und `marketingskills`.

## Schnellübersicht

| Befehl | Workflow |
|--------|----------|
| `/awt-content keyword <thema>` | Keyword-Recherche + Cluster-Strategie |
| `/awt-content blog <thema>` | Vollständiger Blog-Artikel (Brief → Outline → Artikel → SEO → GEO) |
| `/awt-content newsletter <thema>` | Newsletter / E-Mail-Sequenz |

---

## Erstkonfiguration (einmalig pro Projektordner)

Beim ersten Aufruf prüfen, ob `.agents/product-marketing-context.md` im
aktuellen Arbeitsverzeichnis vorhanden ist.

**Falls nicht vorhanden**, folgende Anleitung ausgeben:

> **Einmalige Einrichtung erforderlich:**
> Führe diesen Befehl im Terminal aus, um das AWT-Markenprofil in deinen
> Projektordner zu kopieren:
>
> ```bash
> mkdir -p .agents && cp ~/.claude/plugins/awt-content-skills/product-marketing-context.md .agents/product-marketing-context.md
> ```
>
> Danach den gewünschten `/awt-content`-Befehl erneut aufrufen.

**Falls vorhanden:** Datei einlesen und als Kontext für alle nachfolgenden Schritte nutzen.

---

## Befehlsrouting

1. Erstes Argument parsen: `keyword`, `blog` oder `newsletter`
2. Restliche Argumente = Thema / Seed-Keyword
3. Kein Argument → Nutzer fragen, welchen Workflow er starten möchte
4. Unbekanntes Argument → Schnellübersicht anzeigen

---

## Workflow 1: `/awt-content keyword <thema>`

**Zweck:** Keyword-Strategie für ein Thema aus dem Versicherungs- oder
Finanzierungsbereich entwickeln — priorisierte Keywords, Content-Lücken
und konkrete Artikelthemen für AWT.

### Eingaben sammeln (falls nicht im Thema enthalten)

| Parameter | Frage | Standard |
|-----------|-------|---------|
| Zielgruppe | Privatpersonen, Familien oder beides? | Privatpersonen & Familien |
| Ziel | Traffic aufbauen oder Leads generieren? | Leads |
| Konkurrenten | Bekannte Wettbewerber-Domains? | check24.de, interhyp.de |

### Schritte

**Schritt 1 — Keyword-Recherche**
```
/seo:keyword-research "<thema>"
```
Ergebnis: Keywords mit Suchvolumen, Schwierigkeit, Suchintent und Chance.

**Schritt 2 — AWT-Filterung**
Ergebnisse bewerten:
- Kommerzielle und informationelle Keywords bevorzugen
- YMYL-Keywords markieren (→ hohe E-E-A-T-Anforderungen im Artikel)
- Lokale Keywords hervorheben (Berlin, DACH)
- Regulierte Begriffe kennzeichnen ("Anlageberatung", "Garantiezins")

**Schritt 3 — Artikelvorschläge**
Aus den Top-Keywords 3–5 konkrete Artikelthemen für AWT ableiten:
- Welche Keywords als Blog-Artikel geeignet sind
- Welche für Newsletter-Themen passen
- Welche Pillar-Page-Potenzial haben

### Ausgabe

```
# Keyword-Report: [Thema]

## Top-Chancen (Schnelle Gewinne)
Keyword | Volumen | Schwierigkeit | Intent | Score

## Wachstums-Keywords
Keyword | Volumen | Schwierigkeit | Intent | Score

## YMYL-Keywords (hoher E-E-A-T-Bedarf)
[Liste mit redaktionellem Hinweis]

## Empfohlene Artikel-Themen für AWT
1. [Titel] — Keyword: [...], Typ: Ratgeber/Vergleich/How-To
2. ...

## Nächste Schritte
→ /awt-content blog "<empfohlener Titel>" — Artikel erstellen
→ /awt-content newsletter "<thema>" — Newsletter erstellen
```

---

## Workflow 2: `/awt-content blog <thema>`

**Zweck:** Vollständigen, SEO- und GEO-optimierten Blog-Artikel für AWT
Finanz GmbH erstellen — von Brief bis fertiger Artikel mit Qualitätsprüfung.

### Eingaben sammeln

| Parameter | Frage | Standard |
|-----------|-------|---------|
| Ziel-Keyword | Haupt-Keyword für den Artikel? | Aus Thema ableiten |
| Artikeltyp | Ratgeber, Vergleich, How-To, Listicle, FAQ? | Ratgeber |
| Wortanzahl | Gewünschte Länge? | 2000–2500 Wörter |
| Plattform | WordPress, HTML, Markdown? | Markdown |

### Schritte

**Schritt 1 — Content Brief**
```
/blog brief "<thema>"
```
Merken: Primär-Keyword, Sekundär-Keywords, empfohlenes Template, Wettbewerbs-Lücken.

**Schritt 2 — Gliederung**
```
/blog outline "<thema>"
```
Ergebnis: SERP-informierte H2/H3-Struktur.

**Schritt 3 — Artikel schreiben**
```
/blog write "<thema>"
```
Mit folgenden AWT-Vorgaben:
- Sprache: Deutsch, Sie-Form
- Zielgruppe: Privatpersonen und Familien in Berlin / DACH
- Markenstimme: professionell, beratend, vertrauenswürdig
- Gliederung aus Schritt 2 verwenden
- CTA am Ende: "Jetzt kostenlose Beratung buchen" + "Jetzt per WhatsApp schreiben"
- YMYL: Alle Zahlen und Fakten mit Quellenangabe
- Platzhalter `[INTERN: Thema]` für interne Verlinkungen setzen
- Pflicht-Disclaimer einfügen (siehe AWT-Regeln unten)

**Schritt 4 — SEO-Prüfung**
```
/blog seo-check <erstellte-datei>
```
Bei kritischen Fehlern → Artikel anpassen, dann weiter zu Schritt 5.

**Schritt 5 — GEO/AEO-Optimierung**
```
/blog geo <erstellte-datei>
```
Top-3-Empfehlungen zur KI-Zitierbarkeit einarbeiten.

**Schritt 6 — Schema-Markup** (optional, bei Artikeln mit FAQ)
```
/seo:generate-schema Article
```

### AWT-Pflichtregeln für jeden Artikel

1. **YMYL-Compliance:** Alle Zahlen, Zinssätze, gesetzliche Regelungen mit
   Quelle belegen (Bundesbank, BaFin, Stiftung Warentest, GDV).

2. **Pflicht-Disclaimer** am Ende des Artikels:
   > *Hinweis: Dieser Artikel dient der allgemeinen Information und ersetzt
   > keine individuelle Beratung. AWT Finanz GmbH ist zugelassener
   > Versicherungsmakler (§ 34d GewO). Für eine persönliche Einschätzung
   > stehen wir gerne zur Verfügung.*

3. **Keine konkreten Produktempfehlungen** ohne Beratungskontext.
   Korrekt: "Je nach Situation kann XY sinnvoll sein."
   Falsch: "Sie sollten XY abschließen."

4. **Doppelter CTA** am Artikelende:
   - Primär: "Jetzt kostenlose Beratung buchen" (Button/Link)
   - Sekundär: "Jetzt per WhatsApp schreiben" (WhatsApp-Link)

5. **Interne Links:** Platzhalter `[INTERN: Thema]` setzen, wo Links zu
   anderen AWT-Artikeln sinnvoll sind — nachträglich manuell ergänzen.

### Ausgabe

```
# Blog-Artikel: [Titel]

Status: Fertig / SEO-Korrekturen ausstehend / GEO-Korrekturen ausstehend
Datei: [dateiname.md]
Primär-Keyword: [...]
Wortanzahl: [...]
SEO-Score: [Zusammenfassung]
GEO-Score: [X/100]

---
[Vollständiger Artikel-Inhalt]
---

## Nächste Schritte
- [ ] Interne Links ergänzen (INTERN-Platzhalter suchen und ersetzen)
- [ ] Beitragsbild erstellen: /blog image generate "<thema>"
- [ ] Für Social Media aufbereiten: /blog repurpose <datei>
- [ ] Newsletter aus diesem Artikel: /awt-content newsletter "<thema>"
```

---

## Workflow 3: `/awt-content newsletter <thema>`

**Zweck:** Newsletter oder E-Mail-Sequenz für AWT-Kunden erstellen —
mit Betreff, Vorschautext, Inhalt und CTA.

### Eingaben sammeln

| Parameter | Frage | Standard |
|-----------|-------|---------|
| Typ | Einzel-Newsletter oder Sequenz (wie viele E-Mails)? | Einzel-Newsletter |
| Zielgruppe | Bestandskunden, neue Leads, Interessenten für Thema X? | Bestandskunden |
| Hauptbotschaft | Was soll der Leser erfahren oder tun? | Beratung buchen |
| Quell-Artikel | Gibt es einen Blog-Artikel als Basis? (Dateiname) | optional |
| Versandsystem | Mailchimp, CleverReach, ActiveCampaign, anderes? | Mailchimp |

### Schritte

**Schritt 1 — Markenkontext laden**
`.agents/product-marketing-context.md` einlesen.
AWT-Markenstimme, Zielgruppe und CTA als Basis für alle E-Mails.

**Schritt 2a — Einzel-Newsletter** (1 E-Mail)
`email-sequence`-Skill (marketingskills) mit folgendem Kontext:
- Typ: Einzel-Newsletter / monatlicher Ratgeber
- Zielgruppe: Privatpersonen und Familien, Berlin / DACH
- Branche: Versicherung und Finanzierung, AWT Finanz GmbH
- Ton: Professionell, beratend, Deutsch, Sie-Form
- Quell-Artikel falls vorhanden: zusammenfassen und als Basis nutzen

**Schritt 2b — E-Mail-Sequenz** (mehrere E-Mails)
`email-sequence`-Skill (marketingskills) mit AWT-Sequenzstruktur:
- E-Mail 1 (sofort): Thema einführen + konkreten Mehrwert liefern
- E-Mail 2 (Tag 2–3): Vertiefung + Beispiel oder Kundensituation
- E-Mail 3 (Tag 5–6): Einwände behandeln ("Brauche ich das wirklich?")
- E-Mail 4 (Tag 8–10): Sozialer Beweis + klare Handlungsaufforderung

**Schritt 3 — Betreffzeilen-Optimierung** (optional)
`ai-seo`-Skill (marketingskills) für KI-optimierte Betreffzeilen.

### AWT-Pflichtregeln für jeden Newsletter

1. **Betreffzeile:** Max. 50 Zeichen, nutzenorientiert.
   Bewährte Muster:
   - Frage: "Sind Sie richtig versichert?"
   - Zahl: "3 Fehler bei der Baufinanzierung"
   - Aktualität: "EZB senkt Zinsen — was das für Sie bedeutet"
   - Kfz-Saison: "Jetzt wechseln und bis zu X € sparen"

2. **Struktur jeder E-Mail:**
   Hook (1–2 Sätze) → Wert-Inhalt (150–250 Wörter) → Doppelter CTA

3. **Doppelter CTA** in jeder E-Mail:
   - Primär-Button: "Jetzt kostenlose Beratung vereinbaren"
   - Sekundär-Link: "Per WhatsApp schreiben"

4. **Pflichtabschluss:**
   ```
   Mit freundlichen Grüßen,
   Ihr Team von AWT Finanz GmbH | Berlin

   Zugelassener Versicherungsmakler (§ 34d GewO)
   [Abmelde-Link] | [Impressum] | [Datenschutz]
   ```

5. **DSGVO-Reminder:** E-Mails nur an Empfänger mit Double Opt-In senden.

### Ausgabe

```
# Newsletter: [Thema]

Typ: [Einzel / Sequenz X E-Mails]
Zielgruppe: [...]
Versandsystem: [...]

---
## E-Mail 1
Betreff: [...]
Vorschautext: [...]

[Vollständiger E-Mail-Inhalt]

CTA 1: [Beratung buchen] → [Link]
CTA 2: [WhatsApp] → [Link]

---
[Weitere E-Mails bei Sequenz]

## Versand-Checkliste
- [ ] Double Opt-In der Empfängerliste bestätigt
- [ ] Abmelde-Link eingefügt
- [ ] Impressum und Datenschutz verlinkt
- [ ] Test-E-Mail versendet
- [ ] Mobilansicht geprüft
```

---

## Qualitätssicherung (alle Workflows)

| Prüfpunkt | Anforderung |
|-----------|-------------|
| Sprache | Deutsch, korrekte Grammatik, Sie-Form |
| Quellenangaben | Alle Zahlen und Fakten belegt |
| YMYL-Compliance | Keine Produktempfehlungen ohne Disclaimer |
| Markenstimme | Professionell, beratend, vertrauenswürdig |
| CTA | Jeder Artikel und jede E-Mail: Beratung buchen + WhatsApp |
| Disclaimer | Haftungsausschluss wo erforderlich eingefügt |

---

## Weiterführende Befehle

Nach jedem Workflow sinnvolle Folgeschritte:

- `/blog repurpose <datei>` — Artikel für LinkedIn, Instagram, Facebook aufbereiten
- `/blog image generate "<thema>"` — Beitragsbild erstellen (Gemini API)
- `/seo:optimize-meta` — Title-Tag und Meta-Description optimieren
- `/seo:audit-page <datei>` — Vollständigen CORE-EEAT-Audit durchführen
- `/blog strategy Versicherung Berlin` — Gesamtstrategie für Themenbereich entwickeln
- `/blog calendar monthly` — Redaktionskalender für einen Monat erstellen
