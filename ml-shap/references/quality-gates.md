# Quality gates

Confirm all items before delivery.

## Scientific validity

- The task is correctly described as classification, regression, nowcasting, or forecasting.
- The forecast horizon and feature availability time are explicit.
- No target, future, group, or preprocessing leakage is present.
- The split matches temporal, grouped, spatial, or IID structure.
- The final test set was not used for tuning, threshold selection, or feature selection.
- A naive and interpretable baseline are included.
- Metrics match the target distribution and decision goal.
- Extreme periods and subgroup failures are discussed.

## Explanation validity

- SHAP uses the correct model output and class.
- Explanations use unseen or validation observations.
- Correlated predictors are discussed.
- PDP is not overinterpreted outside supported data ranges.
- Thresholds are treated as approximate unless uncertainty and stability are quantified.
- Prediction explanation is not described as causal inference.
- Any fallback method is named correctly.

## Reproducibility and delivery

- Seeds, package versions, split rules, and best parameters are saved.
- Tables contain exact values behind the figures.
- Figures include units, readable labels, and vector versions.
- Predictions retain dates or IDs for auditability.
- The source data was not modified.
- The report states limitations and the strongest caveat.
