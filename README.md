# VL-Survey

The survey's complete English system coding table is available in [Complete_system_coding.xlsx](Complete_system_coding.xlsx). It contains **564 systems and 79 columns** in one worksheet, with one system per row: 238 virtual models and 326 digital twins. Each row includes an article title, publication year, and direct article link.

[Read the column guide online](https://zhangzihan-is-good.github.io/VL-Survey/Coding_table_guide.html) for each column's meaning, possible values, and applicable conditions. The [standalone HTML guide](Coding_table_guide.html) can also be downloaded and opened offline. It supports keyword search and browsing by topic.

Model limitations and unmodeled components are collected in one numbered list per system. Cross-scale connections and their corresponding test statuses are collected in another numbered list. The guide explains how summary counts are obtained from these details.

Credibility items describe practices reported in the articles. `yes` means the article reports the practice, and `no` means it does not report the practice. `Not applicable` marks a field that does not apply to the model or an empty list. `Not reported` marks information that the article does not provide. Field-specific definitions are given in the guide.

## Coding revision (2026-11-27)

This revision corrects 16 coding cells after a field-consistency audit and review of the source articles. The table still contains 564 systems and 79 columns.

| System ID | Column | Previous value | Corrected value | Reason |
|---|---|---|---|---|
| S027 | <code>uncertainty_narrow_forms</code> | <code>Not applicable</code> | <code>Output distribution</code> | Calibrated DE and DIR probabilities explicitly represent binary output distributions. |
| S100 | <code>scale</code> | <code>molecule and pathway</code> | <code>cell</code> | The model computes single-cell expression states and evolving cell populations. |
| S199 | <code>uncertainty_broad_categories</code> | <code>none</code> | <code>intrinsic stochasticity</code> | Latent-space random sampling explicitly generates a distribution of virtual heart shapes, so broad intrinsic stochasticity is represented. |
| S206 | <code>simple_baseline_result</code> | <code>Not applicable</code> | <code>not stated in the main text</code> | Permutation null models are reported, but no comparative performance direction is stated. |
| S206 | <code>uncertainty_narrow_forms</code> | <code>Not applicable</code> | <code>Stochastic simulation</code> | Tissue conductivities are sampled from a Beta distribution to simulate variation. |
| DS118 | <code>scale</code> | <code>cell</code> | <code>organism</code> | Implemented pharmacokinetic variants compute systemic absorption, central/peripheral disposition and clearance states coupled to cell populations, so the highest modeled scale is organism. |
| DS144 | <code>model_weights_publicly_available</code> | <code>Not applicable</code> | <code>Not reported</code> | The implemented ridge regression has learned coefficients, whose public release is not stated. |
| DS160 | <code>model_weights_publicly_available</code> | <code>Not applicable</code> | <code>Not reported</code> | The trained linear emulator requires learned coefficients and intercepts; their public release is not stated. |
| DS161 | <code>model_weights_publicly_available</code> | <code>Not applicable</code> | <code>Not reported</code> | The implemented LASSO formula requires learned coefficients; their public release is not stated. |
| DS189 | <code>model_weights_publicly_available</code> | <code>Not applicable</code> | <code>Not reported</code> | The fitted generalized additive model has learned parameters; their public release is not stated. |
| DS204 | <code>model_weights_publicly_available</code> | <code>Not applicable</code> | <code>yes</code> | The article publishes the fitted statistical parameters and reports public model code. |
| DS217 | <code>scales_modeled</code> | <code>molecule and pathway;cell;tissue and organoid;organ</code> | <code>molecule and pathway;cell;tissue and organoid</code> | Remove organ because the Oncosimulator and biomechanics simulator compute tissue states; patient anatomy defines their domains rather than an independent organ state. |
| DS217 | <code>cross_scale_links_and_tests</code> | <code>1. Joint training or joint solution &#124; model-to-model &#124; bidirectional &#124; molecule and pathway→cell &#124; Test: partial</code><br><code>2. Joint training or joint solution &#124; model-to-model &#124; bidirectional &#124; cell→tissue and organoid &#124; Test: no</code><br><code>3. Joint training or joint solution &#124; model-to-model &#124; bidirectional &#124; tissue and organoid→organ &#124; Test: partial</code><br><code>4. Parameter or boundary-condition passing &#124; measurement-to-model &#124; top-down &#124; tissue and organoid→molecule and pathway &#124; Test: no</code> | <code>1. Parameter or boundary-condition passing &#124; model-to-model &#124; bottom-up &#124; molecule and pathway→cell &#124; Test: partial</code><br><code>2. Joint training or joint solution &#124; model-to-model &#124; bidirectional &#124; cell→tissue and organoid &#124; Test: no</code><br><code>3. Parameter or boundary-condition passing &#124; measurement-to-model &#124; top-down &#124; tissue and organoid→molecule and pathway &#124; Test: no</code> | Remove the same-scale OS–BMS link and encode the explicitly serial molecular CKR handoff as bottom-up parameter passing. |
| DS228 | <code>uncertainty_narrow_forms</code> | <code>Not applicable</code> | <code>Stochastic simulation</code> | Probabilistic fibrosis assignment explicitly simulates stochastic tissue variation. |
| DS244 | <code>scales_modeled</code> | <code>tissue;organ</code> | <code>molecule and pathway;tissue and organoid</code> | Toxin and collagen concentrations and tissue mechanics are computed; the facial sag index is an endpoint. |
| DS299 | <code>scales_modeled</code> | <code>organ</code> | <code>tissue and organoid</code> | The finite-element model computes muscle and fat tissue mechanics, with bones constrained as rigid bodies. |

The remaining scale inconsistency for DS088 was left unchanged because the available article and repository pages required browser verification; no unverified correction was made.
