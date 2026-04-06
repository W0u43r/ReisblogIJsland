# IJsland Reisblog — Setup Handleiding

Een cinematische reisblog voor GitHub Pages. Donker thema, aurora-sfeer, cinematic foto's.

## Structuur

```
/
├── index.html          ← Landingspagina (overzicht + kaart + countdown)
├── dag-01/
│   └── index.html      ← Dag 1 pagina (volledig ingevuld als voorbeeld)
├── dag-02/
│   └── index.html      ← Kopieer dag-01 en pas aan
└── README.md
```

---

## 1. GitHub Pages activeren

1. Maak een nieuwe GitHub repository aan: `gebruikersnaam/ijsland-2025` (of eigen naam)
2. Push alle bestanden naar de `main` branch
3. Ga naar **Settings → Pages → Source: Deploy from branch → main → / (root)**
4. Je site is bereikbaar op: `https://gebruikersnaam.github.io/ijsland-2025/`

---

## 2. Countdown instellen

Open `index.html` en zoek deze regel:

```js
const DEPARTURE = new Date('2025-07-12T08:00:00');
```

Verander de datum naar jouw vertrekdatum.

---

## 3. Reacties instellen via Giscus (gratis)

Giscus gebruikt GitHub Discussions als backend. Volledig gratis.

### Eenmalige setup:
1. Zorg dat je repo **public** is (vereist voor Giscus)
2. Activeer **Discussions** in je repo: Settings → Features → ✅ Discussions
3. Installeer de Giscus app: https://github.com/apps/giscus → geef toegang aan je repo
4. Ga naar https://giscus.app/
5. Vul je repo in (bijv. `gebruikersnaam/ijsland-2025`)
6. Kies mapping: **pathname** (elke dagpagina krijgt eigen discussie)
7. Kopieer het gegenereerde `<script>` tag

### Per dagpagina:
Vervang dit blok in elke `dag-XX/index.html`:

```html
<!-- Plak hier jouw giscus <script> tag -->
<div class="giscus"></div>
```

Door:

```html
<script src="https://giscus.app/client.js"
  data-repo="gebruikersnaam/ijsland-2025"
  data-repo-id="JOUW_REPO_ID"
  data-category="Announcements"
  data-category-id="JOUW_CATEGORY_ID"
  data-mapping="pathname"
  data-strict="0"
  data-reactions-enabled="1"
  data-emit-metadata="0"
  data-input-position="bottom"
  data-theme="dark"
  data-lang="nl"
  crossorigin="anonymous"
  async>
</script>
<div class="giscus"></div>
```

---

## 4. Nieuwe dag toevoegen

1. Kopieer de map `dag-01/` naar `dag-02/`, `dag-03/`, etc.
2. Open het nieuwe `index.html` en pas aan:
   - `<title>` → "Dag 02 — De Gouden Cirkel | IJsland MMXXV"
   - `dag-number-badge` → "Dag 02"
   - `day-date` → de juiste datum
   - `day-hero-title` → naam van de dag
   - `day-hero-intro` → intro tekst
   - Weergegevens in de weather-bar
   - Highlights
   - De tekst in `<article class="day-content">`
   - De foto's (vervang de Unsplash URLs door jouw eigen foto-URLs)
   - Navigatieknoppen (vorige/volgende dag links)

3. Open `index.html` (de hoofdpagina):
   - Verander de day-card van `dag-02` van placeholder naar een echte card (kopieer het format van dag-01 card)
   - Update de teller: "2 van 14 gepubliceerd"

4. Commit en push naar GitHub → de site update automatisch.

---

## 5. Foto's hosten

**Optie A — In de repo zelf (eenvoudigst):**
- Maak een map `/fotos/dag-01/` aan
- Zet je foto's erin (geoptimaliseerd: max 800KB per foto, JPEG kwaliteit 80%)
- Verwijs ernaar: `src="../fotos/dag-01/foto1.jpg"`
- Gratis, maar repo wordt groot bij veel foto's

**Optie B — Cloudinary (gratis, aanbevolen voor veel foto's):**
- Maak gratis account op cloudinary.com
- Upload foto's → kopieer de URL
- Bonus: Cloudinary verkleint automatisch: voeg `w_1400,q_80` toe aan de URL

**Foto's optimaliseren voor web:**
- Gebruik https://squoosh.app/ (gratis, browser-based)
- Aanbevolen: breedte 1400px, JPEG kwaliteit 80%

---

## 6. Eigen naam/namen invullen

Zoek in `index.html` naar:
```
Wij zijn [Namen]
```
En vervang door jullie eigen namen.

---

## Handige tools

| Tool | Gebruik | Link |
|------|---------|------|
| Squoosh | Foto's optimaliseren | squoosh.app |
| Giscus | Reacties | giscus.app |
| Cloudinary | Foto's hosten | cloudinary.com |
| GitHub Pages | Website hosten | pages.github.com |

---

## Tip: workflow tijdens de reis

1. Schrijf je dagverhaal in een notitie-app (bijv. Apple Notes of Google Keep)
2. Selecteer 2-3 beste foto's, optimaliseer ze via Squoosh
3. Open `dag-XX/index.html` op je laptop, plak tekst en foto-links in
4. Commit en push via GitHub Desktop (of de GitHub app op je telefoon)
5. Binnen 1 minuut staat het live
