# Interactive Solubility Calculator Website

A standalone, research-grade web application for predicting the solid–liquid equilibrium (SLE) solubility of organic solutes in diverse pure solvents and oils across multiple temperatures.

---

## 📁 Project Directory Location

All files for this project are located on your computer at:
```bash
/Users/abhishekkumar/.gemini/antigravity/scratch/solubility-calculator
```

---

## 🗂️ Files Included

1. **`index.html`**
   - Complete self-contained single-page application.
   - Includes full HTML5 markup, modern chemical-science CSS styling, responsive layout, and thermodynamic calculation engine in vanilla JavaScript.
   - Includes interactive Chart.js integration for Temperature vs. Solubility curves.

2. **`README.md`**
   - Documentation, theory explanation, and usage guide.

---

## 🚀 How to Run the Website

### Option 1: View Directly in Your Browser
Simply double-click or open `index.html` directly in any web browser:
```bash
open /Users/abhishekkumar/.gemini/antigravity/scratch/solubility-calculator/index.html
```

### Option 2: Run via Local Web Server (Recommended)
From your terminal:
```bash
cd /Users/abhishekkumar/.gemini/antigravity/scratch/solubility-calculator
python3 -m http.server 8000
```
Then navigate to:
```
http://localhost:8000/index.html
```

---

## 🔬 Scientific & Thermodynamic Overview

### Governing Solid–Liquid Equilibrium (SLE) Equation:
$$x_i \cdot \gamma_i(T, \mathbf{x}) = \exp\left[-\frac{\Delta H_{\text{fus}, i}}{R}\left(\frac{1}{T} - \frac{1}{T_{m, i}}\right)\right]$$

- **$x_i$**: Saturation mole fraction of solute $i$ in solution.
- **$\gamma_i$**: Activity coefficient of the solute in the liquid phase (accounting for non-ideal solute–solvent interactions).
- **$T$**: Operating temperature ($\text{K}$).
- **$T_{m, i}$**: Melting temperature of the solute ($\text{K}$).
- **$\Delta H_{\text{fus}, i}$**: Enthalpy of fusion ($\text{J}/\text{mol}$).
- **$R$**: Universal gas constant ($8.314462618\text{ J}/(\text{mol}\cdot\text{K})$).

### Key Features Implemented:
- **32 Pre-loaded Compounds**: Spices, flavor molecules, and pharmaceutical compounds with literature $T_m$ and $\Delta H_{\text{fus}}$.
- **25 Pre-loaded Solvents**: Polar, non-polar, and vegetable triglyceride oils.
- **Custom Solute & Solvent Support**: Add custom compounds with automatic validation and custom badging.
- **Multi-Solute Support**: Evaluate multiple solutes sequentially in the same solvent.
- **Multi-Temperature Evaluation**: Add and remove temperature points with independent unit conversions (°C and K).
- **Interactive Graph**: Real-time Temperature vs. Solubility curves with hover HUD tooltips and dynamic unit selectors.
- **Melting Point Detection**: Warns clearly if $T \ge T_m$ (liquid regime).
