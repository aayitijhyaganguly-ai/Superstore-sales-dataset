# Superstore-sales-dataset
## Data Cleaning & Preprocessing

## Objective
This project demonstrates the process of acquiring a public dataset, performing 
data cleaning, and preprocessing it using Python to prepare it for further analysis.

## Dataset
- **Source:** Kaggle — Superstore Sales Dataset (train.csv)
- **Size:** 9,800 rows × 18 columns (before cleaning)
- **Content:** Retail order-level data including order/ship dates, customer info, 
  product category, region, and sales amount.

## Tools & Libraries
- Python
- pandas
- numpy
- matplotlib

## Steps Performed

### 1. Initial Data Exploration
- Checked shape, column types, and summary statistics using `.info()`, `.describe()`
- Checked for missing values with `.isnull().sum()`
- Checked for duplicate rows with `.duplicated().sum()`

### 2. Data Cleaning
- **Missing values:** Found 11 missing values in `Postal Code` (out of 9,800 rows). 
  Dropped these rows since the missing percentage was negligible (~0.1%).
- **Duplicates:** No duplicate rows found.
- **Irrelevant columns:** Dropped `Country` column — contained only one unique value 
  ("United States"), providing no analytical value.
- **Date format correction:** `Order Date` and `Ship Date` were stored as text in 
  DD/MM/YYYY format. Explicitly parsed using `pd.to_datetime(..., format='%d/%m/%Y')` 
  to prevent silent misparsing (default parsing assumes
