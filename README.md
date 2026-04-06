# Customer Behavior Data Analysis

A comprehensive end-to-end data analysis project on customer behavior, covering data cleaning, exploratory data analysis (EDA), statistical testing, data transformation, feature engineering, and machine learning preprocessing — all using Python.

---

## Project Structure

```
customer-behavior-analysis/
│
├── Customer_behavior_data.ipynb   # Main Jupyter Notebook (full analysis pipeline)
├── customer_data.xlsx             # Primary customer dataset
├── performance_data.xlsx          # RFM scores (Recency, Frequency, Monetary)
├── additional_data.xlsx           # Extended dataset with combined features
└── README.md
```

---

## Dataset Overview

| File | Description |
|---|---|
| `customer_data.xlsx` | Core customer info: demographics, purchase behavior, churn status |
| `performance_data.xlsx` | RFM scores per customer (Recency, Frequency Score, Monetary Score) |
| `additional_data.xlsx` | Merged dataset with all features combined |

**Key Columns:**
`CustomerID`, `Gender`, `Age`, `Income`, `City`, `Region`, `Frequency_of_Purchases`, `Average_Purchase_Amount`, `Customer_Lifespan_Months`, `Purchase_Channel`, `Date_of_Purchase`, `Churn_Status`, `Recency`, `Frequency_Score`, `Monetary_Score`

---

## Project Pipeline

### 1. Data Cleaning
- Handled missing values using `SimpleImputer` (median for `Income`, mode for `City`)
- Removed inconsistent entries (e.g., `'XXXX'` in `Customer_Lifespan_Months`)
- Corrected data types (`datetime`, `int`, `float`)
- Removed duplicate records

### 2. Data Integration
- Merged `customer_data` with `performance_data` on `CustomerID` (inner join)
- Concatenated with `additional_data` for a complete final dataset

### 3. Exploratory Data Analysis (EDA)
- **Frequency Analysis** — Purchase channel distribution
- **Percentage Analysis** — Channel-wise percentage share
- **Group-By Analysis** — Median purchase amount by city
- **Pivot Table** — Churn status vs. RFM scores
- **Cross-Tab Analysis** — Churn distribution across cities

### 4. Data Visualization
| Chart Type | Insight |
|---|---|
| Bar Chart | Purchase channel frequency |
| Stacked Bar | Churn by city |
| Pie Chart | Purchase channel percentage |
| Line Chart | Average purchase amount by city |
| Histogram | Distribution of average purchase amount |
| Scatter Plot | Frequency of purchases vs. purchase amount |
| Heatmap | Correlation matrix of numeric features |
| Box Plot | Purchase amount by churn status |
| KDE Plot | Distribution of Age & Purchase Amount |

### 5. Data Transformation
- **Shapiro-Wilk Test** — Normality testing for numeric columns
- **Square Root Transformation** — Applied on `Age`
- **Log Transformation** — Applied on `Age`
- **Box-Cox Transformation** — Applied on `Age`

### 6. Statistical Analysis
| Test | Variables | Purpose |
|---|---|---|
| One-Sample t-test | `Average_Purchase_Amount` | Test against hypothesized mean (68) |
| Independent t-test | `Churn_Status` vs `Average_Purchase_Amount` | Compare churned vs. retained customers |
| ANOVA (Levene's Test) | `Frequency_of_Purchases` by `City` | Variance equality across cities |
| Chi-Square Test | `Purchase_Channel` vs `Region` | Independence between categorical variables |
| Pearson Correlation | `Frequency_of_Purchases` vs `Average_Purchase_Amount` | Linear relationship |
| Linear Regression (OLS) | `Frequency_of_Purchases` → `Average_Purchase_Amount` | Predictive modeling |

### 7. Feature Engineering
- Extracted `Year`, `Month`, `Date` from `Date_of_Purchase`
- Created `Customer_Value` and `CLV` (Customer Lifetime Value) features
- **Binning** — `Customer_Lifespan_Months` → `engagement_level` (Low / Moderate / High)
- **Label Encoding** — `Churn_Status`
- **One-Hot Encoding (Dummies)** — `Gender`, `City`, `Region`, `Purchase_Channel`

### 8. Feature Selection (ML Preprocessing)
- Prepared `X` and `y` for:
  - **Regression task** — predicting `CLV`
  - **Classification task** — predicting `Churn_Status`

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Matplotlib | Data visualization |
| Seaborn | Statistical plots |
| Scikit-learn | Imputation, encoding |
| SciPy | Statistical tests |
| Statsmodels | OLS Linear Regression |

---

## Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/ManasSriv10/customer-behavior-analysis.git
   cd customer-behavior-analysis
   ```

2. **Install dependencies:**
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn scipy statsmodels openpyxl
   ```

3. **Launch the notebook:**
   ```bash
   jupyter notebook Customer_behavior_data.ipynb
   ```

---

## Key Insights

- Churned customers show different average purchase amounts compared to retained customers (validated via t-test)
- Purchase channel distribution reveals dominant shopping preferences
- RFM scores vary significantly between churned and non-churned customers
- Age and purchase amount distributions required transformation to approach normality
- Feature engineering created meaningful inputs for downstream ML modeling

---

## Notes

- The dataset includes customers from multiple US cities: Chicago, New York, Houston, Los Angeles
- All three Excel files must be in the same directory as the notebook to run successfully
- The notebook is structured sequentially — run cells in order for correct results

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## License

This project is open source and available under the [MIT License](LICENSE).
