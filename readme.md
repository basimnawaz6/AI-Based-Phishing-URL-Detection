# AI-Based Phishing URL Detection System

## Overview

This project presents a Machine Learning-based phishing URL detection system that classifies URLs as either **Legitimate** or **Phishing** using handcrafted URL features and supervised learning algorithms.

The project evaluates and compares three machine learning models:

* Random Forest
* XGBoost
* Multi-Layer Perceptron (MLP)

Unlike traditional approaches that use a fixed threshold of 0.5, this implementation performs **validation-based threshold optimization** before final testing, resulting in more reliable and realistic performance evaluation.

---

## Project Workflow

```text
Dataset
   ↓
Feature Extraction
   ↓
Train / Validation / Test Split
   ↓
Model Training
   ↓
Threshold Optimization (Validation Set)
   ↓
Best Threshold Selection
   ↓
Final Test Evaluation
   ↓
Visualization & Analysis
```

---

## Trained Models

Trained model files are not included in this repository due to their large size.

To reproduce results:

1. Download dataset
2. Run notebook
3. Train models
4. Generate results

---

## Repository Structure

```text
AI_Based_Phishing_URL_Detection_System/

├── data/
│   └── dataset.csv
│
├── notebooks/
│   └── AI_Based_Phishing_URL_Detection_System.ipynb
│
├── results/
│   ├── confusion_matrices.png
│   ├── feature_importance.png
│   ├── model_comparison_bars.png
│   ├── model_comparison_summary.csv
│   ├── precision_recall_curves.png
│   ├── roc_curves.png
│   └── threshold_optimization.png
│
├── train_test/
│   ├── data/
│   │   └── dataset.csv
│   │
│   ├── notebooks/
│   │   └── AI_Based_Phishing_URL_Detection_System_train_to_test.ipynb
│   │
│   ├── results/
│   │   ├── bar_chart_model_comparison_0.3.png
│   │   ├── bar_chart_model_comparison_0.35.png
│   │   ├── bar_chart_model_comparison_0.4.png
│   │   ├── bar_chart_model_comparison_0.45.png
│   │   ├── bar_chart_model_comparison_0.5.png
│   │   ├── model_comparison.png
│   │   ├── threshold_analysis.png
│   │   └── README.md
│
└── README.md
```

---

## Feature Engineering

The model extracts 24 URL-based features including:

### URL Structure Features

* URL Length
* Domain Length
* Path Length
* Query Length

### Special Character Features

* Dot Count
* Hyphen Count
* Underscore Count
* Slash Count
* Question Mark Count
* Equal Sign Count
* At Sign Count
* Ampersand Count
* Percent Symbol Count

### Ratio Features

* Digit Ratio
* Letter Ratio
* Special Character Ratio

### Security Indicators

* Suspicious TLD Detection
* IP Address Detection
* Hyphenated Domain Detection
* Suspicious Keyword Count

### Statistical Features

* Domain Entropy
* URL Entropy
* Domain Dot Count
* Path Slash Count

---

## Machine Learning Models

### Random Forest

```python
RandomForestClassifier(
    n_estimators=250,
    max_depth=25,
    min_samples_split=5,
    min_samples_leaf=2,
    class_weight='balanced'
)
```

### XGBoost

```python
XGBClassifier(
    n_estimators=300,
    learning_rate=0.08,
    max_depth=8,
    subsample=0.9,
    colsample_bytree=0.9,
    scale_pos_weight=balanced_ratio
)
```

### Multi-Layer Perceptron

```python
MLPClassifier(
    hidden_layer_sizes=(128,64),
    early_stopping=True,
    max_iter=500
)
```

---

## Evaluation Metrics

The models are evaluated using:

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC

Threshold optimization is performed on the validation set before evaluating on the final test set.

---

## Final Results

The models were trained using a Train → Validation → Test workflow. Decision thresholds were optimized on the validation set and final performance was evaluated on an unseen test set.

### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1 Score | ROC-AUC | Optimal Threshold |
|---------|---------|---------|---------|---------|---------|---------|
| Random Forest | 91.78% | 85.97% | 84.98% | **85.47%** | **96.95%** | 0.52 |
| XGBoost | 90.70% | 85.00% | 81.77% | 83.35% | 96.09% | 0.61 |
| MLP | 90.17% | 83.62% | 81.41% | 82.50% | 95.49% | 0.39 |

### Best Model

🏆 **Random Forest** achieved the best overall performance and was selected as the final deployment candidate.

| Metric | Value |
|----------|----------|
| Accuracy | 91.78% |
| Precision | 85.97% |
| Recall | 84.98% |
| F1 Score | 85.47% |
| ROC-AUC | 96.95% |
| Optimal Threshold | 0.52 |

### Performance Highlights

- Highest F1 Score among all evaluated models.
- Highest ROC-AUC score, demonstrating strong discrimination capability.
- Balanced Precision and Recall, reducing both false positives and false negatives.
- Validation-based threshold optimization improved classification performance over a fixed threshold approach.

---

## Visualizations

The project automatically generates:

* Model Comparison Charts
* ROC Curves
* Precision-Recall Curves
* Confusion Matrices
* Threshold Optimization Analysis
* Feature Importance Visualization

### Model Comparison

![Model Comparison](results/model_comparison_bars.png)

### ROC Curves

![ROC Curves](results/roc_curves.png)

### Precision-Recall Curves

![Precision Recall Curves](results/precision_recall_curves.png)

### Confusion Matrices

![Confusion Matrices](results/confusion_matrices.png)

### Threshold Optimization

![Threshold Optimization](results/threshold_optimization.png)

### Feature Importance

![Feature Importance](results/feature_importance.png)

---

## Visualizations

The project automatically generates:

* Model Comparison Charts
* ROC Curves
* Precision-Recall Curves
* Confusion Matrices
* Threshold Optimization Analysis
* Feature Importance Visualization

---

## Previous Experiment

The `train_test` directory contains an earlier implementation that evaluated models using multiple fixed thresholds:

* 0.30
* 0.35
* 0.40
* 0.45
* 0.50

This experiment was used to study threshold sensitivity before implementing the current Train-Validation-Test workflow.

---

## Key Improvements Over Previous Version

* Proper Train / Validation / Test split
* Threshold tuning performed on validation data only
* Final evaluation performed on unseen test data
* Class imbalance handling
* Improved Random Forest configuration
* Better visualization and model analysis
* Reduced risk of threshold-selection bias

---

## Future Work

* SHAP Explainability
* Real-time URL Scanner API
* Browser Extension
* Deep Learning URL Classification
* Ensemble Voting Models
* Flask/FastAPI Deployment
* Feature Selection Analysis