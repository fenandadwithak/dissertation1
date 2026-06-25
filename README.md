# Bayesian Time-Varying Load Apportionment Model
### Daily Prediction and Source Apportionment of Orthophosphate
**Thames, Trent, and Severn**

> Fenanda Dwitha Kurniasari (S2744048)

---

## Overview

This repository contains the R Markdown analysis for a Bayesian time-varying load apportionment model (LAM) that predicts daily orthophosphate concentrations and separates point-source from diffuse-source contributions across three major English river catchments: Thames, Trent, and Severn.

---

## Repository Structure

```
├── bayesian_LAM_vers(finale3).Rmd   # Main analysis script
├── bayesian_LAM_vers-finale3-.html  # Rendered output
├── dataset per 31 december 2025 (used).RData  # Input dataset
├── rds_file/                        # Pre-fitted model objects (brms)
├── output_img/                      # Saved figures
├── Journal and Literatures/         # References and literature
└── dissertation1.Rproj              # RStudio project file
```

---

## Data

The analysis uses two variables: daily orthophosphate concentration and daily river flow, covering 2000–2025 for the three catchments.

### Option 1 — Load from saved file (recommended)

A pre-downloaded dataset is provided in the repository:

```r
load("dataset per 31 december 2025 (used).RData")
```

This is the dataset used in the final analysis and is ready to use with no further setup.

### Option 2 — Pull fresh from API

If you want to re-download the raw data, uncomment the API block at the top of the script. This requires two custom import functions:

- `import_wq()` — fetches water quality concentration data (sourced from `import_wq_function.R`)
- `import_hde()` — fetches daily flow data (sourced from `import_hde_function.R`)

The following sites and determinands are queried over the period 2000-01-01 to 2025-12-31:

| Catchment | Concentration site | Flow site |
|---|---|---|
| Thames | TH-PTHR0107 (Teddington) | 3400TH |
| Severn | MD-00025085 (Haw Bridge) | 2606 |
| Trent | MD-36701570 (Dunham) | 4022 |

Determinand codes pulled: orthophosphate (0180), nitrate (0117), ammonia (0111), dissolved zinc (3408).

> **Note:** The API option requires a working connection to the data provider and may take some time to download the full 25-year record.

---

## Installation

Install all required packages before running the analysis:

```r
install.packages(c(
  "brms",
  "tidyverse",
  "posterior",
  "bayesplot",
  "tidybayes",
  "lubridate",
  "patchwork",
  "moments",
  "dplyr",
  "knitr"
))
```

Then load them at the top of the script:

```r
library(brms)
library(tidyverse)
library(posterior)
library(bayesplot)
library(tidybayes)
library(lubridate)
library(patchwork)
library(moments)
library(dplyr)
library(knitr)
```

> **Note:** `brms` requires a working Stan installation. See [mc-stan.org](https://mc-stan.org/users/interfaces/rstan) if you run into issues.

---

## Running the Analysis

### Option 1 — Use pre-fitted models (recommended)

Fitting the MCMC models from scratch is time-consuming. Pre-fitted `brms` model objects are saved as `.rds` files in the `rds_file/` folder. The script loads these directly:

```r
fit <- readRDS("rds_file/your_model.rds")
```

This skips the sampling step entirely and lets you reproduce all results and figures instantly.

### Option 2 — Refit from scratch

If you want to refit the models, set the fitting flag in the script to `TRUE`. Be aware this may take several hours depending on your machine.

---

## Output

- **HTML report:** `bayesian_LAM_vers-finale3-.html` — fully rendered analysis with tables, figures, and model summaries
- **Figures:** saved to `output_img/` as `.png` files

---

## References

Key papers and literature used in this study are available in the `Journal and Literatures/` folder.
