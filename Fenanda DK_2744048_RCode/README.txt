BAYESIAN TIME-VARYING LOAD APPORTIONMENT MODEL
Daily Prediction and Source Apportionment of Orthophosphate
Thames, Trent, and Severn
Fenanda Dwitha Kurniasari (S2744048)

================================================================================
OVERVIEW
================================================================================
This project uses a Bayesian time-varying load apportionment model (LAM) to
predict daily orthophosphate concentrations and separate point-source from
diffuse-source contributions across three English river catchments:
Thames, Trent, and Severn.

================================================================================
FILES
================================================================================
bayesian_LAM_vers(finale3).Rmd       Main analysis script
bayesian_LAM_vers-finale3-.html      Rendered output
dataset per 31 december 2025.RData   Input dataset
rds_file/                            Pre-fitted brms model objects
output_img/                          Saved figures
Journal and Literatures/             References
dissertation1.Rproj                  RStudio project file

================================================================================
DATA (2000-2025)
================================================================================
Variables: daily orthophosphate concentration + daily river flow

Selected Sites:
  Thames  | Concentration: TH-PTHR0107 (Teddington) | Flow: 3400TH
  Severn  | Concentration: MD-00025085 (Haw Bridge)  | Flow: 2606
  Trent   | Concentration: MD-36701570 (Dunham)      | Flow: 4022

Determinands: orthophosphate (0180), nitrate (0117), ammonia (0111),
              dissolved zinc (3408)

Loading options:
  Option 1 (recommended) - load saved file:
    load("dataset per 31 december 2025 (used).RData")

  Option 2 - pull fresh from API:
    Uncomment the API block and use import_wq() and import_hde() functions.
    Requires a working connection to the data provider.

================================================================================
INSTALLATION PACKAGE
================================================================================
install.packages(c(
  "brms", "tidyverse", "posterior", "bayesplot", "tidybayes",
  "lubridate", "patchwork", "moments", "dplyr", "knitr"
))

Note: brms requires Stan. See https://mc-stan.org/users/interfaces/rstan

================================================================================
RUNNING THE ANALYSIS
================================================================================
Option 1 (recommended) - use pre-fitted models:
  Load .rds files from rds_file/ folder. Skips MCMC sampling entirely.
  fit <- readRDS("rds_file/your_model.rds")

Option 2 - refit from scratch:
  Set the fitting flag to TRUE in the script.
  Warning: may take several hours.

================================================================================
OUTPUT
================================================================================
- HTML report: bayesian_LAM_vers-finale3-.html
- Figures: saved as .png in output_img/
