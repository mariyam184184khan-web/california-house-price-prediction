# 🏡 California Housing Price Prediction

## 📌 Project Overview
Predicting house prices is a classic problem in data science and machine learning, with real-world applications in real estate, urban planning, and investment.  
This project analyzes the **California Housing dataset** to:

- Explore key factors influencing housing prices  
- Build and evaluate predictive models for price estimation  
- Provide actionable insights for real estate and policy decisions  

---

## 🗂️ Dataset
The dataset includes socio-economic, geographic, and housing features for various California districts.  

**Key Columns:**

- `MedInc` — Median income  
- `HouseAge` — Average house age  
- `AveRooms` — Average rooms per household  
- `AveBedrms` — Average bedrooms per household  
- `Population` — District population  
- `AveOccup` — Average occupancy per household  
- `Latitude` — Geographical latitude  
- `Longitude` — Geographical longitude  
- `Rooms_per_Household` — Engineered feature: average rooms per household  
- `Bedrooms_per_Room` — Engineered feature: bedroom-to-room ratio  
- `Population_per_Household` — Engineered feature: population per household  

**Target Variable:**  
- `MedHouseVal` (log-transformed for modeling)

```python
feature_cols = [
    'MedInc', 'HouseAge', 'AveRooms', 'AveBedrms',
    'Population', 'AveOccup', 'Latitude', 'Longitude',
    'Rooms_per_Household', 'Bedrooms_per_Room', 'Population_per_Household'
]
y = np.log(df['MedHouseVal'])
## 🔍 Exploratory Data Analysis (EDA)

### Correlation Analysis
- Strong positive correlation between `MedInc` and house prices  
- Negative correlation between `Bedrooms_per_Room` and prices  
- Moderate correlations among other features identified  

### Scatter Plots
- Median income and geographic location are strong predictors  
- House age has minor influence  

### Feature Distributions
- Right-skewed features (e.g., `AveRooms`, `Population`) were log-transformed  
- Engineered features highlight housing density and quality  

---

## ⚙️ Modeling Approach

Two models were trained and evaluated using pipelines:

| Model                     | RMSE   | R² Score |
|----------------------------|--------|-----------|
| Linear Regression          | 0.333  | 0.657     |
| Random Forest Regression   | 0.236  | 0.829     |

**Model Selection:**  
Random Forest outperformed Linear Regression, capturing non-linear relationships and complex feature interactions, making it ideal for precise predictions.

---

## 📈 Random Forest Analysis

- **Residual Analysis:** Checked residuals vs predicted values for reliability  
- **Actual vs Predicted:** Strong alignment observed  
- **Learning Curve:** Model adequately trained without overfitting  

### Feature Importance

| Feature                                      | Importance      |
|----------------------------------------------|----------------|
| `MedInc`                                     | Highest        |
| `Longitude`                                  | High           |
| `Latitude`                                   | High           |
| `HouseAge` / `Bedrooms_per_Room` / `Population_per_Household` | Moderate |

### Cross-Validation (5-fold)
```python
RMSE scores: [0.238, 0.233, 0.236, 0.241, 0.238]
Mean RMSE: 0.237
Std Dev: 0.003
## 💡 Business Insights
- **Median Income** is the dominant driver of housing prices  
- **Geographic location** significantly impacts value (coastal vs inland areas)  
- **Secondary factors** such as house age and household composition contribute modestly  

### Recommendations
1. Focus affordable housing policies on high-demand areas  
2. Target investments in coastal/metropolitan regions for premium developments  
3. Incorporate additional features (school quality, transport, employment rates) for better predictive insights  

---

## 🛠️ Tech Stack
- **Language:** Python  
- **Libraries:** pandas, numpy, matplotlib, seaborn, scikit-learn  
- **Modeling:** Linear Regression, Random Forest Regression  
- **EDA & Stats:** Correlation heatmaps, scatter plots, log transformations  

---

## 📝 Conclusion
The project demonstrates that **income levels and geographic positioning** are the primary determinants of California housing prices.  
Random Forest Regression provides robust predictions, effectively modeling complex feature interactions, and is well-suited for practical applications in real estate planning and policy-making.
