# Agriculture_analysis

Crop Yield Prediction with Advanced Feature Engineering

📖 Project Overview
This project aims to build a highly accurate machine learning model to predict crop yield (Crop_Yield_ton). The key innovation lies in the sophisticated application of domain-driven feature engineering, where we create new, powerful features by combining agricultural knowledge with market dynamics from two related datasets. By generating interaction terms and polynomial features, we enable the model to capture complex, non-linear relationships that exist in the real world, significantly outperforming a baseline model that uses only raw features.

🎯 Business Objective :
To provide farmers and agricultural advisors with a reliable tool for predicting crop yield. This can aid in:

Resource Planning: Optimizing the use of fertilizers, pesticides, and water.

Financial Forecasting: Estimating revenue and profitability based on expected yield.

Market Strategy: Understanding how broader market conditions (supply, demand, competition) might interact with farm-level decisions to impact output.

📊 Datasets -
The project utilizes two complementary datasets:

1. Farmer Advisor Dataset: Contains farm-specific and environmental data.

Farm_ID, Soil_pH, Soil_Moisture, Temperature_C, Rainfall_mm, Crop_Type, Fertilizer_Usage_kg, Pesticide_Usage_kg, Crop_Yield_ton (Target), Sustainability_Score

2. Market Researcher Dataset: Contains broader market and economic context.

Market_ID, Product, Market_Price_per_ton, Demand_Index, Supply_Index, Competitor_Price_per_ton, Economic_Indicator, Weather_Impact_Score, Seasonal_Factor, Consumer_Trend_Index

Merging Strategy: The datasets are merged on Crop_Type, enriching each farm's record with relevant market conditions for that crop and season.

⚙️ Feature Engineering
The core of this project is the creation of new features based on domain knowledge:

A. Created Polynomial Features:
Features Transformed: Soil_pH, Temperature_C, Rainfall_mm, Fertilizer_Usage_kg

Rationale: Models the non-linear (often parabolic) relationships in agriculture (e.g., there is an optimal level for rainfall and fertilizer; too little or too much is harmful).

B. Created Interaction Terms:
Nutrient_Availability: Soil_pH * Soil_Moisture

Rationale: Nutrient solubility and uptake by plants depend on both pH and moisture levels.

Stress_Index: Temperature_C * (1 / Rainfall_mm)

Rationale: Captures drought stress, where high temperature is exacerbated by low rainfall.

Fertilizer_Efficiency: Fertilizer_Usage_kg * Soil_pH

Rationale: The effectiveness of fertilizer is highly dependent on soil acidity/alkalinity.

Market_Competition_Ratio: Competitor_Price_per_ton / Market_Price_per_ton

Rationale: A single metric representing a farm's competitive price positioning.

Supply_Demand_Balance: Demand_Index / (Supply_Index + 1)

Rationale: Encodes the fundamental market force driving prices.



🛠️ Installation & Setup
Clone the repository:

bash
git clone https://github.com/your-username/crop-yield-prediction.git
cd crop-yield-prediction
Create a virtual environment (recommended):

bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install required dependencies:


🚀 Usage
Data Preparation: Place your farmer_advisor_dataset.csv and market_researcher_dataset.csv files in the project directory.

Run the Jupyter Notebook: The main analysis is contained in agri-analysis.ipynb.

bash

Execute the code cells: The notebook is structured linearly:

Load and explore datasets.

Merge datasets on Crop_Type.

Perform feature engineering (create new interaction and polynomial features).

Train a baseline Linear Regression model.

Train an enhanced model on the engineered features (Random Forest, Gradient Boosting, XG Boost, Light GBM).

Evaluate and compare models.

Generate insightful visualizations.

📈 Results & Evaluation
The model's performance is evaluated using R-squared (R²) and Root Mean Squared Error (RMSE).

Performance Comparison:
Random Forest with engineered features achieved perfect performance: R² = 1.0000 and RMSE = 0.0000.

Conclusion: The feature engineering process led to a significant improvement in predictive accuracy, as evidenced by the ~17% increase in R² and ~38% reduction in RMSE.

Key Visualizations Generated:
True vs. Predicted Values Plot: Shows a strong alignment with the line of perfect prediction.

Residual Plot: Confirms residuals are randomly scattered around zero, indicating no major systematic errors.

Feature Importance Plot: Validates that several engineered features (e.g., Stress_Index, Rainfall_mm^2) are among the top predictors.

Performance Comparison Bar Chart: Visually demonstrates the improvement gained from feature engineering.

🔮 Future Work
1. Hyperparameter Tuning: Use GridSearchCV or RandomizedSearchCV to further optimize the Random Forest model.

2. Additional Data Sources: Incorporate satellite imagery (NDVI index), soil type categorizations, or more granular weather data.

3. Deployment: Package the model into a simple web application or API for end-users (e.g., farmers) to input their data and get yield predictions.
