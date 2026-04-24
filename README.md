# ⚡ Biogas Surplus Calculator

A free, open-source calculator for smallholder biogas farmers in East and Southern Africa. Enter your daily dung input and cooking use to see how much surplus gas you could put to work.

**Live demo:** [https://keepexploring.github.io/surplus-biogas/](https://keepexploring.github.io/surplus-biogas/)

---

## What it does

- Estimates daily biogas production from cow dung input (0.04 m³/kg, Gurung 1997 / SNV/BSP field data)
- Calculates cooking consumption for single or double stoves
- Shows daily and annual surplus
- Checks whether your digester is optimally loaded (for 6 m³, 8 m³, 12 m³ fixed dome digesters)
- Shows which productive use applications your surplus can power: chicken brooding, food drying, fodder chopping, water heating, lighting
- Prompts farmers to think beyond the three case study applications with open-ended idea cards

## Data sources

| Claim | Source |
|---|---|
| 0.04 m³ biogas per kg wet cow dung | Gurung, B. (1997). *Training Manual: Proper Utilisation of Bio-Slurry*. BSP/SNV. |
| Stove consumption 0.3 m³/hr (single) | SNV/BSP field programme standard |
| 30-day hydraulic retention time | Standard for mesophilic fixed dome digesters |
| Productive use consumption figures | Warnars, L. & Oppenoorth, H. (2014). *Bioslurry: A Supreme Fertiliser*. SNV/Hivos. |
| Digester loading ranges | SNV Africa Biogas Partnership Programme guidance |

## How to deploy to GitHub Pages (free hosting)

### Option A — Quickest (no Git knowledge needed)

1. Go to [github.com](https://github.com) and sign in (or create a free account)
2. Click **+** → **New repository**
3. Name it `biogas-calculator`, set to **Public**, click **Create repository**
4. Click **uploading an existing file**, drag in `index.html`, click **Commit changes**
5. Go to **Settings** → **Pages** → under *Source* select **main branch** → click **Save**
6. Your app will be live at `https://YOUR-USERNAME.github.io/biogas-calculator` within ~60 seconds

### Option B — Using Git

```bash
git clone https://github.com/YOUR-USERNAME/biogas-calculator.git
cd biogas-calculator
cp /path/to/index.html .
git add index.html
git commit -m "Add calculator"
git push origin main
```

Then enable GitHub Pages as in step 5 above.

### Option C — Fork this repository

If this repo is already public, just click **Fork** at the top right, then enable Pages in your fork's Settings.

---

## Customisation

All parameters are in the `<script>` section of `index.html`:

```js
const YIELD = 0.04;  // m³ biogas per kg wet cow dung — change for different feedstocks
```

To add a feedstock (e.g. pig dung at ~0.065 m³/kg):
1. Add a third toggle button alongside single/double stove
2. Adjust the `YIELD` constant per selection

To add a new productive use:
```js
const uses = [
  ...
  { name:"Your new use", icon:"🔧", need:1.5, needLabel:"1.5 m³/day", desc:"Description" },
];
```

To add a new digester size:
```js
const digesters = [
  ...
  { size:"16 m³", minLoad:45, maxLoad:65, prodMin:1.8, prodMax:2.6, livestock:"5–7 cattle" },
];
```

---

## Licence

MIT — free to use, adapt, and redistribute with attribution.

Built by [CREATIVenergie](https://www.creativenergie.co.uk) / CREATIVenergie.  
Field data from SNV, BSP, Gurung (1997), Warnars & Oppenoorth (2014).
