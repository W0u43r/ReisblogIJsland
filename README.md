# IJsland 2026 — Dagelijkse update checklist

Gebruik deze handleiding elke avond om de reisblog bij te werken.
Doe de stappen in volgorde — dan mis je niets.

---

## Overzicht van de mappenstructuur

```
ijsland-2026/
├── index.html              ← Hoofdpagina (overzicht van alle dagen)
├── README.md               ← Dit bestand
├── dag-01/
│   └── index.html          ← Dagpagina dag 1
├── dag-02/
│   └── index.html          ← Dagpagina dag 2
├── dag-03/
│   └── index.html          ← (nog aan te maken)
│   ...
└── images/
    ├── dag-01/             ← Foto's van dag 1
    ├── dag-02/             ← Foto's van dag 2
    └── dag-03/             ← (nog aan te maken)
```

---

## Stap-voor-stap: nieuwe dag publiceren

### Stap 1 — Foto's klaarzetten

1. Maak de map `images/dag-XX/` aan (bijv. `images/dag-03/`).
2. Zet de foto's van die dag daarin.
3. Gebruik korte bestandsnamen zonder spaties, bijv. `waterval.jpg` of `zonsondergang.jpg`.
4. **Tip:** verklein de foto's naar maximaal 1920px breed vóór upload — dit laadt veel sneller.

---

### Stap 2 — Nieuwe dagpagina aanmaken

1. Kopieer de map `dag-02/` en hernoem hem naar `dag-03/` (of het juiste nummer).
2. Open `dag-03/index.html` in een teksteditor.
3. Pas de volgende **8 plekken** aan (zoek op `AANPASSEN ❶` t/m `AANPASSEN ❽`):

| # | Wat aanpassen | Voorbeeld |
|---|---|---|
| ❶ | Browsertab-titel | `Dag 03 — Hvolsvöllur \| IJsland 2026` |
| ❷ | Navigatie: vorige/volgende dag-knoppen + paden | `← Dag 02` en `Dag 04 →` |
| ❸ | Hero: foto, dagnummer, datum, grote titel, intro-zin | zie hieronder |
| ❹ | Weerbalk: temperatuur, wind, zonsondergang, km gereden | actuele waarden invullen |
| ❺ | Hoogtepunten: 3–5 bullets van de dag | korte zinnen |
| ❻ | Verhaal: 3–5 alinea's + 1 pull-quote | schrijf in `<p>` tags |
| ❼ | Foto's: breed / paar / trio blokken + onderschriften | paden naar `../images/dag-03/` |
| ❽ | Dag-navigatie onderaan: titels en paden | vorige dag ← → volgende dag |

**Hero foto** (`AANPASSEN ❸`):
```html
<img class="day-hero-img"
  src="../images/dag-03/jouw-foto.jpg"
  alt="Korte beschrijving">
```

**Eerste dag (dag-01):** zet de "← Vorige dag"-knop op `disabled` (staat al zo in het sjabloon).  
**Laatste dag (dag-13):** zet de "Volgende dag →"-knop op `disabled`.

---

### Stap 3 — Foto's in de pagina plaatsen (`AANPASSEN ❼`)

Kies per blok de gewenste lay-out:

**A) Breed — één foto, volle breedte:**
```html
<div class="photo-hero-block" onclick="openLightbox(this.querySelector('img').src)">
  <img src="../images/dag-03/landschap.jpg" alt="Omschrijving">
</div>
<p class="photo-caption">Onderschrift hier</p>
```

**B) Paar — twee foto's naast elkaar:**
```html
<div class="photo-pair">
  <div class="photo-pair-item" onclick="openLightbox(this.querySelector('img').src)">
    <img src="../images/dag-03/foto-links.jpg" alt="Omschrijving">
  </div>
  <div class="photo-pair-item" onclick="openLightbox(this.querySelector('img').src)">
    <img src="../images/dag-03/foto-rechts.jpg" alt="Omschrijving">
  </div>
</div>
<p class="photo-caption">Links: naam · Rechts: naam</p>
```

**C) Trio — drie staande foto's naast elkaar:**
```html
<div class="photo-trio">
  <div class="photo-pair-item" onclick="openLightbox(this.querySelector('img').src)">
    <img src="../images/dag-03/staand-1.jpg" alt="Omschrijving">
  </div>
  <div class="photo-pair-item" onclick="openLightbox(this.querySelector('img').src)">
    <img src="../images/dag-03/staand-2.jpg" alt="Omschrijving">
  </div>
  <div class="photo-pair-item" onclick="openLightbox(this.querySelector('img').src)">
    <img src="../images/dag-03/staand-3.jpg" alt="Omschrijving">
  </div>
</div>
<p class="photo-caption">Onderschrift voor de drie foto's</p>
```

---

### Stap 4 — Hoofdpagina bijwerken (`index.html`)

Open `index.html` en doe de volgende 4 dingen:

#### 4a. Nieuwe dagkaart toevoegen in de dagboeken-sectie

Zoek het commentaar `NIEUW DAG-SJABLOON` (rond regel 200) en voeg **boven** het commentaar een nieuw kaartblok in:

```html
<a href="dag-03/index.html" class="day-card">
  <img class="day-card-img"
    src="https://images.unsplash.com/photo-XXXXXXX?w=800&q=80"
    alt="Korte beschrijving"
    loading="lazy">
  <div class="day-card-overlay"></div>
  <div class="day-card-content">
    <p class="day-card-number">Dag 03 · 22 April</p>
    <h3 class="day-card-title">Hvolsvöllur</h3>
    <p class="day-card-meta">
      <span class="day-card-status status-done"></span>Gepubliceerd
    </p>
  </div>
</a>
```

- Gebruik `status-done` voor een voltooide dag.
- Gebruik `status-live` + tekst `Nu live` voor de dag die je **nu** publiceert.
- Verander de vorige `status-live` dag naar `status-done` + `Gepubliceerd`.

#### 4b. Teller `PUBLISHED` ophogen

Zoek in het `<script>` blok onderaan `index.html`:
```javascript
const PUBLISHED = 2;
```
Verhoog het getal met 1 (dus `3`, `4`, etc.).

#### 4c. Nieuwe locatie toevoegen in `VISITED_PLACES`

Zoek het blok `const VISITED_PLACES = [` en verwijder de `//` commentaarslashes vóór de juiste dag:
```javascript
/* Dag 03 */ { dag:3, datum:'22 april', naam:'Hvolsvöllur', lat:63.7520, lng:-20.2209, svgX:281, svgY:425, isLive:true  },
```

- Zet de nieuwe dag op `isLive: true`.
- Zet de vorige dag terug op `isLive: false`.

#### 4d. Placeholder verwijderen uit `PLACEHOLDERS`

Zoek het blok `const PLACEHOLDERS = [` en verwijder de regel van de dag die je zojuist publiceerde:
```javascript
{ n:'03', datum:'22 April', titel:'Hvolsvöllur' },   // ← deze regel verwijderen
```

---

### Stap 5 — Controleren vóór publicatie

Open `index.html` lokaal in je browser en check:

- [ ] De countdown staat nog goed (of toont "We zijn onderweg")
- [ ] De nieuwe dagkaart verschijnt met de juiste foto en status
- [ ] Het grijze placeholder-vakje voor die dag is verdwenen
- [ ] De teller bovenaan de dagboeken-sectie klopt (`X van 13 gepubliceerd`)
- [ ] De kaart toont de nieuwe locatie met de groene pulserende stip
- [ ] De sidebar op de kaart toont de nieuwe locatie

Open de nieuwe dagpagina (`dag-03/index.html`) en check:

- [ ] Browsertab-titel is correct
- [ ] Vorige/volgende knoppen werken (klikken navigeert naar de juiste dag)
- [ ] Hero-foto laadt correct
- [ ] Weerbalk en hoogtepunten staan erin
- [ ] Foto's laden en lightbox werkt (klik op een foto)
- [ ] Navigatie onderaan verwijst naar de juiste buur-dagen

---

### Stap 6 — Publiceren naar GitHub Pages

```bash
git add .
git commit -m "Dag 03: Hvolsvöllur"
git push
```

Na een minuutje is de blog live op je GitHub Pages URL.

---

## Snelle referentie: statusklassen

| Klasse | Betekenis | Uiterlijk |
|---|---|---|
| `status-done` | Dag gepubliceerd | klein blauw bolletje |
| `status-live` | Huidige dag (vandaag) | groen pulserend bolletje |

Er is altijd **maximaal één** dag tegelijk `status-live`.

---

## Snelle referentie: coördinaten per dag

Alle coördinaten staan al klaar in `index.html` in het `VISITED_PLACES` blok.
Verwijder gewoon de `//` commentaarslashes bij de juiste dag.

| Dag | Locatie | lat | lng |
|---|---|---|---|
| 01 | Reykjavik | 64.1355 | -21.8954 |
| 02 | Úthlid | 64.2793 | -20.4440 |
| 03 | Hvolsvöllur | 63.7520 | -20.2209 |
| 04 | Kirkjubæjarklaustur | 63.7801 | -18.0898 |
| 05 | Höfn | 64.2497 | -15.2020 |
| 06 | Egilsstaðir | 65.2669 | -14.3949 |
| 07 | Mývatn | 65.5887 | -16.9903 |
| 08 | Mývatn | 65.5887 | -16.9903 |
| 09 | Hvammstangi | 65.3968 | -20.9394 |
| 10 | Ólafsvík | 64.8960 | -23.7060 |
| 11 | Borgarnes | 64.5609 | -21.9010 |
| 12 | Reykjavik | 64.1355 | -21.8954 |
| 13 | Terug naar huis | 64.1355 | -21.8954 |

---

## Veelgemaakte fouten

**Foto laadt niet** → controleer of het pad begint met `../images/dag-XX/` (met de `../` ervóór).

**Placeholder verdwijnt niet** → check of je de juiste regel hebt verwijderd uit het `PLACEHOLDERS` array in `index.html`.

**Kaart toont de locatie niet** → check of je de `//` commentaarslashes hebt verwijderd bij de juiste dag in `VISITED_PLACES`.

**Twee groene stippen op de kaart** → je bent vergeten de vorige dag terug te zetten op `isLive: false`.

**Dagkaart-teller klopt niet** → check of je `PUBLISHED` hebt opgehoogd in `index.html`.
