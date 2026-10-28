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

## Analysis Workflow

The notebook performs the following steps:

1. Load the CSV into a pandas DataFrame.
2. Inspect the shape, data types, and class distribution.
3. Convert `TotalCharges` to numeric values and replace its 11 empty values
   with `0`.
4. Remove `customerID`, which is an identifier rather than a predictive feature.
5. Convert `Churn` from `Yes`/`No` to the binary target values `1`/`0`.
6. Explore churn rates, numerical distributions, boxplots, categorical churn
   rates, and correlations.
7. Combine `No internet service` and `No phone service` with the corresponding
   `No` category.
8. Separate the features (`X`) from the target (`y`) and one-hot encode
   categorical features.
9. Split the data into 80% training and 20% test sets using stratification and
   `random_state=42`.
10. Train a logistic regression pipeline with `StandardScaler` and
    `class_weight="balanced"`.
11. Evaluate the model with five-fold cross-validation, ROC-AUC,
    classification metrics, and a confusion matrix.

## Baseline Results

The current logistic regression baseline achieved:

- Cross-validation ROC-AUC: approximately **0.84**
- Test ROC-AUC: approximately **0.84**
- Churn recall: approximately **78%**
- Churn precision: approximately **51%**

The balanced class weights prioritize finding churners, which improves recall
but also creates more false-positive churn predictions and therefore lowers
precision. The model is suitable as a baseline for comparing future approaches,
not as a production deployment model.

## Learning Log

Development observations and decisions are recorded in
[`learninglog.md`](learninglog.md).

## Next Steps

- Compare logistic regression with tree-based and ensemble classifiers.
- Tune the classification threshold based on retention-campaign costs.
- Add hyperparameter tuning and a consistent preprocessing pipeline.
- Compare models using precision, recall, F1-score, ROC-AUC, and a
  precision-recall curve.
- Add model interpretation and error analysis.
- Document the data source and licensing information.

## License

No license has been specified yet.
