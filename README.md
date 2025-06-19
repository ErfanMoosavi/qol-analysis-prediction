# Quality of Life Analysis

This project analyzes a dataset containing various metrics related to the quality of life in different countries. The main goal is to clean the data, handle missing values, and apply a machine learning model (Linear Regression) to predict missing entries, particularly in the "Health" column.

## Features

- **Data Preprocessing**
  - Loads CSV-based country-level quality-of-life data
  - Drops irrelevant or redundant columns
  - Detects and visualizes missing values

- **Missing Value Imputation**
  - Identifies zero entries in the "Health" column as missing
  - Uses Linear Regression to predict and fill missing "Health" values based on other numerical features

- **Visualization**
  - Generates visual insights using:
    - Seaborn heatmaps
    - Histograms and distribution plots

- **Machine Learning**
  - Applies `LinearRegression` from scikit-learn
  - Fits model on remaining data to predict missing values

## Technologies Used

- **Python** — Primary programming language
- **Pandas** — Data handling and manipulation
- **NumPy** — Numerical computation
- **Matplotlib & Seaborn** — Visualization
- **scikit-learn** — Regression model and evaluation

## Project Workflow

1. **Load and Inspect Data**
   - Dataset is loaded from `Dataset/quality_of_life.csv`
   - Drops unnecessary columns like `Unnamed: 0` and `Rank`

2. **Clean Data**
   - Inspects basic statistics and structure
   - Detects and locates anomalies (zeros in `Health`)

3. **Handle Missing Values**
   - Locates the sample with missing `Health`
   - Builds a linear regression model using the rest of the dataset
   - Predicts and replaces the missing value

4. **Visualization**
   - Uses seaborn and matplotlib for data exploration
   - Displays value distributions, correlations, and missing value heatmaps

## File Structure

```
.
├── Dataset/
│   └── quality_of_life.csv
├── quality_of_life.ipynb
└── README.md
```

## Example Code Snippet

```python
# Train model on available data
x_train = df.drop(["Health", "Country"], axis=1).drop(134)
y_train = df.drop(134)["Health"]
lin_reg = LinearRegression().fit(x_train, y_train)

# Predict missing value
pred = lin_reg.predict(df.drop(["Health", "Country"], axis=1).iloc[134].values.reshape(1, -1))
df.loc[134, "Health"] = pred[0]
```

## Notes

- The model assumes linearity between features and `Health`
- Can be extended by trying other regressors (e.g., RandomForest, SVR)
- Exploratory Data Analysis (EDA) steps are basic but can be enriched

## Future Extensions

- Add classification or clustering models
- Build an interactive dashboard using Streamlit
- Incorporate socio-economic indicators from external datasets
