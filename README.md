# TIE Dark Matter Analysis 
 
**Theory of Spatial Infrastructure (TIE)**  
Dark Matter as a Missing Factor of 2π — 84.1% Fraction — Zero Free Parameters
 
[![ORCID](https://img.shields.io/badge/ORCID-0009--0008--4935--9010-A6CE39?logo=orcid)](https://orcid.org/0009-0008-4935-9010)
[![Zenodo](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.19120084-blue)](https://zenodo.org/records/XXXXXXX)
[![License](https://img.shields.io/badge/License-Scientific_Reproducibility-orange.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)
 
---
 
## Description
 
Paper and reproducible Python code demonstrating that the 84% of the universe labeled "dark matter" is a consequence of an omitted factor of 2π in the mass-energy relation. Within TIE, the real mass of any object is m_TIE = 2π · m_obs, yielding a dark fraction of exactly 1 − 1/2π = 84.1% — verified against Planck 2018 to 0.1%.
 
| Module | Description |
|--------|-------------|
| **Paper** | Full derivation + observational evidence + falsifiability conditions |
| **Verification** | Python script reproducing every numerical prediction in the paper |
| **TIE Module** | Reusable Python class for all TIE calculations |
 
**One source of truth.** All predictions use only four measured constants (G, c, H₀, ℏ). Zero discrepancies possible between code and paper.
 
---
 
## TIE Equations (zero free parameters)
 
```
a₀     = c · H₀ / 2π = 1.082 × 10⁻¹⁰ m/s²     (derived, not fitted)
m_TIE  = 2π · m_obs                               (real mass of infrastructure)
f_dark = 1 − 1/2π = 84.1%                         (dark matter fraction)
v_flat = (G · M · a₀)^(1/4)                       (flat rotation velocity)
Λ_TIE  = 2H₀²/c² = 1.145 × 10⁻⁵² m⁻²           (cosmological constant)
```
 
---
 
## Results
 
| Prediction | TIE | Observed | Error |
|---|---|---|---|
| Dark matter fraction | 84.1% | ~84% (Planck 2018) | 0.1% |
| Acceleration scale a₀ | 1.082×10⁻¹⁰ m/s² | ~1.2×10⁻¹⁰ (McGaugh) | ~10% |
| Cosmological constant Λ | 1.145×10⁻⁵² m⁻² | 1.0904×10⁻⁵² (Planck) | 5.0% |
| GPS correction | 45.7 μs/day | 45.9 μs/day | 0.4% |
| Mercury precession | 43.0″/century | 43.1 ± 0.5″/century | 0.3% |
| Light deflection | 1.752″ | 1.748 ± 0.006″ (VLBI) | 0.2% |
| Cluster factor | 2π ≈ 6.28 | ~6.67× | 6% |
| SPARC σ_dex | 0.085 dex | ΛCDM NFW: 0.101 dex | TIE better |
| BIC advantage | ΔBIC = 1324 | — | TIE preferred |
| **Free parameters** | **0** | **ΛCDM: 6 + 270** | **—** |
 
---
 
## Installation
 
```bash
git clone https://github.com/RALC-TIE-CREATOR/TIE-Dark-Matter.git
cd TIE-Dark-Matter/code
```
 
No external dependencies — uses only Python standard library (`math`).
 
---
 
## Usage
 
```bash
# Full verification of all paper predictions
python TIE_Dark_Matter_Verification.py
 
# Use as a module
python -c "from TIE_constants import TIE; TIE.summary()"
```
 
### Module examples
 
```python
from TIE_constants import TIE
 
# Dark matter fraction
print(f"Dark fraction: {TIE.f_dark:.4f}")        # 0.8408
 
# Flat rotation velocity for a galaxy (solar masses → km/s)
print(f"v_flat: {TIE.v_flat_solar(5e10):.1f} km/s")
 
# Cosmological constant
print(f"Λ_TIE = {TIE.Lambda:.3e} m⁻²")
 
# TIE acceleration at 20 kpc from 5×10¹⁰ M☉
r = 20 * TIE.kpc
M = 5e10 * TIE.M_sun
print(f"a_TIE = {TIE.a_TIE(M, r):.3e} m/s²")
 
# Black hole horizon (M87*)
M87 = 6.5e9 * TIE.M_sun
print(f"r_h = {TIE.r_horizon_TIE(M87)/1e3:.2e} km")   # 1.14×10¹⁷ km
print(f"r_s = {TIE.r_schwarzschild(M87)/1e3:.2e} km")   # 1.92×10¹⁰ km
```
 
---
 
## Repository Structure
 
```
TIE-Dark-Matter/
├── README.md                              # This file
├── LICENSE                                # Scientific Reproducibility License
├── CITATION.cff                           # Citation metadata
├── paper/
│   └── TIE_Dark_Matter_Paper_EN.docx      # Paper (English)
├── code/
│   ├── TIE_Dark_Matter_Verification.py    # Full verification script
│   ├── TIE_constants.py                   # Reusable TIE module
│   └── requirements.txt                   # No external dependencies
├── data/
│   └── planck_2018_values.json            # Reference observational values
└── figures/                               # Plots (planned)
```
 
---
 
## Falsifiability
 
TIE's dark matter prediction is falsifiable under four conditions:
 
| # | Condition | Instrument | Status |
|---|---|---|---|
| 1 | Direct detection of a DM particle accounting for 84% | XENON/LZ/PandaX | All null ✓ |
| 2 | Baryon fraction ≠ 1/(2π) at >3σ | CMB-S4 / LiteBIRD | Pending |
| 3 | v_flat = (GMa₀)^(1/4) excluded at >3σ | SPARC / next-gen surveys | 0.085 dex ✓ |
| 4 | Newton deviations at a_N ≫ a₀ | Precision ephemeris | None found ✓ |
 
---
 
## Related Work
 
| Paper | DOI | Description |
|---|---|---|
| TIE Treatise (Book) | [R@LC: Theory of Spatial Infrastructure (TIE): Unification of the Four Fundamental Forces through Elimination of Artificial T2 and Zero Free Parameters](https://www.amazon.co.uk/dp/B0GT8MNQ4F) | Complete theory — 13 chapters, 16 predictions |
| SPARC Quantitative Test | [10.5281/zenodo.19120085](https://doi.org/10.5281/zenodo.19120085) | 135 galaxies, σ=0.085 dex, BIC>1300 vs ΛCDM |
| **This paper** | [10.5281/zenodo.19120084](https://doi.org/10.5281/zenodo.19120084) | Dark matter = missing factor of 2π |
 
---
 
## Reproducibility
 
This code is the source of truth for the results published in:
 
> Lecona, R. (R@LC). (2026). *Dark Matter as a Missing Factor of 2π: A Zero-Parameter Derivation from TIE*. Zenodo. DOI: [10.5281/zenodo.19143650] 
All numbers in the paper are reproducible by running:
```bash
python TIE_Dark_Matter_Verification.py
```
 
---
 
## Theoretical Framework
 
TIE is a complete treatise developed by R@LC. The formal derivation of the equations, the Lagrangian, and the postulates can be found in:
 
- **Complete Treatise (Amazon):** [Spanish](https://www.amazon.com/dp/B0GR2113JR) | [English](https://www.amazon.co.uk/dp/B0GT8MNQ4F)
- **Interactive Tools (20 modules):** https://ralc-tie-creator.github.io
 
---
 
## License
 
Scientific Reproducibility License — execution and citation with attribution are permitted.
Commercial use or redistribution of derived versions without express authorization
from the author is prohibited. The underlying analytical method (Bisturí TIE) is
subject to a patent registration process. See [LICENSE](LICENSE) file for details.
 
---
 
## Author
 
**Rubén A. Lecona Curto (R@LC)**  
Independent Researcher, México  
ORCID: [0009-0008-4935-9010](https://orcid.org/0009-0008-4935-9010)  
Email: ralc007@hotmail.com
