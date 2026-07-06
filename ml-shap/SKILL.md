---
name: ml-shap
description: Run a complete, leakage-aware machine-learning workflow on CSV or Excel tabular data when the user identifies input features, one output feature, and optionally a date, group, region, or ID column. Use for regression or classification tasks requiring data audits, defensible train/test splitting, baseline and nonlinear model comparison, tuning, out-of-sample evaluation, SHAP interpretation, nonlinear thresholds, interactions, robustness checks, publication-ready figures and tables, a reproducible script, and a written results report.
---

# ML-SHAP

Execute the analysis rather than only describing it. Preserve the source file and write all deliverables to a separate output directory.

## Collect the specification

Obtain or infer:

- source file and worksheet;
- output column;
- input columns;
- regression or classification task;
- date/time, group, region, and ID columns;
- forecast horizon if the user means future prediction;
- positive class and primary metric for classification;
- research focus, such as a focal variable or expected threshold.

Ask only when a missing choice materially changes the scientific question. Otherwise infer safely and record the assumption.

## Audit before modeling

Check schema, sample count, date range, duplicates, missingness, infinities, constant columns, data types, target distribution, category cardinality, outliers, class balance, and suspiciously high target correlations.

Detect leakage explicitly:

- exclude IDs, post-outcome variables, target-derived fields, and future information;
- distinguish same-period estimation from genuine forecasting;
- if a feature is almost identical to the target, retain it only when requested and add an exclusion sensitivity analysis;
- fit imputers, scalers, encoders, feature selection, and resampling inside the training pipeline only.

Stop and explain if the target is unusable. Otherwise continue.

## Choose validation from the data structure

Never default blindly to random splitting.

- Time or forecast task: sort chronologically, reserve the latest 15–25% as an untouched test set, and tune with expanding-window or rolling validation. Lag predictors according to the forecast horizon.
- Repeated groups, people, firms, cities, or sites: use group holdout or grouped cross-validation.
- Spatial generalization: prefer spatial blocks or region holdout.
- Ordinary IID regression: use shuffled K-fold validation with a fixed seed.
- IID classification: use stratified splits; use stratified-group validation when both class and group structure exist.

Keep the final test set untouched until model selection is finished. Report exact split dates or group rules.

## Build and compare models

Always include a naive baseline and an interpretable linear baseline.

For regression, consider:

- mean/median or persistence baseline;
- linear regression, Ridge, or Elastic Net;
- random forest and Extra Trees;
- gradient boosting, XGBoost, LightGBM, or CatBoost when available;
- SVR or neural models only when justified by scale and structure.

For classification, consider:

- majority or prior baseline;
- logistic regression;
- random forest and Extra Trees;
- gradient boosting, XGBoost, LightGBM, or CatBoost;
- calibrated probabilities when decisions depend on risk scores.

Tune only competitive model families using the selected cross-validation design. Prefer randomized or Bayesian search to wasteful grids. Fix seeds and limit parallelism when resources are constrained.

## Evaluate out of sample

Regression:

- primary: RMSE or MAE;
- also report R² and MAE; report MAPE only when targets are safely away from zero;
- inspect observed-versus-predicted, residual-versus-predicted, residual distribution, and temporal residuals.

Classification:

- report confusion matrix, precision, recall, F1, ROC-AUC, and PR-AUC;
- prioritize PR-AUC, recall, or cost-sensitive metrics for imbalance;
- show ROC, precision–recall, calibration, and threshold-performance plots;
- never choose a threshold on the final test set.

Report cross-validation mean and dispersion plus untouched-test performance. Diagnose regime shifts, extrapolation failures, and subgroup errors rather than celebrating a single score.

## Explain the selected model

Use SHAP when compatible:

- TreeExplainer for tree ensembles;
- LinearExplainer for linear models;
- model-agnostic explainers only with a justified background sample and manageable computation.

Produce explanations in this order:

1. global mean absolute SHAP importance;
2. SHAP beeswarm for magnitude, direction, and heterogeneity;
3. dependence plots for key variables, with zero line and defensible smoothing;
4. SHAP interaction values or interaction dependence for important pairs;
5. waterfall plots for representative, extreme, correct, and failed predictions;
6. grouped or temporal SHAP summaries when heterogeneity matters.

Explain predictions on validation/test observations, not only training data. State the SHAP background dataset and class explained.

If SHAP cannot be installed or computed, use permutation importance plus PDP/ALE and label these methods accurately. Never call a substitute “SHAP.” Prefer ALE over PDP when predictors are strongly correlated.

Treat all model explanations as predictive associations. Do not use causal language unless a valid causal design or estimator is added.

Read [references/figures-and-tables.md](references/figures-and-tables.md) when deciding the output set. Read [references/quality-gates.md](references/quality-gates.md) before finalizing.

## Run robustness checks

Include checks proportional to the claim:

- alternative seeds, folds, cut dates, or holdout groups;
- removal of suspicious or dominant features;
- alternative model families;
- reduced versus full feature sets;
- class weighting or resampling sensitivity;
- subgroup and regime performance;
- lag/horizon variants for forecasts;
- bootstrap confidence intervals when useful.

Do not interpret unstable ranks or thresholds as substantive findings.

## Deliver

Create:

- an Excel workbook containing data audit, descriptive statistics, correlations, split definition, model comparison, best parameters, robustness results, feature importance, thresholds/interactions, and holdout predictions;
- publication-ready PNG and vector PDF/SVG figures;
- a concise Markdown or Word report covering methods, results, limitations, and interpretation boundaries;
- a reproducible Python or R script plus environment/package information;
- a machine-readable summary JSON when useful.

Lead the final response with the main result and the most important caveat. Link the report, workbook, script, and output directory.

