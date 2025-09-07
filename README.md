# 🏡 California Housing Price Prediction

## 📌 Project Overview
This project predicts housing prices in California using the **California Housing dataset**, a popular dataset for regression tasks. The dataset includes socio-economic and geographical features such as median income, house age, average occupancy, and location information.

Accurate price predictions help stakeholders—homebuyers, sellers, policymakers, and investors—make informed decisions, while understanding the drivers of housing prices provides insights into economic and demographic trends.

---

## 🗂️ Dataset

### Initial Columns
- `MedInc` – Median income of households in a district  
- `HouseAge` – Median age of houses in a district  
- `AveRooms` – Average number of rooms per household  
- `AveBedrms` – Average number of bedrooms per household  
- `Population` – Population of the district  
- `AveOccup` – Average household occupancy  
- `Latitude` – Geographical latitude  
- `Longitude` – Geographical longitude  

Additional features were engineered for better insights:
- `Rooms_per_Household`  
- `Bedrooms_per_Room`  
- `Population_per_Household`  

---

## 🔍 Exploratory Data Analysis (EDA)
- **Log Transformation:** Applied to skewed features (e.g., house prices, population) to normalize distributions.  
- **Correlation Heatmap:** Revealed strong positive correlation between median income and house prices, and negative correlation between bedrooms per room and house value.  
- **Scatter Plots:**  
  - Median income strongly drives house prices.  
  - Geographic factors (latitude & longitude) influence regional housing trends.  
  - Engineered features highlight housing density and quality.

- **Distribution Analysis:** Features such as income and population show skewness; outliers were handled during preprocessing.

---

## 🏗️ Model Building & Evaluation
Two regression models were implemented:

### Linear Regression
- RMSE: 0.333  
- R² Score: 0.657  

### Random Forest Regression
- RMSE: 0.236  
- R² Score: 0.829  

**Insights:**
- Random Forest outperforms Linear Regression, effectively capturing non-linear relationships.
- Cross-validation confirms model stability: mean RMSE = 0.237, SD = 0.003.

---

## 📊 Feature Importance (Random Forest)
Key predictors of house prices:
- **Median Income:** Most influential  
- **Longitude & Latitude:** Capture regional differences  
- **House Age, Bedrooms per Room, Population per Household:** Secondary influence  

---

## 💡 Business Insights
- **Income-driven affordability:** Higher-income areas have higher housing prices.  
- **Location sensitivity:** Coastal and metropolitan regions are premium markets.  
- **Secondary factors:** House characteristics affect buyer preferences but are less influential.  

---

## ✅ Conclusion & Suggestions
- Median income and geographic location are primary drivers of housing prices in California.  
- Random Forest is recommended for precise predictions.  

**Recommendations:**
1. **Policy:** Focus affordable housing initiatives on high-demand, high-income areas.  
2. **Investment:** Prioritize coastal/metropolitan areas for premium projects; explore inland areas for affordable housing.  
3. **Data Enrichment:** Incorporate features like school quality, transport accessibility, and employment rates for better insights.

---

