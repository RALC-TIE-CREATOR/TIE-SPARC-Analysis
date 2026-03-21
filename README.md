TIE Dark Matter Analysis
Theory of Spatial Infrastructure (TIE)
Dark Matter as a Missing Factor of 2π — 84.1% Fraction — Zero Free Parameters
Mostrar imagen
Mostrar imagen
Mostrar imagen
Mostrar imagen

Description
Paper and reproducible Python code demonstrating that the 84% of the universe labeled "dark matter" is a consequence of an omitted factor of 2π in the mass-energy relation. Within TIE, the real mass of any object is m_TIE = 2π · m_obs, yielding a dark fraction of exactly 1 − 1/2π = 84.1% — verified against Planck 2018 to 0.1%.
ModuleDescriptionPaperFull derivation + observational evidence + falsifiability conditionsVerificationPython script reproducing every numerical prediction in the paperTIE ModuleReusable Python class for all TIE calculations
One source of truth. All predictions use only four measured constants (G, c, H₀, ℏ). Zero discrepancies possible between code and paper.

TIE Equations (zero free parameters)
a₀     = c · H₀ / 2π = 1.082 × 10⁻¹⁰ m/s²     (derived, not fitted)
m_TIE  = 2π · m_obs                               (real mass of infrastructure)
f_dark = 1 − 1/2π = 84.1%                         (dark matter fraction)
v_flat = (G · M · a₀)^(1/4)                       (flat rotation velocity)
Λ_TIE  = 2H₀²/c² = 1.145 × 10⁻⁵² m⁻²           (cosmological constant)

Results
PredictionTIEObservedErrorDark matter fraction84.1%~84% (Planck 2018)0.1%Acceleration scale a₀1.082×10⁻¹⁰ m/s²~1.2×10⁻¹⁰ (McGaugh)~10%Cosmological constant Λ1.145×10⁻⁵² m⁻²1.0904×10⁻⁵² (Planck)5.0%GPS correction45.7 μs/day45.9 μs/day0.4%Mercury precession43.0″/century43.1 ± 0.5″/century0.3%Light deflection1.752″1.748 ± 0.006″ (VLBI)0.2%Cluster factor2π ≈ 6.28~6.67×6%SPARC σ_dex0.085 dexΛCDM NFW: 0.101 dexTIE betterBIC advantageΔBIC = 1324—TIE preferredFree parameters0ΛCDM: 6 + 270—

Installation
bashgit clone https://github.com/RALC-TIE-CREATOR/TIE-Dark-Matter.git
cd TIE-Dark-Matter/code
No external dependencies — uses only Python standard library (math).

Usage
bash# Full verification of all paper predictions
python TIE_Dark_Matter_Verification.py

# Use as a module
python -c "from TIE_constants import TIE; TIE.summary()"
Module examples
pythonfrom TIE_constants import TIE

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

Repository Structure
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

Falsifiability
TIE's dark matter prediction is falsifiable under four conditions:
#ConditionInstrumentStatus1Direct detection of a DM particle accounting for 84%XENON/LZ/PandaXAll null ✓2Baryon fraction ≠ 1/(2π) at >3σCMB-S4 / LiteBIRDPending3v_flat = (GMa₀)^(1/4) excluded at >3σSPARC / next-gen surveys0.085 dex ✓4Newton deviations at a_N ≫ a₀Precision ephemerisNone found ✓

Related Work
PaperDOIDescriptionTIE Treatise (Book)10.5281/zenodo.18851408Complete theory — 13 chapters, 16 predictionsSPARC Quantitative Test10.5281/zenodo.19120085135 galaxies, σ=0.085 dex, BIC>1300 vs ΛCDMThis paper10.5281/zenodo.XXXXXXXDark matter = missing factor of 2π

Reproducibility
This code is the source of truth for the results published in:

Lecona, R. (R@LC). (2026). Dark Matter as a Missing Factor of 2π: A Zero-Parameter Derivation from TIE. Zenodo. DOI: 10.5281/zenodo.XXXXXXX

All numbers in the paper are reproducible by running:
bashpython TIE_Dark_Matter_Verification.py

Theoretical Framework
TIE is a complete treatise developed by R@LC. The formal derivation of the equations, the Lagrangian, and the postulates can be found in:

Complete Treatise (Amazon): Spanish | English
Interactive Tools (20 modules): https://ralc-tie-creator.github.io


License
Scientific Reproducibility License — execution and citation with attribution are permitted.
Commercial use or redistribution of derived versions without express authorization
from the author is prohibited. The underlying analytical method (Bisturí TIE) is
subject to a patent registration process. See LICENSE file for details.

Author
Rubén A. Lecona Curto (R@LC)
Independent Researcher, México
ORCID: 0009-0008-4935-9010
Email: ralc007@hotmail.com
