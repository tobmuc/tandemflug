# Tandemflug Voralpen – GitHub Page

One-Page-Website für Gleitschirm-Tandemflüge mit Buchungsformular, SEO und Google Analytics (mit Einwilligung).

Geplante Adresse: **https://tobmuc.github.io/tandemflug/** (Repository `tobmuc/tandemflug`)

## 1. Veröffentlichen

**Variante A – Upload im Browser (ohne Git)**
1. https://github.com/new → Name `tandemflug`, **Public**, ohne README → *Create repository*
2. *uploading an existing file* → den **Inhalt** dieses Ordners hineinziehen (inkl. `img/`, `fonts/`, `.nojekyll`) → *Commit changes*
3. *Settings → Pages → Build and deployment → Source: Deploy from a branch → Branch `main`, Ordner `/ (root)`* → *Save*
4. Nach 1–2 Minuten ist die Seite unter https://tobmuc.github.io/tandemflug/ online.

**Variante B – Git**
```bash
cd tandemflug-website
git init -b main && git add . && git commit -m "Tandemflug-Website"
git remote add origin https://github.com/tobmuc/tandemflug.git
git push -u origin main
```
Danach Pages wie in Schritt 3 aktivieren.

> Anderer Repo-Name oder eigene Domain? Dann die URL `https://tobmuc.github.io/tandemflug/` in `index.html` (Head + JSON-LD), `sitemap.xml`, `robots.txt` und die Pfade `/tandemflug/` in `404.html` ersetzen.

## 2. Anpassen

Alles Wichtige steht im Block `CONFIG` oben im `<script>` von `index.html`:

| Feld | Bedeutung |
|---|---|
| `email` | Empfänger der Anfragen |
| `web3formsKey` / `formspreeId` | Formular-Versand (kostenloser Key von web3forms.com). Ohne Key öffnet sich nur das Mailprogramm. |
| `gaId` | Google-Analytics-Mess-ID `G-…` (leer = kein Tracking, kein Banner) |
| `whatsapp` | Nummer ohne `+`, z. B. `4917612345678` (leer = ausgeblendet) |
| `price`, `weight` | Preis und Gewichtsbereich |
| `mountains` | Fluggebiete |
| `pilot` | Name, XContest-Link und Flugbuch-Zahlen (Sektion erscheint, sobald `stats` oder `years` gefüllt sind) |

## 3. Google Analytics 4

1. https://analytics.google.com → *Verwaltung → Property erstellen* → Datenstream **Web** mit `https://tobmuc.github.io/tandemflug/`
2. Mess-ID (`G-…`) in `CONFIG.gaId` eintragen und neu hochladen.
3. GA wird **erst nach Klick auf „Statistik erlauben"** geladen (DSGVO/TDDDG). Widerruf über „Cookie-Einstellungen" im Footer.
4. In GA unter *Datenaufbewahrung* 2 oder 14 Monate wählen und den Wert in `datenschutz.html` eintragen. Google-Signale ausgeschaltet lassen.
5. Mitgemessene Ereignisse:
   - `generate_lead` – Anfrage abgeschickt (in GA als **Schlüsselereignis** markieren)
   - `cta_click` – Klick auf „Flug anfragen" (mit Bereich)
   - `select_content` – „Hier fliegen" bei einem Fluggebiet
   - `contact_click` – E-Mail oder WhatsApp
   - `faq_open` – geöffnete FAQ-Frage

## 4. SEO

Schon eingebaut: Title und Description mit Keywords (Tandemflug, Gleitschirm, München, Bergnamen), Canonical, Open-Graph-Bild für WhatsApp/Facebook (`img/og-image.jpg`), strukturierte Daten (Service, Fluggebiete, FAQ), `sitemap.xml`, WebP-Bilder mit festen Maßen, lokal eingebundene Schriften, schnelle Ladezeit ohne externe Skripte.

Nach dem Livegang:
1. **Google Search Console** → Property „URL-Präfix" `https://tobmuc.github.io/tandemflug/` → Bestätigung per HTML-Tag (das `<meta name="google-site-verification" …>` in den `<head>` kopieren) → `sitemap.xml` einreichen.
2. **Google Unternehmensprofil** als Dienstleister mit Einzugsgebiet (Oberbayern/Tirol) anlegen und die Seite verlinken. Das bringt für lokale Suchen wie „Tandemflug München" meist mehr als jede Meta-Optimierung.
3. Optional eigene Domain (z. B. `tandemflug-…de`): *Settings → Pages → Custom domain*. Erst dann greift auch `robots.txt`.

## 5. Rechtliches

- `impressum.html` und `datenschutz.html` sind **Vorlagen**: gelb markierte Platzhalter ausfüllen. Kein Rechtsrat; im Zweifel mit einem Generator (z. B. e-recht24) oder Anwalt abgleichen.
- Personen auf den Fotos um Einverständnis zur Veröffentlichung fragen.
- Schrift: Inter (SIL Open Font License, siehe `fonts/OFL.txt`), lokal eingebunden – keine Verbindung zu Google Fonts.

## Struktur

```
index.html        Startseite
impressum.html    Impressum (Vorlage)
datenschutz.html  Datenschutzerklärung (Vorlage)
404.html          Fehlerseite
sitemap.xml, robots.txt, favicon.svg, .nojekyll
img/              Fotos (WebP + JPG), og-image.jpg, apple-touch-icon.png
fonts/            Inter (WOFF) + Lizenz
```
