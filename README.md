# Customer Churn Prediction

A data analytics and machine learning project that analyzes customer purchasing behavior and predicts customer churn using RFM analysis and an XGBoost classification model.

## Project Overview

Customer churn is an important business problem because identifying customers who are likely to stop engaging with a business can support targeted retention strategies.

This project uses transactional retail data to:

- Clean and preprocess raw transaction data
- Analyze customer purchasing behavior
- Generate customer-level RFM features
- Define and identify potential churned customers
- Train a machine learning model for churn prediction
- Evaluate and improve the model
- Generate customer-level churn predictions
- Visualize insights through a Power BI dashboard

## Dataset

The project uses the **Online Retail** transactional dataset.

The original dataset contains **541,909 transaction records** and 8 columns, including:

- InvoiceNo
- StockCode
- Description
- Quantity
- InvoiceDate
- UnitPrice
- CustomerID
- Country

Data preprocessing removes records with missing customer identifiers and invalid transaction values. After cleaning, the dataset contains **397,884 records**.

## Methodology

### 1. Data Cleaning

The raw transaction data is inspected for:

- Missing values
- Invalid quantities
- Invalid prices
- Transaction anomalies

The data is then cleaned before customer-level analysis.

### 2. RFM Analysis

Customer purchasing behavior is summarized using three RFM features:

- **Recency** – how recently a customer made a purchase
- **Frequency** – how frequently a customer made purchases
- **Monetary** – how much a customer spent

These features are aggregated at the customer level and used as inputs for churn analysis.

### 3. Churn Identification

A churn label is created based on customer recency.

Customers whose purchasing inactivity exceeds the defined threshold are classified as potential churn customers.

### 4. Feature Transformation

Log transformations are applied to selected numerical features to reduce the effect of skewed distributions and improve the modelling process.

### 5. Machine Learning

An **XGBoost classifier** is used to predict customer churn.

The modelling process includes:

- Train-test splitting
- Feature selection
- Model training
- Classification evaluation
- Churn probability prediction
- Class-weight tuning to improve detection of churn cases

### 6. Model Evaluation

The model is evaluated using classification metrics including:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrix

Particular attention is given to the recall and F1-score of the churn class because identifying potential churn customers is an important objective of the project.

## Data Leakage Handling

During model development, an initial model produced unrealistically strong performance.

Further analysis identified that a feature derived directly from Recency was contributing to target leakage because the churn label itself was based on customer recency.

The affected feature was removed from the final feature set, and the model was retrained.

This provides an important modelling lesson: strong evaluation results should be investigated for possible data leakage rather than accepted without validation.

## Business Insights

The project produces customer-level churn predictions that can be used to identify customers who may require retention attention.

The resulting predictions are exported to an Excel file and can be further explored through the Power BI dashboard.

## Power BI Dashboard

A Power BI dashboard is included in the project to present customer churn analysis and prediction results in an interactive format.

The dashboard is intended to make the analytical results easier to explore from a business perspective.

## Project Structure

```text
Customer-Churn-Prediction/
│
├── notebooks/
│   └── 01_data_cleaning.ipynb
│
├── powerbi/
│   └── churnprediction.pbix
│
├── results/
│   └── customer_churn_predictions.xlsx
│
├── .gitignore
├── requirements.txt
└── README.md