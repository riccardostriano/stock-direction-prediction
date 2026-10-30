Copia tutto questo nel tuo `README.md`:

````markdown
# Stock Direction Prediction

Bachelor’s thesis project comparing machine learning and deep learning models for next-day stock price direction prediction on Apple (AAPL).

## Overview

The project investigates whether historical market data and technical indicators can help predict the direction of the next trading day's closing price.

The task is formulated as a binary classification problem:

- **1 — Up:** the next day's closing price is higher than the current day's.
- **0 — Down or unchanged:** the next day's closing price is lower than or equal to the current day's.

The analysis uses Apple stock data from **2018 to 2023**.

## Repository Contents

- [Python notebook](notebooks/ProgettoML.ipynb): data preparation, feature engineering, model training and evaluation.
- [Thesis](thesis/StrianoRiccardo_TesiTriennale.pdf): full methodology, experimental results and discussion, in Italian.
- [Presentation](presentation/Presentazione_TesiTriennale.pptx): slides prepared for the thesis defense, in Italian.

## Data and Features

The dataset includes five historical market variables:

- Open
- High
- Low
- Close
- Volume

Additional features were created through feature engineering:

- Daily return
- 10-day moving average
- 50-day moving average
- Volatility
- Momentum

These indicators summarize price changes, trends and fluctuations.

## Models

Four models were evaluated:

- Logistic Regression
- Support Vector Machine (SVM)
- Random Forest
- Long Short-Term Memory network (LSTM)

An **always-up baseline**, which predicts an increase for every observation, was used as a reference.

## Methodology

- Chronological split: **80% training and 20% testing**.
- Feature standardization for Logistic Regression, SVM and LSTM.
- Temporal cross-validation using **TimeSeriesSplit with five folds**.
- Hyperparameter tuning using **GridSearchCV for SVM and Random Forest**.
- Evaluation through accuracy, precision, recall, F1-score and confusion matrices.
- Analysis of Random Forest feature importance.
- Comparison of traditional models with and without engineered features.

## Results Reported in the Thesis

Precision, recall and F1-score below are **weighted averages**.

| Model | Accuracy | Precision | Recall | F1-score |
|---|---:|---:|---:|---:|
| Always-up baseline | 53.8% | 0.29 | 0.54 | 0.38 |
| Logistic Regression | 52.4% | 0.53 | 0.52 | 0.52 |
| SVM | 49.7% | 0.53 | 0.50 | 0.46 |
| Random Forest | 49.0% | 0.52 | 0.49 | 0.45 |
| LSTM | 48.6% | 0.53 | 0.49 | 0.42 |

### Main Findings

- No model exceeded the baseline accuracy in the experiments reported in the thesis.
- The baseline benefited from the greater proportion of upward days in the test set, but never identified a downward day.
- Logistic Regression achieved the highest weighted F1-score and the most balanced classification of upward and downward days.
- SVM and Random Forest identified downward days more effectively than upward days.
- The LSTM did not provide an advantage over traditional models in the reported experiment.

These findings highlight the difficulty of predicting daily stock price direction using historical market data alone.

### Effect of Feature Engineering

| Model | Accuracy without engineered features | Accuracy with engineered features |
|---|---:|---:|
| Logistic Regression | 49.3% | 52.4% |
| SVM | 48.3% | 49.7% |
| Random Forest | 51.7% | 49.0% |

Engineered features improved the reported accuracy of Logistic Regression and SVM, but not Random Forest.

### Feature Importance

Engineered features accounted for approximately **56%** of the total impurity-based feature importance in Random Forest.

However, feature importance describes how variables contribute to reducing impurity during tree construction. It does not establish that those variables improve performance on unseen data.

## Limitations

- The analysis focuses on a single stock and a limited historical period.
- The models rely on historical market data and technical indicators.
- News, company fundamentals and geopolitical events are not included.
- Financial patterns can change over time, limiting generalization.
- The models received different levels of hyperparameter tuning.
- LSTM sequence construction reduces the number of test observations compared with the traditional models.

## Running the Notebook

Install the main dependencies:

```bash
pip install numpy pandas matplotlib scikit-learn tensorflow yfinance jupyter
```

Open `notebooks/ProgettoML.ipynb` in Jupyter or in VS Code with Python and Jupyter support, select a Python environment with the required dependencies, and run the cells in order.

An internet connection is required for downloading market data.

## Reproducibility Note

The results presented in this README refer to the experiments documented in the submitted thesis.

Some saved outputs in the accompanying notebook differ from the thesis results, particularly for Random Forest and LSTM. The thesis should therefore be used as the reference for the numerical results summarized above.

## Author

**Riccardo Striano**

Bachelor’s thesis in Artificial Intelligence and Data Analytics  
University of Trieste
````



