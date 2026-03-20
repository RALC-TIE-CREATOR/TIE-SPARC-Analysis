# TIE SPARC Analysis

**Teoría de la Infraestructura Espacial (TIE)**  
Test Cuantitativo sobre el Catálogo SPARC — 135 Galaxias — Cero Parámetros Libres

[![ORCID](https://img.shields.io/badge/ORCID-0009--0008--4935--9010-A6CE39?logo=orcid)](https://orcid.org/0009-0008-4935-9010)
[![Zenodo](https://img.shields.io/badge/DOI-10.5281%2Fzenodo.19120085-blue)](https://zenodo.org/records/19120085)
[![License](https://img.shields.io/badge/License-Reproducibilidad_Científica-orange.svg)](LICENSE)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)

---

## Descripción

Script Python unificado que replica exactamente los tres módulos de análisis de la web TIE:

| Módulo | Herramienta web | Descripción |
|--------|----------------|-------------|
| **H-02** | [SPARC Explorer](https://ralc-tie-creator.github.io/sparc.html) | v_TIE vs v_obs para las 175 galaxias |
| **H-20** | [RMS Global](https://ralc-tie-creator.github.io/rms.html) | RMS, σ_dex, χ²r, sesgo — 135 galaxias |
| **H-06** | [Simulador RAR](https://ralc-tie-creator.github.io/simrar.html) | Relación Aceleración Radial — 135 galaxias |

**Una sola fuente de verdad.** Los tres módulos usan exactamente los mismos datos, fórmulas y constantes. Cero discrepancias posibles entre herramientas.

---

## Ecuaciones TIE (cero parámetros libres)

```
a₀     = c · H₀ / 2π = 1.082 × 10⁻¹⁰ m/s²   (derivado, no ajustado)
v_flat = (G · M_bar · a₀)^(1/4)               (velocidad plana asintótica)
a_bar  = v_flat⁴ / (G · M_bar)                (aceleración bariónica efectiva)
a_TIE  = √(a_bar · (a_bar + a₀))              (predicción RAR)
```

---

## Resultados

| Modelo | Parámetros libres | RMS (km/s) | σ (dex) | Veredicto |
|--------|:-----------------:|:----------:|:-------:|-----------|
| **TIE** | **0** | **29.3** | **0.0854** | ✓ Predicción |
| ΛCDM NFW | 2/galaxia | 35.0 | 0.101 | Ajuste de referencia |
| Newton puro | 0 | 185.5 | 0.175 | ✗ Falsificado |

**Submuestra Q=1 (87 galaxias de alta calidad):** σ_dex = 0.0589 dex

---

## Instalación

```bash
git clone https://github.com/RALC-TIE-CREATOR/TIE-SPARC-Analysis.git
cd TIE-SPARC-Analysis
pip install numpy matplotlib
```

Descargar el catálogo SPARC:
```bash
# Desde: http://astroweb.cwru.edu/SPARC/
# Archivo: Title_SPARC__I__Mass_Models_for_175.txt
```

---

## Uso

```bash
# Análisis completo (H-20 + H-06)
python TIE_SPARC_Analysis.py --sparc Title_SPARC__I__Mass_Models_for_175.txt

# Con gráficas
python TIE_SPARC_Analysis.py --sparc <archivo> --plot

# Solo alta calidad Q=1
python TIE_SPARC_Analysis.py --sparc <archivo> --quality 1

# Con tabla detallada H-02 por galaxia
python TIE_SPARC_Analysis.py --sparc <archivo> --sparc-detail

# Todo junto con gráficas en carpeta específica
python TIE_SPARC_Analysis.py --sparc <archivo> --plot --outdir ./figuras/
```

---

## Salida

El script genera automáticamente tres figuras:

| Archivo | Contenido |
|---------|-----------|
| `TIE_H02_H20_vflat.png` | v_TIE predicha vs v_obs observada (muestra completa + Q=1) |
| `TIE_H20_residuals.png` | Histograma de residuos log₁₀(v_TIE/v_obs) con gaussiana ajustada |
| `TIE_H06_RAR.png` | Relación de Aceleración Radial a_obs vs a_bar con curva TIE |

---

## Datos

**Catálogo SPARC:**  
Lelli, F., McGaugh, S.S. & Schombert, J.M. (2016). *SPARC: Mass Models for 175 Disk Galaxies with Spitzer Photometry and Accurate Rotation Curves*. AJ, 152, 157.  
→ http://astroweb.cwru.edu/SPARC/

**Nota:** El archivo del catálogo no está incluido en este repositorio por derechos de distribución. Descárgalo directamente desde la URL oficial.

---

## Reproducibilidad

Este script es la fuente de verdad de los resultados publicados en:

> Lecona, R. (R@LC). (2026). *135 Galaxies, Zero Free Parameters: A Quantitative Test of the Spatial Infrastructure Theory (TIE) Against the SPARC Catalogue*. Zenodo. DOI: [10.5281/zenodo.19120085](https://zenodo.org/records/19120085)

Los números del paper (RMS=29.3, σ=0.0854, N=135) son reproducibles ejecutando:
```bash
python TIE_SPARC_Analysis.py --sparc <archivo>
```

---

## Marco teórico

TIE es un tratado completo desarrollado por R@LC. La derivación formal de las ecuaciones, el Lagrangiano y los postulados se encuentran en:

- **Tratado completo (Amazon): https://www.amazon.com/dp/B0GR2113JR (Español) y https://www.amazon.co.uk/dp/B0GT8MNQ4F (Ingles)
- **Herramientas interactivas:** https://ralc-tie-creator.github.io  

---

## Licencia

Licencia de Reproducibilidad Científica — se permite ejecutar y citar con atribución.
Queda prohibido el uso comercial o la redistribución de versiones derivadas sin
autorización expresa del autor. El método analítico subyacente (Bisturí TIE) está
sujeto a proceso de registro de patente. Ver archivo [LICENSE](LICENSE) para detalles.

---

## Autor

**Rubén A. Lecona Curto (R@LC)**  
Investigador Independiente, México  
ORCID: [0009-0008-4935-9010](https://orcid.org/0009-0008-4935-9010)  
Email: ralc007@hotmail.com
