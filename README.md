# Superstore-sales-dataset
### Data Cleaning & Preprocessing

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
  to prevent silent misparsing (default parsing assumes MM/DD/YYYY).
- **Categorical consistency check:** Verified `Ship Mode`, `Segment`, `Region`, and 
  `Category` columns — no typos, casing issues, or inconsistent labels found.

### 3. Outlier Analysis
- Applied the IQR method on the `Sales` column.
- Found 1,145 outliers (~11.7% of the dataset), with IQR bounds of approximately 
  -272.79 to 500.64.
- Decision: Flagged outliers (`Sales_Outlier_Flag` column) rather than removing them, 
  since they likely represent legitimate high-value bulk orders rather than data errors.

### 4. Preprocessing
- Added `Sales_Log` — log-transformed Sales column, useful for reducing skew in 
  future statistical analysis or modeling.
- Added `Shipping_Delay_Days` — computed as `Ship Date - Order Date`, a new feature 
  for potential delivery-time analysis.

## Challenges Faced
- The date format (DD/MM/YYYY) was not initially obvious and could have caused 
  silently incorrect date parsing if not explicitly specified.
- Deciding how to handle a large proportion (11.7%) of statistically-flagged outliers 
  required judgment — removing them would have discarded legitimate high-value data.

## Files
- `notebook.ipynb` — full code with outputs
- `report.docx` — detailed report with explanations and screenshots

## Author
Aayitijhya Ganguly (Moon)
