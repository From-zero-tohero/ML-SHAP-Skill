# ML-SHAP Skill

A reusable Codex skill for complete, leakage-aware machine-learning analysis of CSV and Excel tabular data.

该技能用于执行完整、可复现且防数据泄漏的表格机器学习流程，支持回归、分类、时间序列、分组数据与 SHAP 可解释性分析。

## Capabilities

- Audit missing values, duplicates, data types, outliers, target balance, and leakage risks.
- Select validation strategies for IID, temporal, grouped, and spatial data.
- Compare naive, linear, tree-ensemble, boosting, and other justified models.
- Tune models without contaminating the final holdout set.
- Evaluate regression and classification with task-appropriate metrics and diagnostics.
- Explain predictions using SHAP; include SHAP beeswarm / 蜂群图（蜂巢图） to show feature importance, contribution direction, feature-value distribution, and sample heterogeneity.
- Fall back transparently to permutation importance and PDP/ALE when SHAP is unavailable.
- Analyze nonlinear effects, interactions, representative cases, subgroups, and temporal regimes.
- Run robustness and sensitivity checks.
- Deliver publication-ready figures, Excel tables, reports, reproducible code, and optional JSON summaries.

## Skill structure

```text
ml-shap/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── figures-and-tables.md
    └── quality-gates.md
```

## Installation

Copy the `ml-shap` directory into your Codex skills directory:

```text
~/.codex/skills/ml-shap
```

Restart or refresh Codex so the skill can be discovered.

## Usage

Invoke the skill explicitly:

```text
Use $ml-shap to run a complete machine-learning and SHAP analysis on my dataset.
```

Example specification:

```text
File: data.xlsx
Worksheet: Sheet1
Output: carbon_emission
Inputs: GDP, population, temperature, urbanization
Task: regression
Time column: year
Group column: city
Research focus: nonlinear GDP effect and threshold
```

If task type or validation structure is uncertain, the skill audits the data and records defensible assumptions before modeling.

## Expected outputs

- Data-quality and descriptive-statistics tables
- Validation design and model-comparison results
- Tuned model parameters and untouched-test predictions
- Regression or classification diagnostics
- SHAP importance bar chart and SHAP beeswarm / 蜂群图（蜂巢图）
- SHAP dependence, interaction, and local waterfall explanations
- Robustness and sensitivity analyses
- Publication-ready PNG plus PDF/SVG figures
- Excel workbook, written report, reproducible script, and optional JSON summary

## Scientific safeguards

- Same-period estimation is not presented as future forecasting.
- Preprocessing and feature selection are fitted inside training folds.
- Temporal, grouped, and spatial structures receive matching validation designs.
- Predictive explanations are not described as causal effects.
- SHAP substitutes are labeled accurately rather than being presented as SHAP.

## License

No license has been specified yet. Add a license before redistributing or incorporating the skill into another project.
# ML-SHAP Skill

A reusable Codex skill for complete, leakage-aware machine-learning analysis of CSV and Excel tabular data.

该技能用于执行完整、可复现且防数据泄漏的表格机器学习流程，支持回归、分类、时间序列、分组数据与 SHAP 可解释性分析。

## Capabilities

- Audit missing values, duplicates, data types, outliers, target balance, and leakage risks.
- Select validation strategies for IID, temporal, grouped, and spatial data.
- Compare naive, linear, tree-ensemble, boosting, and other justified models.
- Tune models without contaminating the final holdout set.
- Evaluate regression and classification with task-appropriate metrics and diagnostics.
- Explain predictions using SHAP; fall back transparently to permutation importance and PDP/ALE when necessary.
- Analyze nonlinear effects, interactions, representative cases, subgroups, and temporal regimes.
- Run robustness and sensitivity checks.
- Deliver publication-ready figures, Excel tables, reports, reproducible code, and machine-readable summaries.

## Skill structure

```text
ml-shap/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── figures-and-tables.md
    └── quality-gates.md
```

## Installation

Copy the `ml-shap` directory into your Codex skills directory:

```text
~/.codex/skills/ml-shap
```

Restart or refresh Codex so the skill can be discovered.

## Usage

Invoke the skill explicitly:

```text
Use $ml-shap to run a complete machine-learning and SHAP analysis on my dataset.
```

Example specification:

```text
File: data.xlsx
Worksheet: Sheet1
Output: carbon_emission
Inputs: GDP, population, temperature, urbanization
Task: regression
Time column: year
Group column: city
Research focus: nonlinear GDP effect and threshold
```

If task type or validation structure is uncertain, the skill audits the data and records defensible assumptions before modeling.

## Expected outputs

- Data-quality and descriptive-statistics tables
- Validation design and model-comparison results
- Tuned model parameters and untouched-test predictions
- Regression or classification diagnostics
- SHAP importance, beeswarm, dependence, interaction, and local explanations
- Robustness and sensitivity analyses
- Publication-ready PNG plus PDF/SVG figures
- Excel workbook, written report, reproducible script, and optional JSON summary

## Scientific safeguards

- Same-period estimation is not presented as future forecasting.
- Preprocessing and feature selection are fitted inside training folds.
- Temporal, grouped, and spatial structures receive matching validation designs.
- Predictive explanations are not described as causal effects.
- SHAP substitutes are labeled accurately rather than being presented as SHAP.

## License

No license has been specified yet. Add a license before redistributing or incorporating the skill into another project.

## Example
<img width="2309" height="1998" alt="02_correlation_matrix" src="https://github.com/user-attachments/assets/a644591c-93b1-4dbe-9520-d248c5ee70bd" />
<img width="2969" height="1168" alt="01_time_series_split" src="https://github.com/user-attachments/assets/3458975d-34fe-4fd4-a8f4-2a75ebb2f503" />
<img width="2001" height="1468" alt="09_interaction_surface" src="https://github.com/user-attachments/assets/97896a45-a6c4-4f87-b6ef-6b61674b0365" />
<img width="2070" height="1409" alt="07_beeswarm_style_permutation_importance" src="https://github.com/user-attachments/assets/b6eb2bce-a533-4c67-a0a9-0813f4073a09" />
<img width="2070" height="1408" alt="06_permutation_importance" src="https://github.com/user-attachments/assets/bf6c67ca-7827-45ab-8ffd-355c7854f971" />
<img width="2969" height="1168" alt="05_residual_diagnostics" src="https://github.com/user-attachments/assets/5ecbdf0d-f1b8-45c9-ae70-b0520430a84a" />
<img width="3269" height="1227" alt="04_predictions" src="https://github.com/user-attachments/assets/39da1ec5-5db1-45e3-9523-35bee9d0d450" />
<img width="2374" height="1408" alt="03_model_comparison" src="https://github.com/user-attachments/assets/114c35b2-5cea-4eba-b8d5-e7a4620a1c3f" />
<img width="2969" height="2068" alt="08_partial_dependence" src="https://github.com/user-attachments/assets/261b17e5-f600-416d-9339-082339ecd137" />


