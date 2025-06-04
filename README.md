# Developing a Machine Learning Model for Hydrogen Bond Acceptance Based on Natural Bond Orbital Descriptors

**Authors:** Diego Ulysses Melo, Leonardo Martins Carneiro, Mauricio Domingues Coutinho-Neto, Paula Homem-de-Mello, and Fernando Heering Bartoloni*

**DOI:** [Link to be added upon publication]

**Associated Data & Code:**
* **Zenodo:** [https://doi.org/10.5281/zenodo.14364022](https://doi.org/10.5281/zenodo.14364022)

---

## Overview

This research predicts hydrogen bond acceptance using machine learning (ML) models. It uniquely employs electronic descriptors from Natural Bond Orbital (NBO) analysis, specifically second-order perturbation stabilization energies ($E^{(2)}$), as features. The study shows that a small set of these descriptors enables highly accurate $pK_{HBX}$ predictions.

## Key Findings

* **Excelent Predictive Performance:** ML models, especially the Multi-layer Perceptron (MLP), accurately predicted $pK_{HBX}$ values (RMSE $0.290$, MAE $0.216$, $R^2$ $0.920$). Errors are < $0.4 \, \text{kcal mol}^{-1}$ in Gibbs free energy.
* **NBO Descriptors Sufficiency:** Eight $\Delta E^{(2)}$ NBO-derived values were enough for robust models, unlike methods needing many descriptors.
* **Chemical Interpretability:** NBO descriptors offer clear chemical meaning. SHAP analysis showed specific NBO interaction contributions.
* **Methodology Efficiency:** The workflow combines efficient GFN2-xTB optimizations with DFT-level NBO analysis, suitable for large-scale use.

## Methodology

1.  **Dataset:** 979 hydrogen bond complexes (HBA + 4-FPh as HBD). $pK_{HBX}$ values from literature.
2.  **Computational Workflow:**
    * **SMILES Processing & Structure Generation:** RDKit used for 2D structure generation and complex formation.
    * **Geometry Optimization:** GFN2-xTB (ALPB solvation - chloroform).
    * **Single-Point & NBO Analysis:** DFT (CAM-B3LYP/def2-TZV, SMD solvation - tetrachloromethane) for $E^{(2)}$ of 8 key interactions in 4-FPh (complexed vs. isolated).
    * **Feature Engineering:** Descriptors ($\Delta E_n^{(2)}$) are differences in $E_n^{(2)}$ (complex vs. isolated 4-FPh).
3.  **Machine Learning Models:**
    * Algorithms: KNN, Decision Tree, RF, SVM, MLP, XGBoost, CatBoost.
    * Hyperparameter Optimization: Optuna (TPE algorithm).
    * Evaluation: Hold-out cross-validation (90/10 split), RMSE, MAE, $R^2$.
4.  **Model Interpretation:** SHAP analysis for NBO descriptor contributions in the MLP model.

## Software and Libraries Used

* **Cheminformatics:** RDKit (2023.09.1)
* **Quantum Chemistry:** GFN2-xTB (xtb 6.5.1), Gaussian 09, NBO (v3), Multiwfn, VMD
* **Machine Learning:** Scikit-learn (1.4.0), XGBoost, CatBoost, Optuna (3.5.0)
* **Programming:** Python 3

## Citation

Please cite:
