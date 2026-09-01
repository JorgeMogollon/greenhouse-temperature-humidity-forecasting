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
│   │   ├── 01_sensor_agreement.png
│   │   └── 02_bme280_rh_saturation.png
│   └── quality_control/
│       ├── 01_monthly_target_coverage.png
│       └── 02_quality_controlled_targets.png
│
├── results/
│   ├── sensor_evaluation/
│   │   ├── 01_sensor_column_mapping.csv
│   │   ├── 02_general_audit.csv
│   │   ├── 03_sampling_interval_summary.csv
│   │   ├── 04_variable_coverage.csv
│   │   ├── 05_physical_range_audit.csv
│   │   ├── 06_sensor_agreement.csv
│   │   ├── 07_bme280_rh_quality.csv
│   │   └── 08_target_variable_selection.csv
│   └── quality_control/
│       ├── 01_timestamp_audit.csv
│       ├── 02_invalid_timestamps.csv
│       ├── 03_duplicate_timestamp_rows.csv
│       ├── 04_regularization_summary.csv
│       ├── 05_physical_range_audit.csv
│       ├── 06_interpolation_summary.csv
│       ├── 07_target_quality_status.csv
│       ├── 08_abrupt_change_summary.csv
│       ├── 09_final_file_validation.csv
│       └── 10_monthly_target_coverage.csv
│
├── metadata/
│   └── 02_analysis_configuration.json
│
├── CITATION.cff
├── LICENSE
├── LICENSE-DATA
├── .gitignore
└── README.md
