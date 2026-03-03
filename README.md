# ⚙️ Cruisin Craftsmen Mechanic – Berekentool

Deze tool is gemaakt voor **aankoop & recycling van materialen**.  
Het draait via **GitHub Pages** zodat iedereen hem eenvoudig kan gebruiken in de browser.

---

## 📂 Bestandsstructuur

- `index.html` → bevat **HTML + CSS + JavaScript** (alles-in-één bestand).  
- `logo.png` → logo dat in de header wordt getoond.  

---

## 🔧 Aanpassen van items & prijzen

### 1. Visuele rij toevoegen (HTML)
In de juiste `<div class="grid">`-sectie een nieuwe rij toevoegen:

```html
<div><label for="hout">Hout</label><div class="price">€15 / stuk</div></div>
<div><input id="hout" type="number" min="0" value="0"></div>
<div class="sub">€<span id="sub-hout">0</span></div>
```
Let op:

for="hout", id="hout" en id="sub-hout" moeten overeenkomen.

### 2. Prijs toevoegen (JS)
Zoek naar het blok:

```js
const PRICES = {
  aankoop: { ... },
  recycling: { ... }
};
```
Voeg daar je item + prijs toe, bv.:
```js
hout: 15
```

### 3. Mooie naam in overzicht (JS)
Zoek naar:
```js
const LABELS = { ... };
```
Voeg toe:
```js
hout: "Hout",
```

### 4. Manager-goedkeuring (optioneel)
Items die manager approval vereisen, staan in:
```js
const restrictedIds = ["plastic","glas","koper"];
```
Wil je dat een nieuw item ook goedkeuring nodig heeft → voeg hem hier toe.

🎨 Styling aanpassen

Alles zit bovenaan in <style>:

```css
body { background: #1e1e1e; color: #FEFEF3; } // Achtergrond
.primary { background: #A82B2D; } //  Primair (bereken) knop
.ghost { background: #444; } // Ghost knoppen (reset/kopieer)
.price { color: #bbb; } // Prijslabels subtiel
```
Logo aanpassen? → vervang logo.png.

💬 Kopieerknoppen aanpassen
Bericht naar klant

Zoek naar
```js
const messages = [ ... ];
```
- Hier staan 10 varianten van het klantbericht.
- Je kan teksten toevoegen of aanpassen.
- De knop kiest steeds een random bericht.

Totaal kopiëren

Laat dit onaangeroerd.
Het verwijdert puntjes (.) zodat FiveM-telefoon het bedrag goed accepteert:

```js
const clean = bedrag.replace(/\./g, '');
```

⌨️ Extra functies

- Enter in een inputveld = automatisch berekenen van die sectie.
- Reset alles = zet alle velden en tabellen terug op 0.

🌐 Publiceren via GitHub Pages

1 Push index.html (en logo.png) naar de main branch.
2 In repo → Settings → Pages → Build from branch → main (/root).
3 URL: https://<username>.github.io/<repo>/
4 Elke commit update de site (kan ±1 minuut duren).

🛠️ Troubleshooting

- 0,00 verschijnt → vervang hardcoded waarden door 0.
- Totaal kopieert met puntjes → check replace(/\./g, '') in de copy-handler.
- Nieuwe items tellen niet mee → check of ze in PRICES én in LABELS zijn toegevoegd.
