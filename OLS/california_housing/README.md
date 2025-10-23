<div align="center">

<img src="assets/logo.png" alt="Project Logo" width="140">

<h1>California Housing — Linear Modeling Study</h1>

<p>
A structured exploration of Ordinary Least Squares (OLS) applied to the California Housing dataset.
The project examines baseline linear regression, feature engineering, polynomial expansion, and detailed diagnostics —
all within the OLS framework.
</p>

</div>

<hr>

<table>
  <tr>
    <td><b>Model Family</b></td>
    <td>OLS (statsmodels)</td>
    <td><b>Dataset</b></td>
    <td>sklearn California Housing</td>
  </tr>
  <tr>
    <td><b>Focus</b></td>
    <td>Interpretability, diagnostics, controlled complexity</td>
    <td><b>Core Tasks</b></td>
    <td>Feature engineering, polynomial expansion, residual analysis</td>
  </tr>
</table>

<hr>

<div align="center">
  <a href="#overview">Overview</a> •
  <a href="#reproducibility">Reproducibility</a> •
  <a href="#workflow">Workflow</a> •
  <a href="#diagnostics">Diagnostics</a> •
  <a href="#results">Results</a> •
  <a href="#structure">Repo Structure</a> •
  <a href="#notes">Notes</a>
</div>

<hr>

## Overview

This project studies how much predictive performance can be improved in the California Housing dataset by progressively extending a plain linear regression model.  
Starting from a standard OLS baseline, the analysis introduces two systematic extensions:  

1. **Interaction terms** between key predictors (such as income × rooms, income × age, and spatial interactions).  
2. **Polynomial feature expansion** to degree two, allowing the model to capture mild nonlinear relationships while remaining within the OLS framework.  

Each stage is evaluated on the same train–test split using R², RMSE, and MAE.  
The results show a steady improvement in predictive accuracy as interaction and polynomial terms are added, confirming that modest feature engineering can substantially enhance linear model performance without resorting to more complex algorithms.

---

## Results

Performance improved consistently with each modeling step.  
The **baseline OLS** using raw features reached an R² of about 0.63 on the test set, capturing the broad relationship between income, location, and housing value but leaving clear nonlinear patterns in the residuals.  
Introducing **interaction terms** lifted the test R² to roughly 0.66, confirming that moderate feature engineering helps linear models recover hidden structure without overfitting.  
The **polynomial model** was the best performer overall, achieving an R² of 0.71 with a test RMSE of 0.29 and MAE of 0.21.  
It successfully absorbed much of the curvature and spatial interaction present in the data while keeping inference transparent and coefficients interpretable.  
Beyond this point, additional complexity would likely yield diminishing returns, suggesting that second-degree polynomial OLS strikes the right balance between simplicity and explanatory power for this dataset.

---

## Results

| Model | R² (Train) | R² (Test) | RMSE (Test) | MAE (Test) | Comment |
|--------|-------------|------------|--------------|-------------|----------|
| Baseline OLS | 0.642 | 0.635 | 0.320 | 0.241 | Standard linear model on raw features |
| Enhanced (Interactions) | 0.668 | 0.662 | 0.308 | 0.229 | Interaction terms add structure and stability |
| Polynomial (Degree 2) | **0.713** | **0.707** | **0.287** | **0.214** | Best-performing model; captures curvature effectively |

Performance improved steadily with each extension.  
The polynomial model delivered the best fit, raising the test R² by about **7 percentage points** over the baseline and reducing RMSE from **0.320 → 0.287**.  
This confirms that modest nonlinearity—introduced through polynomial expansion—can significantly enhance predictive power while keeping the model interpretable.


## Reproducibility

To reproduce results:

```bash
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter lab