# Magazine Sales & Game-Day Demand Forecasting Case Study

> Built a predictive analytics framework to forecast magazine sales based on opponent strength, game conditions, historical performance, and promotional factors, followed by an operational inventory optimization decision.

**Author:** Amisha Farhana Shaik  
**Project Type:** Business Analytics Case Study | Predictive Modeling | Demand Forecasting  

---

## Business Problem

CSU wants to forecast magazine sales for upcoming games and determine:

- What factors drive magazine demand?
- How do weather, opponent rank, and promotional events impact sales?
- Is the model statistically reliable?
- How many magazines should be ordered to maximize profit?

Magazines:
- Selling price = $30  
- Purchase cost = $10  
- Salvage value = $5  

Magazines must be ordered before the season begins.

---

## Dataset Overview

Source: Casestudy2.csv  

Key Variables:

**Quantitative:**
- Week In Season
- Opponent Preseason Rank
- Preseason Ticket Sales
- CSU Preseason Rank
- Kickoff Temperature
- Home Game Number
- Opponent & CSU Previous Season Wins/Losses

**Qualitative:**
- Throwback Jersey (1/0)
- Conference Game (1/0)
- Homecoming (1/0)
- Game Day Weather
- Opponent

Data cleaning steps included:
- Removing missing rows & columns :contentReference[oaicite:2]{index=2}
- Encoding categorical variables (One-hot encoding)
- Converting ticket sales to numeric format

---

## Exploratory Data Analysis

### Correlation Heatmap

Identified relationships among:
- Week In Season
- Opponent Rank
- Ticket Sales
- Kickoff Temperature
- Home Game Number
- Magazine Sales :contentReference[oaicite:3]{index=3}

### Key Observations

- Ticket sales moderately correlate with magazine sales.
- Temperature shows a mild positive relationship.
- Strong collinearity between Week In Season and Home Game Number.
- Throwback jerseys increase average sales significantly.

---

## Model Development

### Base Linear Regression

Target:
Magazine Sales (Units)

Features:
Selected quantitative and encoded qualitative predictors.

Train-Test Split:
80% training / 20% testing.

---

## Diagnostic Analysis

### 1️⃣ Non-Linearity

Residual plots showed mostly random patterns with slight spread at extremes :contentReference[oaicite:4]{index=4}  
Conclusion: Linear assumption largely holds.

---

### 2️⃣ Autocorrelation

Durbin-Watson Statistic ≈ 2.64 :contentReference[oaicite:5]{index=5}  

Interpretation:
- Slight negative autocorrelation
- Not severe

GLS and HAC corrections produced similar results:
- MSE ≈ 452,734
- R² ≈ 0.48

Lagged variable did not improve performance.

---

### 3️⃣ Heteroscedasticity

Residual spread slightly increases at higher predicted values but no clear cone shape :contentReference[oaicite:6]{index=6}  
Conclusion: No strong heteroscedasticity concern.

---

### 4️⃣ Outliers & High Leverage Points

- Observation 28 identified as outlier :contentReference[oaicite:7]{index=7}
- Observations 14 & 33 flagged as high-leverage points
- Recommended: Compare model performance with and without these observations

---

### 5️⃣ Multicollinearity (VIF Analysis)

High VIF values:
- Week In Season (≈19.8)
- Home Game Number (≈20.3)

Recommendation:
- Remove or combine correlated predictors
- Consider PCA if dimensionality reduction is required :contentReference[oaicite:8]{index=8}

---

## Forecasting & Operational Decision

After training the final model:

Predicted average magazine sales:
≈ 2,700 units :contentReference[oaicite:9]{index=9}

---

## Inventory Optimization

Given:

Selling price = $30  
Cost = $10  
Salvage value = $5  

Expected demand ≈ 2,700 units

Under simplified assumption (mean demand forecast):

Optimal order quantity ≈ 2,700 magazines :contentReference[oaicite:10]{index=10}

---

## Technical Workflow

Load & Clean Data  
        ↓  
Encode Qualitative Variables  
        ↓  
EDA (Heatmaps, Scatterplots, Violin Plots)  
        ↓  
Train-Test Split  
        ↓  
Fit OLS Model  
        ↓  
Diagnostics (DW, Residuals, VIF, Outliers)  
        ↓  
GLS & HAC Robustness Checks  
        ↓  
Forecast Demand  
        ↓  
Operational Inventory Decision  

---

## Technical Skills Demonstrated

- Data Cleaning & Encoding
- Exploratory Data Analysis
- Correlation Heatmaps
- Linear Regression Modeling
- Residual Diagnostics
- Durbin-Watson Test
- Multicollinearity (VIF)
- Outlier Detection (Studentized Residuals)
- High Leverage Detection
- GLS & HAC Corrections
- Lagged Variable Modeling
- Train-Test Validation
- Demand Forecasting
- Profit Optimization Logic

---

## Business Insights

- Promotional factors (Throwback Jersey) significantly increase sales.
- Opponent strength and preseason metrics influence demand.
- Seasonal timing and game order matter.
- Multicollinearity between timing variables must be managed carefully.
- Robust regression diagnostics are critical before operational decisions.

---

## Why This Case Study Matters

This project demonstrates:

- Translating statistical modeling into operational strategy.
- Conducting full regression diagnostics before decision-making.
- Evaluating robustness via GLS/HAC corrections.
- Connecting prediction outputs to profit-based inventory decisions.

This reflects real-world sports marketing analytics and retail demand forecasting.

---

## Applications

Sports Analytics | Retail Demand Forecasting | Marketing Analytics | Inventory Optimization | Predictive Modeling | Business Decision Analytics
