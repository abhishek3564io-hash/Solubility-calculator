# Flavor Extraction & Solubility in Cooking Oils
## Code Package — README

---

## 🌐 Live Web Application
**GitHub Pages URL:** https://abhishek3564io-hash.github.io/Solubility-calculator/

**GitHub Repository:** https://github.com/abhishek3564io-hash/Solubility-calculator

---

## 📁 File Descriptions

| File | Description |
|------|-------------|
| `index.html` | Main interactive web application (HTML + CSS + JavaScript, single-file) |
| `solubility_analysis.ipynb` | Jupyter Notebook — thermodynamic parameter estimation and UNIFAC group analysis |
| `README.md` | This file |

---

## 🧪 Scientific Background

This project implements **Solid–Liquid Equilibrium (SLE)** thermodynamic modelling to predict the solubility of flavor compounds (spice bioactives) in cooking oils.

### Core Thermodynamic Model

The SLE equation used is:

```
ln(x_i · γ_i) = -(ΔH_fus / R) × (1/T − 1/T_m)
```

Where:
- `x_i` = mole fraction solubility of solute *i*
- `γ_i` = activity coefficient (accounts for non-ideal mixing)
- `ΔH_fus` = enthalpy of fusion (J/mol)
- `T_m` = melting point temperature (K)
- `T` = system temperature (K)
- `R` = 8.314 J/(mol·K)

### Activity Coefficient Model

A simplified Margules-type / UNIFAC-inspired model is used:

```
ln(γ_i) = A × (ΔδP)²
```

Where `ΔδP` is the polarity difference between solute functional groups and solvent, and `A` is a fitting parameter (default = 2.0).

### Calibrated Parameters (Flavor Compounds)

| Compound | T_m (K) | ΔH_fus (J/mol) | Group Polarity | Source |
|----------|---------|----------------|----------------|--------|
| Curcumin | 456.15 | 35,000 | 1.126 | Calibrated vs. experimental data |
| Capsaicin | 338.60 | 46,400 | 1.124 | Calibrated vs. experimental data |
| Piperine | 403.15 | 27,130 | 0.1 | Calibrated vs. experimental data |

**Calibration basis:** Experimental solubility data from Dey & Bhattacharya (2021) and Ngo et al. (2019). See `Data/` folder for validation comparison.

---

## 🗄️ Database Summary

### Solutes (32 compounds)
Flavor bioactives, pharmaceuticals, and reference compounds:
- **Spice compounds:** Curcumin, Capsaicin, Piperine, Zingerone, Thymol, Eugenol, Vanillin, Anethole, Cinnamaldehyde, Carvacrol, Linalool, Menthol, Limonene, γ-Terpinene
- **Pharmaceutical references:** Aspirin, Paracetamol, Ibuprofen, Caffeine, Cholesterol
- **Carboxylic acids:** Palmitic acid, Stearic acid, Benzoic acid, Salicylic acid
- **Others:** Naphthalene, Glucose, Sucrose, Urea, etc.

### Solvents (25 compounds)
- **Vegetable oils:** Soybean, Olive, Sunflower, Coconut, Palm, Groundnut
- **Organic solvents:** Ethanol, Methanol, Water, Hexane, Acetone, Ethyl acetate, Chloroform, DMF, DMSO, Toluene, Benzene, Diethyl ether, Cyclohexane, Isopropanol, Acetonitrile, THF, DCM, Propylene glycol, Glycerol

---

## 🚀 How to Run

### Option 1: Live Web Application (Recommended)
Visit: **https://abhishek3564io-hash.github.io/Solubility-calculator/**

No installation required. Works in any modern browser.

### Option 2: Run Locally
```bash
# Clone the repository
git clone https://github.com/abhishek3564io-hash/Solubility-calculator.git
cd Solubility-calculator

# Start a local server (Python 3)
python3 -m http.server 8000

# Open in browser
# → http://localhost:8000
```

### Option 3: Jupyter Notebook
```bash
# Install dependencies
pip install jupyter numpy pandas matplotlib

# Launch notebook
jupyter notebook solubility_analysis.ipynb
```

---

## 🖥️ Web Application Features

1. **Multi-Solute Selection** — Add up to 10 solutes simultaneously
2. **Multi-Solvent Support** — Select one or more solvents
3. **Temperature Range** — Set multiple temperatures (default: 298.15 K)
4. **Custom Solute Entry** — Input T_m, ΔH_fus, MW for custom compounds
5. **Interactive Graph** — Chart.js visualization with solubility vs. temperature curves
6. **Results Table** — Mole fraction, mg/g, g/100g solvent outputs
7. **Thermodynamic Properties Panel** — Shows γ, ln(γ), Δδ, and all SLE parameters
8. **Export** — Download results as CSV

---

## 📐 Calculation Workflow

```
1. User selects solute + solvent + temperature
2. Retrieve T_m, ΔH_fus, MW from SOLUTE_DB
3. Retrieve MW, polar from SOLVENT_DB
4. Calculate polarity mismatch: Δδ = GROUP_POLARITY[groups] − solvent.polar
5. Estimate ln(γ) = A × (Δδ)² using fitted A parameter
6. Apply bisection solver to find x_i satisfying SLE equation
7. Convert x_i to mg/g and g/100g using molecular weights
8. Repeat for all solute-solvent-temperature combinations
9. Plot and display results
```

---

## ⚠️ Known Limitations

- Activity coefficient model is simplified (not full UNIFAC)
- Vegetable oils approximated as average triglycerides
- No pressure dependence (assumed 1 atm)
- Liquid-phase non-ideality of solvent not modelled
- For T > T_m, compound is liquid — SLE does not apply; app displays note

---

## 📚 Key References

1. Prausnitz, J.M., Lichtenthaler, R.N., de Azevedo, E.G. (1986). *Molecular Thermodynamics of Fluid-Phase Equilibria*. Prentice Hall.
2. Fredenslund, A., Jones, R.L., Prausnitz, J.M. (1975). Group-contribution estimation of activity coefficients in nonideal liquid mixtures. *AIChE J.*, 21(6), 1086–1099.
3. Dey, T.K., Bhattacharya, S. (2021). Curcumin solubility in vegetable oils. *LWT Food Science and Technology*.
4. Ngo, T.V. et al. (2019). Capsaicin and piperine solubility in edible oils. *Food Chemistry*.

---

## 🏫 Project Information

**Course:** Chemical Engineering (Thermodynamics / Process Design)  
**Topic:** Flavor Extraction & Solubility in Cooking Oils  
**Web Portal:** https://abhishek3564io-hash.github.io/Solubility-calculator/  
**Repository:** https://github.com/abhishek3564io-hash/Solubility-calculator
