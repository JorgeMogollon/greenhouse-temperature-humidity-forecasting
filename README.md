# Greenhouse Temperature and Humidity Forecasting

Data, reproducible notebooks, figures, results, and metadata supporting the analysis and forecasting of greenhouse air temperature and relative humidity at multiple temporal resolutions and forecasting horizons.

> **Repository status:** Active development. The first archived Zenodo release and DOI will be added once the reproducible workflow is complete and the repository is made public.

## Overview

This repository provides the reproducible research materials associated with a greenhouse environmental time-series forecasting study.

The current workflow includes:

- sensor evaluation;
- validation of the original observations;
- temporal quality control;
- regularization to a uniform 4-minute time grid;
- generation of quality-control results and figures;
- preparation of datasets for subsequent forecasting analyses.

Additional forecasting stages will be progressively incorporated as they are completed and validated.

## Repository Structure

```text
greenhouse-temperature-humidity-forecasting/
├── data/
│   ├── raw/
│   │   └── greenhouse_sensor_data_raw.csv
│   └── processed/
│       ├── greenhouse_sensor_data_validated.csv
│       └── greenhouse_sensor_data_4min.csv
│
├── notebooks/
│   ├── 01_sensor_evaluation.ipynb
│   └── 02_quality_control_regularization.ipynb
│
├── figures/
│   ├── sensor_evaluation/
│   └── quality_control/
│
├── results/
│   ├── sensor_evaluation/
│   └── quality_control/
│
├── metadata/
│   └── 02_analysis_configuration.json
│
├── CITATION.cff
├── LICENSE
├── .gitignore
└── README.md
