# Greenhouse Temperature and Relative Humidity Forecasting

Data, reproducible Jupyter notebooks, preprocessing artifacts, figures, results, and metadata supporting multi-resolution and multi-horizon forecasting of greenhouse air temperature and relative humidity.

> **Repository status:** The complete computational workflow has been executed and its final validation outputs are included. Manuscript synchronization and preparation of the first public Zenodo release are in progress.

## Overview

This repository contains the reproducible research materials associated with a greenhouse environmental time-series forecasting study. It covers the complete workflow from sensor evaluation and temporal quality control to model-family benchmarking and paired statistical analysis.

The workflow includes:

- evaluation of the SHT31 and BME280 sensors;
- validation and selection of the target variables;
- regularization to a uniform 4-minute time grid;
- construction of multi-resolution datasets and common forecast origins;
- statistical reference and baseline models;
- machine-learning and deep-learning models;
- advanced traditional time-series models;
- a validation-gated robust residual hybrid strategy;
- final comparison of six model families;
- paired statistical analyses and article-ready figures.

## Study Design

The two forecasting targets are:

- greenhouse air temperature;
- greenhouse relative humidity.

Five temporal resolutions and four forecast horizons are evaluated:

- temporal resolutions: 4, 12, 20, 30, and 60 min;
- forecast horizons: 60, 120, 240, and 480 min.

The combination of five resolutions, four horizons, and two targets produces 40 forecasting tasks for each model family.

Chronological partitions are used throughout the workflow:

- training: March 22 to July 4, 2026;
- validation: July 5 to July 26, 2026;
- test: July 27 to August 19, 2026.

## Repository Structure

```text
greenhouse-temperature-humidity-forecasting/
├── data/
│   ├── raw/
│   └── processed/
│       ├── effective_indices/
│       ├── resolutions/
│       └── sample_indices/
├── figures/
│   ├── article/
│   └── model-family and preprocessing subdirectories/
├── metadata/
├── notebooks/
│   ├── 01_sensor_evaluation.ipynb
│   ├── 02_quality_control_regularization.ipynb
│   ├── 03_multiresolution_dataset.ipynb
│   ├── 04_baselines_statistical_models.ipynb
│   ├── 05_machine_learning_multihorizon.ipynb
│   ├── 06_deep_learning_multihorizon.ipynb
│   ├── 07_advanced_traditional_models.ipynb
│   ├── 08_robust_residual_hybrid.ipynb
│   ├── 09_final_model_family_benchmark.ipynb
│   └── 10_statistical_analysis_and_figures.ipynb
├── preprocessors/
│   └── deep_learning/
├── results/
│   ├── sensor_evaluation/
│   ├── quality_control/
│   ├── multiresolution/
│   ├── baselines_statistical/
│   ├── machine_learning/
│   ├── deep_learning/
│   ├── advanced_traditional/
│   ├── robust_residual_hybrid/
│   ├── final_benchmark/
│   └── statistical_analysis/
├── CITATION.cff
├── LICENSE
├── LICENSE-DATA
├── requirements.txt
├── .gitignore
└── README.md
```

Fitted model files are generated locally by the modeling notebooks and are not included in the current repository archive. The final tabular results, selected predictions, preprocessing objects, validation reports, and manuscript figures are included.

## Notebook Workflow

| Step | Notebook | Purpose |
|---:|---|---|
| 01 | [`01_sensor_evaluation.ipynb`](notebooks/01_sensor_evaluation.ipynb) | Sensor evaluation, agreement analysis, and target selection |
| 02 | [`02_quality_control_regularization.ipynb`](notebooks/02_quality_control_regularization.ipynb) | Temporal quality control and regularization to a 4-minute grid |
| 03 | [`03_multiresolution_dataset.ipynb`](notebooks/03_multiresolution_dataset.ipynb) | Multi-resolution datasets and reusable forecast-origin indices |
| 04 | [`04_baselines_statistical_models.ipynb`](notebooks/04_baselines_statistical_models.ipynb) | Operational references and statistical models |
| 05 | [`05_machine_learning_multihorizon.ipynb`](notebooks/05_machine_learning_multihorizon.ipynb) | Multi-horizon machine-learning evaluation |
| 06 | [`06_deep_learning_multihorizon.ipynb`](notebooks/06_deep_learning_multihorizon.ipynb) | Multi-seed deep-learning candidate evaluation and final predictions |
| 07 | [`07_advanced_traditional_models.ipynb`](notebooks/07_advanced_traditional_models.ipynb) | Advanced traditional time-series models |
| 08 | [`08_robust_residual_hybrid.ipynb`](notebooks/08_robust_residual_hybrid.ipynb) | Robust residual correction and validation-gated fallback strategy |
| 09 | [`09_final_model_family_benchmark.ipynb`](notebooks/09_final_model_family_benchmark.ipynb) | Final six-family benchmark and aggregate performance tables |
| 10 | [`10_statistical_analysis_and_figures.ipynb`](notebooks/10_statistical_analysis_and_figures.ipynb) | Friedman, Wilcoxon-Holm, bootstrap, Diebold-Mariano, and final figures |

Run the notebooks in ascending numerical order. Later notebooks require files generated by the preceding stages.

## Installation

The final workflow was executed with Python 3.13.9. Create an isolated environment and install the direct dependencies listed in `requirements.txt`.

Using Conda:

```bash
git clone https://github.com/JorgeMogollon/greenhouse-temperature-humidity-forecasting.git
cd greenhouse-temperature-humidity-forecasting

conda create --name greenhouse-forecasting python=3.13
conda activate greenhouse-forecasting

python -m pip install --upgrade pip
python -m pip install -r requirements.txt

jupyter lab
```

The repository currently pins package versions only when they were recorded in the final runtime metadata. The remaining entries in `requirements.txt` identify the direct dependencies imported by the notebooks.

## Execution Modes

Notebooks 06, 07, and 08 provide two execution modes:

- `smoke_test`: a short technical check of the pipeline;
- `full`: the complete analysis used to generate the final repository results.

Notebooks 09 and 10 use the `GREENHOUSE_EXECUTION_MODE` environment variable and default to `full` when the variable is not defined.

A smoke test confirms that the workflow runs, but it does not reproduce the complete manuscript-level results. Use `full` for final analyses.

## Reproducibility Principles

- All model families use common forecast origins within each temporal resolution.
- Training, validation, and test partitions are chronological.
- Hyperparameters, architectures, feature sets, and hybrid activation decisions are selected without using the test partition.
- Deep-learning candidates are evaluated across independent random seeds.
- Fitted scalers and imputers use only their corresponding fitting partitions.
- Notebook 09 verifies origin parity, observed-value parity, finite metrics, and exact fallback equivalence.
- Notebook 10 verifies the complete statistical panel and creation of the final figures.

A GPU is optional. TensorFlow can run on a CPU, although the full deep-learning evaluation may require substantially more time.

## Main Outputs

The principal final outputs are located in:

- `results/final_benchmark/`: selected family predictions, task metrics, rankings, and aggregate performance tables;
- `results/statistical_analysis/`: paired tests, bootstrap estimates, Diebold-Mariano contrasts, and validation summaries;
- `figures/article/`: article-ready PNG and PDF figures;
- `metadata/`: analysis configurations and runtime information.

The machine-readable validation files are:

- [`results/final_benchmark/11_output_validation.csv`](results/final_benchmark/11_output_validation.csv);
- [`results/statistical_analysis/13_output_validation.csv`](results/statistical_analysis/13_output_validation.csv).

## Licenses

Source code and Jupyter notebooks are distributed under the [MIT License](LICENSE).

Datasets, figures, tabular results, metadata, and related research outputs are distributed under the [Creative Commons Attribution 4.0 International License](LICENSE-DATA).

## Citation

Citation metadata are provided in [`CITATION.cff`](CITATION.cff).

After publication of the first versioned release, the archived Zenodo DOI will be added to this section and to the citation metadata.

## Repository

https://github.com/JorgeMogollon/greenhouse-temperature-humidity-forecasting
