# Telco Customer Churn Prediction

A machine learning project to predict customer churn using the Telco Customer Churn dataset.

This project was built as a hands-on learning project to understand the end-to-end machine learning workflow, including exploratory data analysis, preprocessing, model evaluation, cross-validation, and model selection.

## Project Objective

The goal is to predict whether a customer is likely to churn based on information such as:

- Customer tenure
- Monthly charges
- Total charges
- Contract type
- Internet service
- Payment method
- Technical support
- Online security
- Other customer and service-related features

Beyond prediction, the project also explores the business implications of customer churn and how a churn prediction model could help identify customers who may need retention efforts.

## Dataset

The project uses the Telco Customer Churn dataset.

The dataset contains customer demographic information, subscribed services, account information, and a binary churn target.

The target variable is:

- `Yes` — Customer churned
- `No` — Customer did not churn

The dataset is imbalanced, with approximately:

- 73.5% non-churn
- 26.5% churn

## Machine Learning Workflow

The project currently follows this workflow:

1. Data cleaning
2. Exploratory Data Analysis (EDA)
3. Feature identification
4. Train/test split
5. Preprocessing pipeline
6. Model training
7. 5-fold stratified cross-validation
8. Model comparison
9. Hyperparameter tuning
10. Final model evaluation

## Preprocessing

A `scikit-learn Pipeline` and `ColumnTransformer` were used to keep preprocessing consistent and prevent data leakage during cross-validation.

### Numerical features

- Missing values → Median imputation
- Scaling → StandardScaler

### Categorical features

- Missing values → Most-frequent imputation
- Encoding → OneHotEncoder
- Unknown categories → Ignored using `handle_unknown="ignore"`

## Models Compared

The following models were evaluated:

- Logistic Regression
- Random Forest
- Neural Network (MLP)
- XGBoost

### Cross-Validation Results

5-fold stratified cross-validation produced the following results:

| Model | Accuracy | Precision | Recall | F1 | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 0.8017 | 0.6521 | 0.5425 | 0.5916 | 0.8460 |
| Random Forest | 0.7845 | 0.6226 | 0.4789 | 0.5412 | 0.8183 |
| Neural Network | 0.7701 | 0.5784 | 0.4957 | 0.5328 | 0.7939 |
| XGBoost | 0.7803 | 0.6021 | 0.5084 | 0.5511 | 0.8222 |

Based on the cross-validation results, **Logistic Regression performed best across all five evaluation metrics** and was selected as the current model.

## Evaluation Metrics

Several metrics were used because accuracy alone can be misleading for an imbalanced churn dataset.

- **Accuracy** — Overall percentage of correct predictions
- **Precision** — How many predicted churners actually churned
- **Recall** — How many actual churners were successfully identified
- **F1 Score** — Balance between precision and recall
- **ROC-AUC** — Measures the model's ability to distinguish between churners and non-churners across classification thresholds

## Exploratory Data Analysis

Some notable patterns found during EDA include:

- Very-new customers showed substantially higher churn than long-term customers.
- Month-to-month contracts were associated with higher churn.
- Very-new customers on month-to-month contracts showed particularly high churn.
- Fiber-optic customers with month-to-month contracts also showed relatively high churn.
- Longer contracts were associated with lower churn.
- Very-new customers on two-year contracts showed extremely low observed churn in the dataset.

These observations suggest that customer tenure and contract structure may be important factors in understanding churn behavior.

## Project Status

This project is currently being developed as a learning project.

### Completed

- [x] Data cleaning
- [x] Exploratory data analysis
- [x] Feature preprocessing
- [x] Preprocessing pipeline
- [x] Logistic Regression baseline
- [x] Cross-validation
- [x] Model comparison
- [x] Initial hyperparameter experimentation

### Planned

- [ ] Finalize model tuning
- [ ] Final model evaluation
- [ ] Refactor notebook code into a structured ML project
- [ ] Experiment tracking
- [ ] Model versioning
- [ ] Build a prediction API
- [ ] Dockerize the application
- [ ] Add automated testing
- [ ] Set up CI/CD
- [ ] Deploy the model

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- XGBoost
- Jupyter / Kaggle Notebooks
- Git
- GitHub

Future stages of the project will introduce additional MLOps tools and practices.

## Repository Structure

The project currently centers around the Kaggle notebook.

The structure will evolve as the project moves from experimentation toward a more production-oriented ML workflow.

```text
telco-churn-prediction/
│
├── README.md
├── notebooks/
│   └── telco_churn.ipynb
│
└── ...
