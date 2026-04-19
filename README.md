# 📈 Crop Yield Prediction — Linear Regression Analysis

**Author:** Oluwatobi Victoria Babalola | MSc Data Science  
**Portfolio:** [bbt-portfolio.vercel.app](https://bbt-portfolio.vercel.app) | **LinkedIn:** [oluwatobi-babalola-victoria](https://www.linkedin.com/in/oluwatobi-babalola-victoria/)

---

## 📌 Project Summary

Can we predict crop yield from a single environmental factor? This project applies **simple linear regression** to Maji Ndogo agricultural survey data, systematically testing whether temperature or pollution level predicts standardised crop yield — and rigorously evaluating model assumptions through residual analysis.

---

## 🎯 Objectives

- Test whether `Ave_temps` and `Pollution_level` have a linear relationship with `Standard_yield`
- Quantify relationships using Pearson correlation across all numeric features
- Fit and evaluate simple linear regression models using Scikit-learn
- Apply 80/20 train-test split for honest generalisation testing
- Diagnose model fit through residual histogram, scatter, and actual vs predicted plots
- Identify which crop types are most sensitive to pollution using per-crop regression loops

---

## 🗃️ Dataset

Agricultural field survey data from Maji Ndogo, loaded from an SQLite database using the `FieldDataProcessor` pipeline module.

**Target variable:** `Standard_yield` — standardised yield normalised per crop type

**Features tested:**

| Feature | Description |
|---------|-------------|
| `Ave_temps` | Average temperature (°C) |
| `Pollution_level` | Pollution level (0 = clean, 1 = highly polluted) |
| `Soil_fertility` | Fertility index (0–1) |
| `Rainfall` | Annual rainfall (mm) |
| `Elevation` | Field elevation (metres) |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python 3.10 | Core language |
| Pandas | Data manipulation |
| NumPy | Numerical computation |
| Scikit-learn | Linear regression, train-test split, metrics |
| SciPy | Pearson correlation |
| Matplotlib / Seaborn | Visualisation |
| SQLAlchemy | Database connection |

---

## 📁 Repository Structure

```
crop-yield-linear-regression/
├── crop_yield_linear_regression.ipynb   ← Main analysis notebook
├── data_ingestion.py                    ← DB engine & SQL utilities
├── field_data_processor.py             ← OOP data pipeline class
├── validate_data.py                    ← Data quality tests
├── Maji_Ndogo_farm_survey_small.db     ← SQLite source database
└── README.md                           ← This file
```

---

## 🔍 Key Functions

```python
get_correlation(df, col1, col2)
# → Pearson r between any two columns

fit_linear_regression_model(df, predictor_col, target_col)
# → (model, predictions, y_values)

get_slope_intercept(model)
# → (slope, intercept)

calculate_evaluation_metrics(predictions, y_values)
# → (R², MAE, MSE, RMSE)

data_train_test_split(df, predictor_col, target_col)
# → (X_train, X_test, y_train, y_test) with 80/20 split

train_split_linear_regression_model(X_train, X_test, y_train, y_test)
# → (model, predictions, y_test)

calculate_residuals_statistics(predictions, y_test)
# → (mean_residual, std_residual)
```

---

## 💡 Key Findings

| Finding | Detail |
|---------|--------|
| Temperature correlation | r ≈ 0.007 — virtually no linear relationship |
| Pollution correlation | r ≈ -0.286 — weak but meaningful (40× stronger than temperature) |
| Model R² | ~8% — pollution explains ~8% of yield variance |
| Residual mean | ≈ 0 — model is unbiased |
| Generalisation | Train vs test metrics near-identical — consistent generalisation |
| Best next model | Multiple linear regression or Random Forest recommended |

---

## 👩‍💻 Author

**Oluwatobi Victoria Babalola**  
📧 bablotobi@gmail.com  
🌐 [bbt-portfolio.vercel.app](https://bbt-portfolio.vercel.app)  
💼 [LinkedIn](https://www.linkedin.com/in/oluwatobi-babalola-victoria/)  
🐙 [GitHub](https://github.com/TechieBbt)
