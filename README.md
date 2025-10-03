# Quality of Life Analysis

## 📌 Overview

**Quality of Life Analysis** is a project that analyzes country-level metrics related to quality of life.
It focuses on **data cleaning, missing value handling, and prediction of missing entries** using **Linear Regression**, particularly targeting the "Health" column.

---

## ✨ Features

This project provides a robust workflow for preprocessing, imputing missing values, and visualizing quality-of-life metrics.

* **Data Preprocessing** → Loads CSV-based data, drops irrelevant columns, and inspects for missing values.
* **Missing Value Imputation** → Predicts missing "Health" values using Linear Regression.
* **Visualization** → Generates insights using Seaborn heatmaps, histograms, and distribution plots.
* **Machine Learning** → Uses `LinearRegression` from scikit-learn for predicting missing data.

---

## 🚀 Installation & Dependencies

Install required Python packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

---

## ⚡ Project Workflow

1. **Load and Inspect Data**

   * Dataset loaded from `Dataset/quality_of_life.csv`
   * Drops unnecessary columns like `Unnamed: 0` and `Rank`

2. **Clean Data**

   * Inspects basic statistics and structure
   * Detects anomalies (zeros in `Health` column)

3. **Handle Missing Values**

   * Locates the missing `Health` sample
   * Trains Linear Regression on the rest of the data
   * Predicts and fills the missing value

4. **Visualization**

   * Explores data using Seaborn and Matplotlib
   * Plots value distributions, correlations, and missing value heatmaps

---

## 🗂 File Structure

```
.
├── Dataset/
│   └── quality_of_life.csv
├── quality_of_life.ipynb
└── README.md
```

---

## 🧩 Example Code Snippet

```python
# Train model on available data
x_train = df.drop(["Health", "Country"], axis=1).drop(134)
y_train = df.drop(134)["Health"]
lin_reg = LinearRegression().fit(x_train, y_train)

# Predict missing value
pred = lin_reg.predict(df.drop(["Health", "Country"], axis=1).iloc[134].values.reshape(1, -1))
df.loc[134, "Health"] = pred[0]
```

---

## 📊 Notes

* Assumes linearity between features and `Health`
* Can be extended using other regressors (RandomForest, SVR, etc.)
* Basic EDA is included; further exploration can be added

---

## 🔮 Future Extensions

* Add classification or clustering models
* Build an interactive dashboard using Streamlit
* Integrate socio-economic indicators from external da
