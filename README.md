# Telco Customer Churn Prediction

This project explores customer churn in a telecommunications dataset and builds a
baseline machine-learning model to identify customers who are likely to leave.
The analysis is implemented in a Jupyter notebook using pandas, visualization
libraries, and scikit-learn.

## Project Status

The project currently contains:

- Data cleaning and type conversion
- Exploratory data analysis (EDA)
- Feature preparation and one-hot encoding
- A stratified train/test split
- A scaled, class-balanced logistic regression baseline
- Cross-validation and test-set evaluation

Further model comparison and tuning are not implemented yet.

## Dataset

The dataset is stored in
[`data/Telco-Customer-Churn.csv`](data/Telco-Customer-Churn.csv). It contains
7,043 customer records and includes:

- **Customer information:** gender, senior-citizen status, partner, and dependents
- **Services:** phone, internet, security, backup, protection, support, and streaming
- **Account information:** tenure, contract, billing, payment method, and charges
- **Target:** `Churn`, where `Yes` means the customer left and `No` means the
  customer stayed

The CSV is excluded from version control by the repository's `.gitignore` file.

## Repository Structure

```text
telco-churn-prediction/
├── data/
│   └── Telco-Customer-Churn.csv   # Input dataset
├── notebook/
│   └── analysis.ipynb              # Cleaning, EDA, preparation, and modeling
├── learninglog.md                  # Progress notes and observations
├── .gitignore
└── README.md
```

The `venv/` directory may exist locally as the Python virtual environment, but
it is intentionally ignored and is not part of the project source.

## Requirements

- Python 3.12 or later
- JupyterLab or a Jupyter-compatible notebook interface
- pandas
- NumPy
- Matplotlib
- Seaborn
- scikit-learn

## Setup

From the repository root, create and activate a virtual environment if one does
not already exist:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
```

Install the required packages:

```powershell
python -m pip install pandas numpy matplotlib seaborn scikit-learn jupyterlab
```

## Run the Analysis

The notebook reads the CSV using a path relative to the `notebook/` directory.
Start JupyterLab from that directory so the data path resolves correctly:

```powershell
Set-Location .\notebook
..\venv\Scripts\python.exe -m jupyter lab analysis.ipynb
```

Alternatively, open `notebook/analysis.ipynb` in VS Code after selecting the
project's `venv` interpreter, then run the cells from top to bottom.

# Analysis Workflow

## Goal
Predict which telecom customers will leave, and recommend who to target with retention offers.

## Data
Kaggle Telco Customer Churn: 7,032 customers (after removing 11 rows with
no billing history), 19 features, 26.6% churn rate.

## Method
1. EDA: histograms, boxplots, churn rate by category, correlation heatmap
2. Cleaning: merged redundant categories, one-hot encoding, stratified 80/20 split
3. Models: logistic regression (baseline), random forest, gradient boosting
4. Evaluation: 5-fold cross-validation on the train set, then one final test

## Results
| Model | CV ROC-AUC |
|---|---|
| Logistic Regression | 0.845 |
| Random Forest | 0.844 |
| Gradient Boosting | 0.847 |

All three performed about the same. Logistic regression test AUC: 0.841.

## Key findings
- New customers (low tenure) are the highest risk
- Month-to-month contracts, fiber optic internet and electronic check payment
  go with much higher churn
- Two-year contracts almost never churn (~3%)

## Business recommendation
Customers who are new, on a month-to-month contract, using fiber internet and paying by electronic check are the most likely to leave. A simple model can find these customers reasonably well (AUC about 0.84). The company should focus retention efforts on this group, for example by encouraging longer contracts and automatic payment. Target customers and moving month-to-month customers to longer contracts and automatic payment.

## Learning Log

Development observations and decisions are recorded in
[`learninglog.md`](learninglog.md).


## License

No license has been specified yet.
