# RBC Estimation Project – Preprocessing of Ukrainian Macroeconomic Data

## Overview

This repository contains the preprocessing pipeline for Ukrainian macroeconomic data as part of the **DSGE/RBC estimation take-home project**. The goal of this stage is to collect, clean, and structure time series data required for estimating a basic Real Business Cycle (RBC) model using Python and the `gEconpy` package.

While the end goal of the project is to fit and simulate a DSGE model for Ukraine, this part focuses specifically on data sourcing, transformation, and preliminary diagnostics, as required by the first evaluation milestone (due Dec 11).

---

## 📁 Contents

The following key files are included:

- `Downloading Labor Data.ipynb`: 
  Notebook used to scrape, clean, and structure labour input (working hours) and wage data from `ukrstat.gov.ua`.
  
- `Working hours.csv`: 
  Quarterly working hours data (2018–2022), aggregated from monthly figures.

- `Average wages.csv`: 
  Quarterly average nominal wage data for the Ukrainian economy (2018–2023).

- `Interest_rate_processed.csv`: 
  Processed central bank policy rate from the National Bank of Ukraine, adjusted to quarterly compounded terms.

- `Bonds_processed.csv`: 
  Daily volumes of government bond sales (USD), resampled and ready for quarterly aggregation.

- `NBU_interest_rates.xlsx`, `bonds_USD.xlsx`, etc.: 
  Raw data downloaded from the National Bank of Ukraine.

- `WB and Fred Processed.ipynb`: 
  Notebook that pulls data from World Bank and FRED APIs including GDP, consumption, investment, capital stock, exports, and imports.

- `Ukraine_RBC.ipynb`: *(to be added)* Notebook implementing the RBC model in `gEconpy`.

---

## 📊 Preprocessed Variables

The data preprocessing includes the following macroeconomic series:

| Variable | Source | Frequency | Notes |
|----------|--------|-----------|-------|
| GDP (`Y`) | World Bank | Annual → Quarterly | Real GDP (constant prices) |
| Consumption (`C`) | World Bank | Annual → Quarterly | Current prices |
| Investment (`I`) | World Bank | Annual → Quarterly | Current prices |
| Capital Stock (`K`) | FRED | Annual → Quarterly | Real capital stock (2017 USD) |
| Employment / Hours Worked (`N`) | Ukrstat | Monthly → Quarterly | Cleaned, renamed, and aggregated |
| Wage (`w`) | Ukrstat | Quarterly | Nominal wage, log-transformed |
| Interest Rate (`r`) | NBU | Daily → Quarterly | Compounded quarterly |
| Bonds (`B`) | NBU | Daily → Quarterly | Volumes at par in USD |

All series are logged (if applicable), de-trended, and tested for stationarity using the Augmented Dickey-Fuller (ADF) test.

---

## 🔧 Tools & Technologies

- Python 3.11+
- Jupyter Notebook
- `pandas`, `numpy`, `matplotlib`, `statsmodels`
- `gEconpy` for DSGE simulation
- World Bank and FRED API (via `pandas_datareader`)
- Excel and .zip parsers (`openpyxl`, `xlrd`)

---

## 🧪 Preprocessing Pipeline Highlights

- Renaming bilingual Ukrainian-English column headers
- Monthly to quarterly aggregation (sum for hours, mean for rates)
- Consistent datetime indexing
- Log-transformation and stationarity checks
- Export to `.csv` for direct use in DSGE estimation

---


