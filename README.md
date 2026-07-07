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
