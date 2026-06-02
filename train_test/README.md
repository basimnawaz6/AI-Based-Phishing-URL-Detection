# AI-Based Phishing URL Detection System

## Overview

This project presents a Machine Learning-based phishing URL detection system designed to classify URLs as either legitimate or phishing. The system evaluates and compares three machine learning models:

* Random Forest
* XGBoost
* Multi-Layer Perceptron (MLP)

The impact of probability threshold tuning is analyzed using multiple performance metrics including Accuracy, Precision, Recall, F1-Score, and ROC-AUC.

---

## Project Objectives

* Detect phishing URLs using machine learning techniques.
* Compare ensemble learning and neural network models.
* Analyze threshold optimization for improved classification.
* Identify the most effective model for phishing URL detection.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Scikit-Learn
* XGBoost
* Matplotlib
* Jupyter Notebook

---

## Machine Learning Models

### Random Forest

* n_estimators = 300
* max_features = sqrt
* random_state = 42

### XGBoost

* n_estimators = 300
* learning_rate = 0.08
* max_depth = 8
* subsample = 0.9
* colsample_bytree = 0.9
* random_state = 42

### Multi-Layer Perceptron (MLP)

* hidden_layer_sizes = (128, 64)
* activation = relu
* solver = adam
* early_stopping = True
* max_iter = 500
* random_state = 42

---

# Results

## Threshold = 0.30

| Model         | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
| ------------- | -------- | --------- | ------ | -------- | ------- |
| Random Forest | 83.68%   | 68.64%    | 78.56% | 73.27%   | 90.69%  |
| XGBoost       | 84.31%   | 73.45%    | 70.33% | 71.85%   | 89.93%  |
| MLP           | 83.86%   | 72.45%    | 69.89% | 71.15%   | 89.41%  |

## Threshold = 0.35

| Model         | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
| ------------- | -------- | --------- | ------ | -------- | ------- |
| Random Forest | 85.08%   | 72.91%    | 75.75% | 74.30%   | 90.69%  |
| XGBoost       | 85.42%   | 79.09%    | 66.33% | 72.15%   | 89.93%  |
| MLP           | 84.90%   | 77.34%    | 66.42% | 71.46%   | 89.41%  |

## Threshold = 0.40

| Model         | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
| ------------- | -------- | --------- | ------ | -------- | ------- |
| Random Forest | 85.93%   | 76.20%    | 73.54% | 74.85%   | 90.69%  |
| XGBoost       | 85.83%   | 82.41%    | 63.89% | 71.98%   | 89.93%  |
| MLP           | 85.44%   | 81.09%    | 63.74% | 71.38%   | 89.41%  |

## Threshold = 0.45

| Model         | Accuracy   | Precision | Recall | F1 Score   | ROC-AUC    |
| ------------- | ---------- | --------- | ------ | ---------- | ---------- |
| Random Forest | **86.49%** | 78.98%    | 71.62% | **75.12%** | **90.69%** |
| XGBoost       | 86.00%     | 85.08%    | 61.67% | 71.50%     | 89.93%     |
| MLP           | 85.60%     | 83.72%    | 61.36% | 70.81%     | 89.41%     |

## Threshold = 0.50

| Model         | Accuracy   | Precision  | Recall | F1 Score | ROC-AUC    |
| ------------- | ---------- | ---------- | ------ | -------- | ---------- |
| Random Forest | **86.74%** | 81.13%     | 69.63% | 74.94%   | **90.69%** |
| XGBoost       | **85.95%** | **87.32%** | 59.25% | 70.60%   | 89.93%     |
| MLP           | 85.65%     | 86.06%     | 59.18% | 70.13%   | 89.41%     |

---

## Key Findings

### Best Overall Model: Random Forest

The Random Forest classifier consistently achieved the strongest overall performance:

* Highest ROC-AUC: 90.69%
* Highest F1-Score: 75.12% (Threshold = 0.45)
* Highest Accuracy: 86.74% (Threshold = 0.50)
* Highest Recall: 78.56% (Threshold = 0.30)

### XGBoost Strength

XGBoost achieved the highest Precision:

* Precision: 87.32% (Threshold = 0.50)

This makes it suitable when minimizing false positives is a priority.

### MLP Performance

The MLP model delivered competitive results but generally performed slightly below Random Forest and XGBoost across most evaluation metrics.

---

## Conclusion

The results demonstrate that Random Forest provides the most balanced performance for phishing URL detection. Through threshold optimization, the model achieved strong Accuracy, Recall, F1-Score, and ROC-AUC values, making it the preferred model for deployment in phishing detection systems.

The study also highlights the importance of threshold tuning in cybersecurity applications, where the trade-off between Precision and Recall directly impacts detection effectiveness.
