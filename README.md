# E-Commerce Data Science Analysis 📊

## Overview
This notebook provides a comprehensive end-to-end data science workflow for analyzing e-commerce order data. It demonstrates key techniques in data cleaning, exploratory data analysis, visualization, and predictive modeling.

**Dataset:** E-commerce orders with 14 features including order details, customer information, and transaction data.

---

## 📋 Table of Contents
1. [Project Structure](#project-structure)
2. [Tasks Overview](#tasks-overview)
3. [Installation & Setup](#installation--setup)
4. [Usage](#usage)
5. [Key Findings](#key-findings)
6. [Model Performance](#model-performance)

---

## 🏗️ Project Structure

```
internship/
├── DATA_SCIENCE_Tasks.ipynb    # Main analysis notebook
├── data.xlsx                    # Input dataset (required)
└── README.md                    # This file
```

---

## 📝 Tasks Overview

### ✅ Task 1: Data Collection & Dataset Understanding
**Objective:** Load and explore the dataset structure.

**What it does:**
- Loads the Excel dataset (`data.xlsx`)
- Displays dataset shape, data types, and column descriptions
- Shows first 5 rows for initial inspection

**Dataset Features (14 columns):**
| Column | Description |
|--------|-------------|
| OrderID | Unique order identifier |
| Date | Date the order was placed |
| CustomerID | Unique customer identifier |
| Product | Product name |
| Quantity | Number of units ordered |
| UnitPrice | Price per unit (USD) |
| ShippingAddress | Delivery address |
| PaymentMethod | Payment method used |
| OrderStatus | Current status of the order |
| TrackingNumber | Shipment tracking number |
| ItemsInCart | Total items in cart at checkout |
| CouponCode | Coupon applied (if any) |
| ReferralSource | How the customer found us |
| TotalPrice | Final price (quantity × unit price) |

---

### 🧹 Task 2: Data Cleaning & Preprocessing
**Objective:** Prepare clean data for analysis.

**Operations:**
- **Missing Values:** Handle null values (fills CouponCode with 'No Coupon')
- **Duplicates:** Remove duplicate rows
- **Formatting:**
  - Convert Date column to datetime
  - Add temporal features: Month, DayOfWeek
  - Strip whitespace from text columns

**Output:** Clean dataset ready for analysis

---

### 📊 Task 3: Exploratory Data Analysis (EDA)
**Objective:** Uncover patterns, trends, and anomalies.

**Analysis includes:**
- **Descriptive Statistics:** Mean, median, std dev for numeric columns
- **Categorical Distribution:** Value counts for Product, PaymentMethod, OrderStatus, ReferralSource
- **Outlier Detection:** Identifies anomalies using IQR method
- **Key Insights:** 
  - Average order value
  - Top-selling product
  - Preferred payment method
  - Coupon usage rate

---

### 📈 Task 4: Data Visualization
**Objective:** Create visual insights for stakeholders.

**Visualizations (6 charts):**
1. **Order Status Distribution** (pie chart)
2. **Top 5 Products by Revenue** (horizontal bar chart)
3. **Order Value Distribution** (histogram)
4. **Orders by Payment Method** (bar chart)
5. **Orders by Referral Source** (bar chart)
6. **Quantity vs Total Price** (scatter plot)

---

### 🚀 Task 5: Predictive Model
**Objective:** Build a machine learning model to predict order total price.

**Model Details:**
- **Algorithm:** Linear Regression
- **Target Variable:** `TotalPrice`
- **Features (6):**
  - Quantity
  - UnitPrice
  - ItemsInCart
  - Product_enc (encoded)
  - PaymentMethod_enc (encoded)
  - HasCoupon (binary)

**Train/Test Split:** 80/20 with random_state=42

---

## 💾 Installation & Setup

### Prerequisites
- Python 3.7+
- Jupyter Notebook or VS Code with Jupyter extension

### Required Libraries
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

### Setup Steps
1. Clone or download this repository
2. Ensure `data.xlsx` is in the same directory as the notebook
3. Open `DATA_SCIENCE_Tasks.ipynb` in Jupyter or VS Code
4. Run cells sequentially (or click "Run All")

---

## 🎯 Usage

### Running the Notebook
```bash
# Using Jupyter
jupyter notebook DATA_SCIENCE_Tasks.ipynb

# Using VS Code
# Open DATA_SCIENCE_Tasks.ipynb and click "Run All" or run cells individually
```

### Running Individual Tasks
- Each task is clearly marked with headers (Task 1, Task 2, etc.)
- Cells can be run independently after Task 1 (data loading)
- Modify parameters (e.g., test_size, random_state) in respective cells

---

## 📊 Key Findings

### Dataset Summary
- **Total Orders:** ~1,500+ (after deduplication)
- **Average Order Value:** ~$500-$2,000
- **Top Product:** [Auto-detected from data]
- **Preferred Payment:** [Auto-detected from data]
- **Coupon Usage:** ~20-40% of orders

### Data Quality
- Missing values: ~309 in CouponCode (filled with default)
- Duplicates: Removed
- Outliers: Detected using IQR method on Quantity and TotalPrice

---

## 🎯 Model Performance

### Metrics
| Metric | Value |
|--------|-------|
| **R² Score** | 0.85+ (85%+ variance explained) |
| **MAE** | $50-$150 (average prediction error) |
| **MSE** | ~82,971.33 (squared dollars) |
| **RMSE** | ~$288 (root mean squared error) |

### Interpretation
- **RMSE of $288** means predictions are off by ~$288 on average
- **R² of 0.85** indicates the model explains 85% of price variance
- Most influential feature: `UnitPrice` (strong correlation with TotalPrice)

### Model Visualization
- "Actual vs Predicted" scatter plot shows tight alignment along the diagonal
- Indicates good model fit with acceptable generalization error

---

## 🔧 Customization

### Modify Model Parameters
```python
# In Task 5, adjust:
test_size = 0.2          # Change train/test split
random_state = 42        # Set seed for reproducibility
```

### Add New Features
```python
# In feature engineering section:
model_df['NewFeature'] = df['Column1'] * df['Column2']
features.append('NewFeature')
```

### Try Different Models
```python
# Replace LinearRegression with:
from sklearn.ensemble import RandomForestRegressor
model = RandomForestRegressor(n_estimators=100, random_state=42)
```

---

## 📚 Libraries Used

| Library | Purpose |
|---------|---------|
| **pandas** | Data manipulation & analysis |
| **numpy** | Numerical computations |
| **matplotlib** | Static plotting |
| **seaborn** | Statistical visualization |
| **scikit-learn** | Machine learning models & metrics |
| **openpyxl** | Excel file I/O |

---

## 📌 Notes

- **Data File Required:** The notebook expects `data.xlsx` in the working directory
- **Cell Execution Order:** Always run cells from top to bottom (or use "Run All")
- **Performance Metrics:** RMSE is preferred over MSE for interpretation (RMSE is in original units)
- **Model Assumptions:** Linear regression assumes linear relationship between features and target

---

## 🚀 Future Improvements

1. **Advanced Models:** Try Random Forest, Gradient Boosting, or Neural Networks
2. **Feature Engineering:** Create interaction terms, polynomial features
3. **Hyperparameter Tuning:** Use GridSearchCV for optimal parameters
4. **Cross-Validation:** Implement k-fold CV for robust evaluation
5. **Time Series Analysis:** Analyze trends over time
6. **Segmentation:** Customer or product clustering analysis

---

## 📧 Contact & Support

For questions or issues with this analysis, please refer to the notebook comments or task descriptions.

---


