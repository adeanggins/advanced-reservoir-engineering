# Advanced Reservoir Engineering Analytics in Python

[![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Domain](https://img.shields.io/badge/Domain-Oil_%26_Gas-black?style=for-the-badge&logo=oil)](https://www.spe.org/)

> **A comprehensive Python library for rigorous reservoir engineering analysis, implementing the workflows from Tarek Ahmed's "Advanced Reservoir Engineering".**

## 📌 Overview
This repository bridges the gap between traditional **Reservoir Engineering** and modern **Data Science**. It translates complex analytical physics-based models—typically found in expensive commercial software—into open-source, reproducible Python code.

The project demonstrates advanced competency in:
* **Physics-Based Modeling:** Material Balance, Aquifer Influx, and Well Testing.
* **Numerical Optimization:** Using `scipy.optimize` for history matching and curve fitting.
* **Differential Equations:** Solving Tarner’s and Muskat’s equations for performance prediction.
* **Economic Valuation:** Building Full-Cycle Discounted Cash Flow (DCF) models with Sensitivity Analysis.

---

## 📚 Repository Structure
The codebase is structured by engineering domain, mirroring the progression of a full-field study.

| Notebook / Module | Engineering Domain | Key Algorithms & Methods |
| :--- | :--- | :--- |
| **[01_Well_Testing_Analysis](notebooks/01_Well_Testing_Analysis.ipynb)** | Transient Flow | • Diffusivity Equation Visualization<br>• Horner Analysis ($k$, $s$, $P^*$)<br>• Derivative Type Curves (Bourdet)<br>• Superposition Principle |
| **[02_Water_Influx_Models](notebooks/02_Water_Influx_Models.ipynb)** | Aquifer Modeling | • Van Everdingen-Hurst (Infinite)<br>• Fetkovich (Finite)<br>• Carter-Tracy (Approximate)<br>• Linear & "Pot" Aquifers |
| **[03_Unconventional_Gas](notebooks/03_Unconventional_Gas_Reservoirs.ipynb)** | Non-Darcy Flow | • Langmuir Isotherms (CBM)<br>• Ramagost-Farshad $P/z$ Correction (Geopressure)<br>• Gas Hydrate Volumetrics<br>• Cole Plot Diagnostic |
| **[04_Material_Balance](notebooks/04_Oil_Reservoir_Performance_MBE.ipynb)** | Reservoir Drive | • General MBE ($F$ vs $\Sigma E$)<br>• Havlena-Odeh History Matching<br>• Drive Indices (DDI, SDI, WDI)<br>• Iterative Gas Cap ($m$) Solution |
| **[05_Performance_Prediction](notebooks/05_Performance_Prediction.ipynb)** | Forecasting | • Decline Curve Analysis (Arps)<br>• Tarner’s Method (Iterative Balance)<br>• Muskat’s Method (Differential ODE)<br>• Water Influx Coupling |
| **[06_Economics](notebooks/06_Oil_Field_Economics.ipynb)** | Valuation | • Discounted Cash Flow (DCF)<br>• NPV, IRR, Payback Period<br>• Fiscal Regimes (Tax/Royalty)<br>• Sensitivity Analysis (Spider Plots) |
| **[Capstone_Orion_Field](notebooks/Capstone_Orion_Field_Study.ipynb)** | **Full Field Study** | **Integrated workflow combining all chapters to simulate the lifecycle of the "Orion Field" from discovery to divestment.** |

---

## 🛠️ Technical Implementation Details

### 1. Advanced Material Balance (Havlena-Odeh)
Implemented the **General Material Balance Equation (GMBE)** as a Python class capable of handling variable pressure histories and multiple drive mechanisms.
```python
# Snippet: Calculating Withdrawal (F) vs Expansion (Et)
df['F'] = df['np'] * (df['bo'] + (df['rp'] - df['rs']) * df['bg']) + df['wp'] * df['bw']
df['Et'] = df['Eo'] + m * df['Eg'] + df['Efw']
# Optimization: Least-squares regression to find N (OIIP)
```

### 2. Numerical Integration for Prediction
Comparing Finite-Difference (Tarner) vs Differential (Muskat) methods to predict Solution-Gas Drive performance.

- Solver: Utilized scipy.optimize.brentq for robust root-finding in the iterative Tarner loop.

- Physics: Custom Relative Permeability and PVT correlations to capture non-linear fluid behavior.

### 3. Economic Sensitivity Analysis
Automated "Spider Plots" to visualize project risk.

- Dynamic Inputs: Function-based recalculation of NPV based on % variance in CAPEX, OPEX, and Price.

- Visualization: Matplotlib/Seaborn implementations for Waterfall charts and Sensitivity curves.
____
## 🚀 Getting Started
Prerequisites
- Python 3.8+

- Jupyter Lab or Notebook

Installation
1. Clone the repo

```Bash

git clone [https://github.com/yourusername/advanced-reservoir-engineering-python.git](https://github.com/yourusername/advanced-reservoir-engineering-python.git)
```
2. Install dependencies

```Bash

pip install -r requirements.txt
```
(Key libraries: numpy, pandas, matplotlib, scipy, numpy_financial)

3. Run the Capstone Launch `Capstone_Orion_Field_Study.ipynb` to see the full integrated workflow in action.
____
## 📬 Contact
Ade Anggi Naluriawan Santoso

Role: Data Scientist | Petroleum Engineer

Expertise: Reservoir Simulation, Python, Machine Learning, Economic Analysis

LinkedIn: https://www.linkedin.com/in/ade-anggi-naluriawan-santoso-83493a81/

Email: adeanggins@gmail.com
____
This repository is based on concepts from "Advanced Reservoir Engineering" by Tarek Ahmed and Paul D. McKinney. It is intended for educational and portfolio demonstration purposes.
