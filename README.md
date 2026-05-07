# COVID-19 Modelling Code for Thuringia

![Zenodo DOI](https://zenodo.org/badge/1052558399.svg)

This repository contains the code and data files used to reproduce the modelling results for the manuscript submitted to PLOS ONE. It includes the final reproducibility files: eight Julia notebooks, five CSV data files, and the Julia project environment.

## Tracked Files

The repository contains the following files:

```text
.gitignore
1-MainModel.ipynb
2-AgeBasedModel.ipynb
3-WeeklyProjection.ipynb
4-CoefficientAdjustment.ipynb
5-Lockdown.ipynb
6-LowCasesScenario.ipynb
7-SindySmoothingSensitivity.ipynb
8-SindyConvolutionSensitivity.ipynb
Manifest.toml
Project.toml
Thuringen-SIRD-Grouped-2.csv
Thuringen_SIRD_2.csv
Thuringen_SIRD_raw_2.csv
Thuringen_agegroup_vaccination.csv
Thuringen_daily_vaccination.csv
```

## Notebooks

Run the numbered notebooks from top to bottom. Each notebook is intended to reproduce a specific part of the paper.

| File                                  | Purpose                                                                                                                | Paper output               |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| `1-MainModel.ipynb`                   | Main SINDy model without coefficient optimisation; includes ICU and hospitalisation calculations and MCMC diagnostics. | Figures 3, 4, 6, 7, 15     |
| `2-AgeBasedModel.ipynb`               | Age-based SINDy model and vaccination scenarios.                                                                       | Figures 2, 8               |
| `3-WeeklyProjection.ipynb`            | Weekly projection examples for different prediction windows.                                                           | Figure 5                   |
| `4-CoefficientAdjustment.ipynb`       | Local, time-dependent, and neural-network-augmented coefficient adjustment.                                            | Figures 9, 10, 11; Table 5 |
| `5-Lockdown.ipynb`                    | Time-dependent coefficient adjustment for lockdown coefficient analysis.                                               | Figure 12                  |
| `6-LowCasesScenario.ipynb`            | Local coefficient adjustment for a low-case scenario.                                                                  | Figure 13                  |
| `7-SindySmoothingSensitivity.ipynb`   | Sensitivity analysis for infection-data smoothing windows.                                                             | Table 6                    |
| `8-SindyConvolutionSensitivity.ipynb` | Sensitivity analysis for convolution kernel choices.                                                                   | Figure 14                  |

## Data Files

The notebooks use the following tracked CSV files:

| File                                 | Description                                                                     |
| ------------------------------------ | ------------------------------------------------------------------------------- |
| `Thuringen_SIRD_2.csv`               | Daily aggregate infection, recovery, death, and vaccination data for Thuringia. |
| `Thuringen_SIRD_raw_2.csv`           | Raw version of the aggregate SIRD data.                                         |
| `Thuringen-SIRD-Grouped-2.csv`       | Age-grouped infection, death, hospitalisation, and ICU data.                    |
| `Thuringen_daily_vaccination.csv`    | Daily total, first-dose, second-dose, and third-dose vaccination data.          |
| `Thuringen_agegroup_vaccination.csv` | Daily age-grouped vaccination data.                                             |

## Julia Environment

The code is written in Julia. The package environment is defined by:

- `Project.toml`
- `Manifest.toml`

The included `Manifest.toml` was generated with Julia `1.11.5`.

To instantiate the environment, start Julia in the repository root and run:

```julia
using Pkg
Pkg.activate(".")
Pkg.instantiate()
```

To open the notebooks with the Julia kernel:

```julia
using Pkg
Pkg.activate(".")
using IJulia
notebook()
```

## Reproducibility Notes

- The numbered notebooks should be run in order within each notebook.
- Some notebooks perform optimisation, MCMC sampling, or neural-network fitting and may take a long time to run.
- Generated figures are outputs of the notebooks and are not tracked as source files in this repository.

## License

This project is licensed under the MIT License. See the LICENSE file in this repository for the full license text.
