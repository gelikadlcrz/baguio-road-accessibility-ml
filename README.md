# Baguio Road Accessibility — Data Mining

A research project examining how road-network disruptions may affect access to healthcare facilities in Baguio City, Philippines. It combines geospatial analysis, network modeling, and machine learning to study and predict accessibility loss under simulated disruption scenarios.

## Project Overview

The project uses spatial and road-network information to characterize transportation connectivity, assess potential changes in accessibility, and investigate whether those changes can be estimated from network and geographic features.

The work is organized around a general research workflow:

1. **Data Preparation:** Inspect, validate, and integrate spatial and network datasets.
2. **Network Analysis:** Represent road connectivity and establish baseline accessibility measures.
3. **Disruption Simulation:** Evaluate changes in accessibility under defined road-disruption scenarios.
4. **Predictive Modeling:** Develop and assess models using features and outcomes derived from the analysis.
5. **Interpretation:** Examine model performance and the factors associated with accessibility loss.

## Repository Organization

```text
data/         Input and processed datasets
notebooks/    Exploratory analysis and research workflows
src/          Reusable Python code
tests/        Automated tests
reports/      Generated reports and figures
docs/         Supporting documentation
```

## Getting Started

Create a Python virtual environment and install the project dependencies:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Project datasets may not be included in version control. Consult the documentation and notebook inputs for the data required to reproduce individual analyses.

## Research Context

This repository contains the **data-mining component** of a broader study of road-network importance and accessibility in Baguio City. Simulation-derived accessibility changes are analytical outcomes, not observations of actual road closures or their consequences. Findings should be interpreted in light of the data sources, modeling assumptions, and evaluation methods documented in the analysis.