# 🏡 California Housing Price Prediction

## 📌 Introduction
Predicting house prices is a classic problem in data science and machine learning, with significant real-world applications in real estate, urban planning, and finance.  

The **California Housing dataset**, widely used for regression tasks, provides information on housing prices across various districts in California along with socio-economic and geographical features such as median income, average occupancy, and proximity to key areas.

Accurate price prediction models are valuable because they help stakeholders — from homebuyers and sellers to policymakers and investors — make informed decisions.  
Understanding the factors that drive housing prices also sheds light on broader economic and demographic patterns.

## 🎯 Objective
This project aims to:

- **Explore and analyze** the California Housing dataset to identify key factors influencing house prices  
- **Build and evaluate predictive models** to estimate housing values  
- **Visualize feature relationships** and assess the importance of socio-economic variables  
- **Provide insights** into how income, location, and housing characteristics contribute to pricing trends  

---

## 🗂️ Dataset

📌 **Source**: [California Housing Dataset — scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)  

### Original Columns
- `MedInc` → Median income in block group  
- `HouseAge` → Median house age in block group  
- `AveRooms` → Average number of rooms per household  
- `AveBedrms` → Average number of bedrooms per household  
- `Population` → Block group population  
- `AveOccup` → Average household occupancy  
- `Latitude` → Block group latitude  
- `Longitude` → Block group longitude  
- `MedHouseVal` → Median house value (target variable)  

### Engineered Features
- `Rooms_per_Household` → Average number of rooms per household  
- `Bedrooms_per_Room` → Ratio of bedrooms to total rooms  
- `Population_per_Household` → Average population per household  

### Final Feature Set
```python
feature_cols = [
    'MedInc', 'HouseAge', 'AveRooms', 'AveBedrms',
    'Population', 'AveOccup', 'Latitude', 'Longitude',
    'Rooms_per_Household', 'Bedrooms_per_Room', 'Population_per_Household'
]
X = df[feature_cols]
y = df['LogMedHouseVal']
## 🔍 Data Exploration & Preparation

### Exploratory Data Analysis (EDA)
- Correlation heatmap to visualize pairwise feature relationships
- **Key observations:**
  - Median Income positively correlated with Median House Value
  - Bedrooms per Room negatively correlated with Median House Value
  - Redundant correlations (e.g., total rooms vs. total bedrooms) highlighted the need for careful feature selection

### Log Transformation of House Prices
- The target variable, `MedHouseVal`, was right-skewed
- Log transformation applied to normalize distribution and stabilize variance

### Log Transformation of Skewed Features
- Features log-transformed:
  - Average Rooms
  - Population
  - Population per Household
- Improved variance stability and model interpretability

---

## ⚙️ Model Building
- Models trained using pipelines with preprocessing and encoding:
  - Linear Regression
  - Random Forest Regression

### Results
| Model                   | RMSE   | R² Score |
|--------------------------|--------|----------|
| Linear Regression        | 0.333  | 0.657    |
| Random Forest Regression | 0.236  | 0.829    |

### Comparative Analysis
- Random Forest significantly outperforms Linear Regression
- Captures non-linear relationships and complex feature interactions
- Linear Regression remains useful for interpretability but explains less variability
- Final visualizations and evaluations were performed on the **Random Forest model**

---

## 📈 Model Evaluation & Visualizations
- Residual vs Predicted Plot: errors distributed around zero
- Histogram of Actual vs Predicted Prices: predicted distribution closely matched actual prices
- Scatter Plot (Actual vs Predicted): points clustered near the diagonal, with some spread at extremes
- Learning Curve: strong generalization with mild overfitting, stabilizing as training size increased
- Feature Importance Plot: highlighted contribution of each predictor

---

## 🔑 Feature Importance Analysis
- Median Income → dominant predictor
- Longitude & Latitude → capture regional differences (coastal vs. inland)
- House Age, Bedrooms per Room, Population per Household → smaller but notable contributions
- Overall: income and location are the strongest drivers of housing values

---

## 📊 Cross-Validation (Random Forest)
- RMSE scores (5 folds): `[0.238, 0.233, 0.236, 0.241, 0.238]`
- Mean RMSE: 0.237
- Standard Deviation: 0.003

These results confirm that the model is **accurate, stable, and generalizes well** across data splits.

---

## 💡 Business Insights, Conclusion & Suggestions

### Business Insights
- Income-driven affordability: higher-income areas command higher housing prices
- Location sensitivity: coastal and urban regions attract premiums, inland areas remain more affordable
- Secondary factors: structural and demographic features influence buyer preferences but play a supporting role

### Conclusion
- Income levels and geographic positioning are primary forces shaping California’s housing market
- Other features add nuance but are less influential

### Suggestions
- Targeted policy measures: focus affordable housing initiatives on high-income, high-demand regions
- Investment strategies: prioritize coastal/urban projects for premium development, explore inland for affordable housing
- Data enrichment: future studies can include employment rates, school quality, and transport access for deeper insights

---

## 🛠️ Libraries Used
- pandas → data manipulation and preprocessing
- numpy → numerical operations
- matplotlib → data visualization
- seaborn → statistical graphics
- scikit-learn → model building, pipelines, and evaluation
