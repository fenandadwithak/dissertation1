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

The input dataset is `dataset per 31 december 2025 (used).RData`, containing daily flow and orthophosphate concentration records up to 31 December 2025 for the three catchments.

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
