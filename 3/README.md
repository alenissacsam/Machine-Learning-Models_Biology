# Asthma Classification (Recreated)

This folder contains a complete, reproducible workflow to predict asthma status (`Has_Asthma`) from `synthetic_asthma_dataset.csv`, with metrics, plots, and rationale for choosing Logistic Regression as the baseline model.

## Files
- `Asthma_Classification.ipynb`: End-to-end workflow with explanations and plots.
- `synthetic_asthma_dataset.csv`: Input data.
- `asthma_model_metrics.csv`: Saved metrics from the latest run.
- `asthma_pipeline.joblib`: Serialized pipeline (if present) for reuse.

## Why Logistic Regression?
- Interpretable: coefficients show direction and magnitude of effects after preprocessing.
- Probabilistic: outputs well-calibrated probabilities suitable for threshold tuning and risk ranking.
- Robust baseline: performs competitively with proper preprocessing and class weighting, fast to train.
- Handles imbalance: `class_weight='balanced'` compensates for class frequency differences.
- Great reference: establishes a solid baseline to compare with tree-based and boosting models.

## Data & Preprocessing
- Target: `Has_Asthma` (0/1). Dropped: `Patient_ID` (identifier), `Asthma_Control_Level` (post-diagnosis leakage).
- Numeric: median imputation + StandardScaler.
- Categorical: most-frequent imputation + OneHotEncoder (ignore unseen on test).
- All wrapped in a single scikit-learn Pipeline for correctness and reproducibility.

## Training & Evaluation
- Split: 80/20 stratified by target.
- Model: `LogisticRegression(max_iter=1000, class_weight='balanced', solver='liblinear')`.
- Metrics computed:
  - Accuracy, Precision, Recall, F1, MCC
  - Full classification report (per class)
- Plots:
  - Confusion Matrix
  - ROC Curve
  - Precision–Recall Curve
  - Calibration Curve
  - Feature Effects (|coef|)
  - Learning Curve (F1 vs training size)

## Current Metrics (latest run)
- Accuracy: 0.9220
- Precision: 0.7819
- Recall: 0.9425
- F1: 0.8547
- MCC: 0.8086

Saved in: `asthma_model_metrics.csv`.

## How to Run
1. Open `Asthma_Classification.ipynb`.
2. Run all cells from top to bottom.
3. Inspect plots inline and metrics in the final cell; metrics also saved to CSV.

## Next Steps (optional)
- Model comparison (RandomForest, GradientBoosting, XGBoost) with cross-validation.
- Threshold tuning to optimize F1 or other criteria.
- Export/reload pipeline for production scoring and batch inference.
