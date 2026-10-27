# Telco Churn Prediction

Machine learning project to predict customer churn for a telecommunications company based on historical customer data.

## Overview

Customer churn refers to customers who discontinue their service. This project builds and evaluates classification models that predict whether a customer is likely to churn, enabling the business to target at-risk customers with proactive retention strategies.

## Dataset

The project uses a telecom customer dataset containing demographic, account, and service information, including:

- **Customer demographics** – gender, senior citizen status, partner, dependents
- **Services** – phone, internet, online security, streaming, etc.
- **Account details** – tenure, contract type, payment method, monthly/total charges
- **Target variable** – `Churn` (Yes/No)

## Tech Stack

- Python 3.12
- pandas, NumPy – data manipulation
- seaborn, matplotlib – visualization
- JupyterLab – interactive analysis

## Project Structure

```
telco-churn-prediction/
├── data/               # Raw and processed datasets
├── notebooks/          # Jupyter notebooks (EDA, modeling)
├── src/                # Source code (preprocessing, training)
├── venv/               # Python virtual environment (not tracked)
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.12+

### Setup

1. Clone the repository:

   ```bash
   git clone <repo-url>
   cd telco-churn-prediction
   ```

2. Create and activate a virtual environment:

   ```powershell
   python -m venv venv
   ./venv/Scripts/Activate.ps1
   ```

3. Install dependencies and launch JupyterLab:

   ```bash
   pip install seaborn pandas numpy jupyterlab
   jupyter lab
   ```

## Workflow

1. **Data cleaning** – handle missing values, correct data types, remove duplicates
2. **EDA** – explore churn distribution and feature relationships
3. **Feature engineering** – encode categoricals, scale numeric features
4. **Modeling** – train baseline classifiers (e.g., logistic regression, tree-based models)
5. **Evaluation** – compare models using accuracy, precision, recall, F1, and ROC-AUC

## Roadmap

- [ ] Add dataset and data dictionary
- [ ] Exploratory data analysis notebook
- [ ] Baseline model pipeline
- [ ] Hyperparameter tuning and model comparison
- [ ] Export predictions / deployment notes

## License

TBD
