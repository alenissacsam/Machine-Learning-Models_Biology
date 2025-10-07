# DNA Classification Workflow Report

This summarizes the workflow in `DNA_Classification.ipynb` for classifying synthetic DNA samples on two targets: `Disease_Risk` (3 classes) and `Class_Label` (4 classes). We started with a PCA-enabled pipeline, but per the latest requirement there are only a few numeric features (~5), so PCA has been fully removed to keep the model simpler and avoid unnecessary complexity.

## Constraints and outputs

- No tree ensembles (e.g., RandomForest).
- Robust cross-validation for model tuning.
- PCA is disabled everywhere (numeric pipeline is impute → scale only).
- Artifacts are saved under `2/outputs/`: metrics JSONs, plots, trained models, predictions.

## Overfitting mitigation

Two main steps reduced overfitting:
- Drop ID-like/high-cardinality text fields (e.g., `Sample_ID`, raw `Sequence`) to prevent memorization.
- Prefer linear models with regularization (LogisticRegression; optionally Calibrated LinearSVC) and tune only the C parameter.

Preprocessor drops near-unique object columns and builds separate pipelines:

```python
numeric_pipeline = Pipeline([
    ('imputer', SimpleImputer(strategy='median')),
    ('scaler', StandardScaler()),
])

categorical_pipeline = Pipeline([
    ('imputer', SimpleImputer(strategy='most_frequent')),
    ('onehot', OneHotEncoder(handle_unknown='ignore', sparse_output=False))
])

preprocess = ColumnTransformer([
    ('num', numeric_pipeline, num_cols),
    ('cat', categorical_pipeline, cat_cols)
])
```

## Cross-validation and tuning (no PCA)

We use repeated stratified K-fold and tune only `C`:

```python
cv = RepeatedStratifiedKFold(n_splits=5, n_repeats=3, random_state=RANDOM_STATE)

pipe = Pipeline([
    ('preprocess', preprocess),
    ('clf', LogisticRegression(max_iter=1000, class_weight='balanced', random_state=RANDOM_STATE))
])

param_grid = {'clf__C': [0.1, 0.3, 0.5, 1.0]}
gs = GridSearchCV(pipe, param_grid=param_grid, scoring='f1_macro', cv=cv, n_jobs=-1, refit=True)
```

For Calibrated LinearSVC we use a version-safe key when tuning C:

```python
for svc_key in ['clf__estimator__C', 'clf__base_estimator__C']:
    param_grid = {svc_key: [0.1, 0.3, 0.5, 1.0]}
    # try GridSearchCV(...)
```

## Evaluation and artifacts

For each target we export:
- Metrics: accuracy, macro precision/recall/f1, MCC for both train and test.
- Plots: confusion matrices, ROC/PR (OvR), learning curves, permutation importance, calibration curves, and threshold sweeps for binary targets (skipped for multiclass).
- Models and metrics: `<tag>_model.joblib`, `<tag>_metrics.json`.
- Predictions: `predictions_dual.csv` with model predictions for both targets.

Note: PCA analysis and PCA vs no-PCA comparisons are now skipped and not produced.

## Status of current runs

From recent runs (pre-PCA removal), logistic regression was the best across both targets with modest generalization gaps. After removing PCA, retraining will produce PCA-free artifacts with the same evaluation suite.

## Conclusion

With only ~5 numeric features, PCA adds no value and can be counterproductive. A regularized logistic regression (optionally a calibrated LinearSVC) with robust CV and careful preprocessing is a simple, strong baseline. The notebook enforces “no PCA” globally and skips PCA-specific analyses and comparisons.
