# 🏡 California Housing Price Prediction

## 📌 Project Overview
Predicting house prices is a classic problem in data science and machine learning, with real-world applications in real estate, urban planning, and investment. This project uses the **California Housing dataset**, which includes socio-economic and geographical features such as median income, house age, average rooms, population, and location to predict housing values.

Accurate price prediction models help stakeholders—homebuyers, sellers, policymakers, and investors—make informed decisions and understand factors driving housing prices.

---

## 🎯 Objective
- Explore and analyze the California Housing dataset to identify key factors influencing house prices.
- Build and evaluate predictive models, including **Linear Regression** and **Random Forest Regression**.
- Visualize feature relationships and assess the importance of socio-economic variables.
- Provide actionable insights on how income, location, and housing characteristics impact pricing trends.

---

## 🗂️ Dataset & Features
The dataset contains the following features used in this project:

```python
feature_cols = [
    'MedInc', 'HouseAge', 'AveRooms', 'AveBedrms',
    'Population', 'AveOccup', 'Latitude', 'Longitude',
    'Rooms_per_Household', 'Bedrooms_per_Room', 'Population_per_Household'
]
## 🎯 Target Variable
```python
y = np.log(df['MedHouseVal'])  # log-transformed median house value
## 🧩 Engineered Features
- **Rooms_per_Household:** Average rooms per household  
- **Bedrooms_per_Room:** Ratio of bedrooms to total rooms  
- **Population_per_Household:** Average number of people per household  

---

## 🧹 Data Preprocessing & EDA
- **Dataset exploration:** `.info()`, `.describe()` for understanding data types and statistics  
- **Feature engineering:** Added rooms/bedrooms/population ratios  
- **Visualization:** Scatter plots, distribution plots, and correlation heatmaps  
- **Log Transformation:** Target and skewed features transformed for better model performance  

### Key Insights from EDA
- Median Income strongly correlates with house prices  
- Bedrooms per Room negatively correlates with house prices (overcrowding indicator)  
- Geographic features (Latitude & Longitude) influence regional price variations  

---

## 🛠️ Modeling & Evaluation
Two models were trained using a pipeline:

| Model                    | RMSE   | R² Score |
|--------------------------|--------|----------|
| Linear Regression        | 0.333  | 0.657    |
| Random Forest Regression | 0.236  | 0.829    |

### Key Takeaways
- Random Forest outperforms Linear Regression due to its ability to capture non-linear relationships  
- Cross-validation confirms the model’s stability:  
  `Mean RMSE = 0.237`, `Std = 0.003`  

---

## 📊 Random Forest Analysis
- **Residual Analysis:** Residual vs predicted plots show well-distributed errors  
- **Actual vs Predicted:** Scatter and histogram plots confirm strong predictive performance  
- **Learning Curve:** Shows model converges well with sufficient data  

### Feature Importance
- **Median Income** is the most influential predictor  
- **Geographic factors** (Longitude & Latitude) are significant  
- Other features (House Age, Bedrooms per Room, Population per Household) contribute moderately  

---

## 💡 Business Insights & Recommendations
- **Income-driven affordability:** Higher median income areas have higher housing prices  
- **Location sensitivity:** Coastal and metropolitan regions command premium pricing  
- **Secondary factors:** House age and household composition influence buyer preferences but are less critical  

### Suggestions
- Focus affordable housing initiatives in high-demand, high-income regions  
- Investment strategies should prioritize coastal/metropolitan projects, with inland areas for budget-friendly developments  
- Enrich data with additional features like school quality or transportation accessibility for improved predictions  

---

## 📌 Conclusion
The California Housing dataset analysis shows that **median income and location are the dominant drivers** of house prices, while structural and demographic factors provide additional insights. **Random Forest Regression** provides a robust, accurate model suitable for real-world decision-making in housing investment and policy planning.

## 🛠️ Libraries / Dependencies
The following Python libraries were used in this project:

```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import mean_squared_error, r2_score
