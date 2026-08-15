# Classification Metrics & Confusion Matrix

A small, reproducible notebook for understanding binary-classification evaluation on a held-out test set.

## What it demonstrates

The notebook covers:

- confusion matrix (`TN`, `FP`, `FN`, `TP`)
- accuracy and balanced accuracy
- precision / positive predictive value
- recall / sensitivity
- specificity
- F1 score
- Matthews correlation coefficient (MCC)
- Cohen's kappa
- ROC AUC
- Average Precision (AP)
- trapezoidal area under the precision-recall curve
- threshold trade-offs

## Important distinction: AP is not trapezoidal PR AUC

`sklearn.metrics.average_precision_score` computes **Average Precision (AP)** as a recall-weighted mean of precision values. It is not the same calculation as trapezoidal integration of a precision-recall curve with `sklearn.metrics.auc`.

The notebook reports the two separately and labels them explicitly.

## Interpretation principles

There is no universal "good" cutoff for most classification metrics. Interpret performance relative to:

- a relevant baseline
- class prevalence
- uncertainty
- the costs of false positives and false negatives
- the intended deployment population and operating threshold

Accuracy can be particularly misleading with class imbalance, so the notebook also reports class-sensitive metrics and ranking metrics.

The threshold table in the notebook is a descriptive sensitivity check on held-out test predictions, not a threshold-selection procedure. In a real workflow, tune or select the operating threshold using training/validation data (or an appropriately nested resampling procedure), lock it, and evaluate that final threshold once on untouched test data.

## Reproducibility

The example:

- uses fixed random seeds
- uses a stratified train/test split
- evaluates metrics on held-out test data
- keeps notebook outputs and execution counts cleared in Git

Binder/repo2docker uses `requirements.txt` for the Python dependencies and `runtime.txt` for the Python version.

## Run locally

```bash
python -m pip install -r requirements.txt
jupyter lab
```

Then open:

`Classification Metrics & Confusion Matrix.ipynb`
