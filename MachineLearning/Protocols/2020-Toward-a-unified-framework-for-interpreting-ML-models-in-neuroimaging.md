# 2020 - Toward a unified framework for interpreting machine-learning models in neuroimaging

**Citation**: Kohoutová L, Heo J, Cha S, Lee S, Moon T, Wager TD, Woo C-W. Toward a unified framework for interpreting machine-learning models in neuroimaging. *Nature Protocols*. 2020;15:??-?? (Protocol originally accepted Dec 2019; doi:10.1038/s41596-019-0289-5)

**DOI**: 10.1038/s41596-019-0289-5  
**URL**: https://doi.org/10.1038/s41596-019-0289-5  
**Type**: Protocol / Methodological Framework  
**Keywords**: interpretability, neuroimaging, fMRI, biomarkers, machine learning, model validation, feature importance, representation analysis

## Abstract (Condensed)
Neuroimaging ML models can map brain function to behavioral and clinical outcomes, but their complexity hinders neuroscientific interpretation and trust. The protocol defines a unified multi-level framework—model-level, feature-level, and biology-level assessments—to evaluate whether a model (i) is human-comprehensible, (ii) supplies meaningful information about mental/behavioral constructs, and (iii) relies on neurobiologically valid (non-confounded) signal. Practical tools (largely MATLAB CANlab, with Python deep learning option) are provided for fMRI classifiers (e.g., SVM, CNN). The framework yields complementary evidence to support mechanistic insight, generalizability, and biological plausibility while highlighting open-ended, iterative validation.

## Problem & Motivation
- Proliferation of predictive ML in neuroimaging (decoding, biomarkers) outpaces interpretability and validation.
- Risk: "black box" models may embed confounds (motion, physiology) or overfit p >> n data, limiting scientific value and translational reliability.
- Need systematic, multi-angle evaluation rather than ad hoc sparsity or single performance metric.

## Framework Overview
Three assessment strata applied iteratively:
1. Model-level: Behavior of whole model (performance, generalizability, confounds, representational properties). 
2. Feature-level: Stability and importance of specific brain features (voxels, regions, networks) and visualization for human readability.
3. Biology-level: Neurobiological plausibility via literature, meta-analytic decoding, network overlap, invasive or multimodal convergence.

A recommended workflow cycles through build → intrinsic validation (Steps 2–6) → feature assessment (Step 7) → broader testing (Steps 8–11) → representational / behavioral analyses (Steps 12–15), revisiting earlier steps if deficiencies emerge.

## Model-Level Assessment (Key Components)
- Performance: Accuracy, sensitivity, specificity via cross-validation (LOSO, k-fold) with strict train/test independence; consider nested CV for hyperparameters.
- Generalizability: Out-of-sample datasets differing in individuals, scanners, contexts; 2AFC tests for pattern signatures (e.g., NPS, SIIPS1).
- Confound Analysis: Predict model outputs or labels from nuisance regressors (motion, physiological noise). Lack of predictive power suggests reduced confound influence.
- Representational / Behavioral Analysis: ROC curves, distance from hyperplane distributions, representational similarity among models and conditions.
- Edge Focus: Overfitting risk with p ≫ n; explicit warning about dependency leakage (shared preprocessing) and familial or site structure.

## Feature-Level Assessment (Options)
| Goal | Method | Notes |
|------|--------|-------|
| Stability | Bootstrap tests | Many resamples (5–10k) to identify reproducible weights; FDR thresholding. |
| Importance (wrapper) | Recursive Feature Elimination (RFE) | Iteratively remove low-weight features; track CV accuracy. |
| Importance (group lesion) | Virtual lesion analysis | Remove or isolate networks/regions; examine performance delta. |
| Importance (nonlinear) | Layer-wise Relevance Propagation (LRP) | Decompose CNN predictions to voxel relevance (positive/negative). |
| Visualization | Thresholded maps, saliency/heat maps | Human-readable localization; check plausibility (e.g., not ventricles). |

Consider complementary nature: stability (robustness) vs contribution (causal necessity proxy) vs explanation (directional relevance).

## Biology-Level Assessment
- Resting-State Network Overlap: Posterior probability of weight map intersection with canonical networks (Yeo 7 networks) for positive & negative weights.
- Meta-Analytic Decoding: Neurosynth term correlations to infer associated psychological constructs; may differentiate nociceptive vs socio-affective patterns.
- Converging Evidence: Compare to prior rodent, primate, human invasive/modulation studies; examine alignment with known circuits (e.g., basal ganglia, amygdala in pain). 
- Open-Ended: Encourage theory-building when models reveal novel regions; pursue validation via targeted experiments or causal perturbation.

## Recommended Validation Workflow
1. Data Quality & Preprocessing: Artifact removal, motion mitigation, appropriate masking, outcome reliability estimation.
2. Cross-Validated Performance: LOSO/k-fold metrics + AUC; stop if underperforming.
3. Confound Probing: Regression of model scores on nuisance variables; nuisance-only predictive tests.
4. Feature Stability/Importance: Bootstrap & RFE; identify minimal performant feature subsets; lesion analysis for network necessity.
5. Nonlinear Explainability (if deep model): LRP or SHAP (future extension) for per-class relevance.
6. Biological Plausibility: Network overlap + meta-analytic decoding; literature triangulation.
7. Generalization: Independent datasets spanning modality/task/population differences.
8. Representational Similarity: Compare multiple models (e.g., NPS vs SIIPS1) across condition matrix; cluster/dendrogram analysis.
9. Iterative Refinement: Rebuild or adjust based on failures (e.g., confound dependence, biologically implausible features).

## Evaluation Metrics & Interpretation
- Accuracy / Sensitivity / Specificity (with confidence intervals) contextualized by outcome reliability upper bounds.
- AUC & d' (or d_a) for discrimination robustness.
- Stability Z/P distributions from bootstrap; FDR-controlled voxel sets.
- Performance delta (%) upon virtual lesion; large drops imply functional necessity group-level.
- Relevance score maps (LRP) thresholded; positive vs negative contributions per class.
- Overlap posterior probabilities across networks: interpret dominance patterns (e.g., somatomotor vs default mode).
- Neurosynth term associations: Prioritize high-correlation, conceptually coherent terms; flag off-target terms (possible confounds).

## Limitations & Caveats
- Interpretability vs biological realism trade-off; sparse maps may oversimplify distributed processes.
- Bootstrap stability does not ensure causal relevance (could reflect correlated features).
- Virtual lesion analysis dependent on parcellation choice; coarse parcellations may mask fine-grained pattern interactions.
- LRP less validated in neuroimaging; methodological maturation needed (compare with perturbation / SHAP analyses).
- Biology-level evidence often indirect; absence of overlap ≠ invalidity (novelty vs noise tension).
- Cross-validation can be biased if data dependencies unaccounted (site, family, session order).

## Future Directions / Enhancements
- Integrate causal inference frameworks (e.g., counterfactual perturbations) for feature necessity.
- Multimodal fusion (EEG/MEG + fMRI) for temporal interpretability layering.
- Standardized reporting templates for interpretability audits (akin to model cards).
- Benchmark datasets and leaderboards emphasizing interpretability metrics, not only accuracy.
- Incorporation of fairness and subgroup performance audits (demographic / clinical stratification).
- Automated stability-generalizability Pareto optimization (hyperparameter search balancing both).

## Practical Tools Referenced
- CANlab (MATLAB) functions: `predict`, `roc_plot`, `svm_rfe`, `canlab_pattern_similarity`, `apply_mask`, `orthviews`, `threshold`.
- Python (deep learning): Keras/TensorFlow CNN, iNNvestigate for LRP, Nilearn/Nibabel for neuroimaging I/O.
- Meta-Analysis: Neurosynth decoder (term-based correlations).

## Relevance to Current Reading Notes
Serves as a protocol-level methodological backbone for interpreting ML-based neuroimaging biomarkers added under AI / clinical translational papers. Provides criteria for evaluating future model-centric papers (pain signatures, psychiatric prediction, cfRNA-brain integration, etc.).

## Personal Notes
- Emphasize iterative loop; don't treat interpretability as post-hoc add-on.
- For upcoming projects: establish preregistered interpretability assessment plan (stability threshold, confound tests, network overlap criteria) before final model lock.
- Consider adding SHAP comparison to LRP in future summaries for nonlinear models.
