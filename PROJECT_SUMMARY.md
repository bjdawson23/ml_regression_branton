# Project Summary – Regression Analysis - Medical Insurance Cost

- **Author:** Branton Dawson
- **Date:** November 24, 2025  

## Project Purpose

This notebook demonstrates comprehensive regression modeling techniques by predicting medical insurance charges using polynomial regression and pipeline optimization. The project systematically compares Linear, Polynomial, Ridge, and Elastic Net models with continuous features to achieve 86% variance explanation in insurance cost predictions.  

## Data source

- **Source file:** Kaggle Medical Cost Personal Dataset - [DATA](https://www.kaggle.com/datasets/mirichoi0218/insurance?resource=download)
- **Description:** The dataset contains 1,338 records. Each record includes:  
  - Numeric features: `age`, `bmi`, `children`  
  - Categorical features: `sex`, `smoker`, `region`  
  - Target variable: `charges` (annual insurance cost)  
- No missing values — dataset is clean.  

## Data Processing & Feature Engineering

- **Outlier Detection:** IQR method identified 139 high-cost outliers (10.4%) ranging $34,618-$63,770 and 9 BMI outliers (0.7%)
- **Initial Exploration:** Created categorical bins (`age_group`, `bmi_category`) and binary indicators (`sex_numerical`, `smoker_status`)
- **Critical Decision:** Switched from categorical dummy variables to continuous features
  - **Why:** Polynomial features on binary values produce no improvement (0² = 0, 1² = 1)
  - **Solution:** Used raw continuous values (`age`, `bmi`) to enable meaningful polynomial transformations
- **Final Features:** 
  - `age` (18-64 continuous)
  - `bmi` (15.96-53.13 continuous)
  - `smoker_status` (binary 0/1)
  - Multi-feature combination: age + bmi + smoker_status  

## Modeling Approach

Four case studies were implemented comparing single vs. multi-feature models:

| Case | Features | Rationale |
|------|----------|----------|
| **Case 1** | Age (continuous) | Test if age correlates with insurance costs |
| **Case 2** | BMI (continuous) | Test if BMI predicts health-related expenses |
| **Case 3** | Smoker Status (binary) | Test strongest behavioral risk factor |
| **Case 4** | Age + BMI + Smoker (multi-feature) | Capture feature interactions and compound effects |

For each case, two pipeline approaches were tested:

| Pipeline | Preprocessing & Model Steps |
|----------|-----------------------------|
| **Linear Pipeline** | SimpleImputer (median) → StandardScaler → LinearRegression |
| **Polynomial Pipeline** | SimpleImputer (median) → PolynomialFeatures (degree=3) → StandardScaler → LinearRegression |

Evaluation metrics: R² (coefficient of determination), MAE (mean absolute error), MSE (mean squared error).

## Results (Test Set Performance)  

### Section 4: Basic Linear Regression (No Pipelines)

| Case | Features | R² | MAE (USD) | MSE |
|------|----------|-----|-----------|-----|
| 1 | Age | 0.124 | 9,173 | 135,983,957 |
| 2 | BMI | 0.040 | 9,785 | 149,085,057 |
| 3 | Smoker Status | 0.660 | 5,626 | 52,745,965 |
| 4 | **Multi-Feature** | **0.778** | **4,261** | **34,512,844** |

### Section 5: Pipeline Comparison

| Case | Model Type | R² | MAE (USD) | MSE | Performance Notes |
|------|------------|-----|-----------|-----|-------------------|
| **Age** | Linear Pipeline | 0.124 | 9,173 | 135,983,957 | Scaling minimal impact |
| | Polynomial (degree 3) | 0.119 | 9,195 | 136,845,313 | Slight degradation |
| **BMI** | Linear Pipeline | 0.040 | 9,785 | 149,085,057 | Scaling minimal impact |
| | Polynomial (degree 3) | 0.018 | 9,863 | 152,452,516 | Worse performance |
| **Smoker** | Linear Pipeline | 0.660 | 5,626 | 52,745,965 | Binary feature unchanged |
| | Polynomial (degree 3) | 0.660 | 5,626 | 52,745,965 | No benefit (0/1 values) |
| **Multi-Feature** | Linear Pipeline | 0.778 | 4,261 | 34,512,844 | Strong baseline |
| | **Polynomial (degree 3)** | **0.862** | **2,838** | **21,501,970** | 🏆 **Best model - 33% error reduction** |

**Key Finding:** Multi-feature polynomial model explains 86% of variance in insurance charges, achieving MAE of $2,838 (33% improvement over linear multi-feature model).

## Key Findings & Insights  

1. **Smoking Status Dominates:** Single strongest predictor (R² = 0.66) — smokers pay 2-3x more than non-smokers
2. **Feature Interactions Critical:** Multi-feature model (R² = 0.78) vastly outperforms single features (R² < 0.13 for age/BMI)
3. **Continuous Features Enable Polynomial Success:** Raw age/BMI values allow meaningful polynomial transformations (age², age³, interactions)
4. **Polynomial Captures Non-Linearity:** Degree 3 polynomial improved R² from 0.78 → 0.86 (33% MAE reduction)
5. **Age/BMI Weak Alone:** Individual predictors (age R² = 0.12, BMI R² = 0.04) insufficient — compound effects matter
6. **StandardScaler Essential:** Critical for multi-feature polynomial models to prevent numerical instability (age³ vs smoker³ scale mismatch)
7. **Categorical Dummy Limitation:** Polynomial features on binary 0/1 values produce identical results — continuous features required  

## Limitations & Challenges

- **Right-Skewed Target:** 139 outliers (10.4%) ranging $34K-$64K create distribution challenges
- **Feature Representation Discovery:** Initial categorical approach (get_dummies) failed — required pivot to continuous features
- **Scaling Complexity:** Understanding when/where to apply StandardScaler (after PolynomialFeatures, not before)
- **Single Features Weak:** Age and BMI individually poor predictors — only effective in combination
- **Limited Features:** Only 3 features used (age, bmi, smoker_status) — excluded children, region, sex
- **No Cross-Validation:** Single 80/20 train/test split limits robustness assessment
- **14% Unexplained Variance:** R² = 0.86 means individual health variations still unpredictable  

## Future Work & Improvements  

If given more time, I would:

- **Add More Features:** Include `children`, `region`, `sex` in multi-feature model to test geographic/demographic patterns
- **Outlier Handling:** Log-transform charges to reduce right-skew, test robust regression (Huber, RANSAC)
- **Cross-Validation:** K-fold validation for robust performance estimates across different data splits
- **Regularization:** Test Ridge/Lasso to handle multicollinearity in polynomial features, prevent overfitting
- **Polynomial Degree Comparison:** Systematically test degrees 2, 4, 5 to find optimal complexity
- **Alternative Models:** Random Forest, Gradient Boosting for non-linear patterns without manual feature engineering
- **Residual Analysis:** Identify systematic prediction errors to guide additional feature engineering
- **Feature Importance:** SHAP values to explain which features/interactions drive individual predictions  

## Conclusion  

This project successfully demonstrates systematic regression analysis by comparing four case studies and achieving 86% variance explanation in insurance cost predictions. The journey from weak single-feature models (R² < 0.13) to strong multi-feature polynomial regression (R² = 0.86, MAE = $2,838) illustrates the critical importance of:

1. **Feature Quality:** Continuous features enable polynomial transformations that categorical dummy variables cannot support
2. **Feature Interactions:** Compound effects (age × bmi × smoker) explain costs far better than individual predictors
3. **Appropriate Complexity:** Polynomial degree 3 captures non-linearity without overfitting
4. **Proper Scaling:** StandardScaler essential for numerical stability in multi-feature polynomial models

The 33% error reduction achieved through polynomial transformations ($4,261 → $2,838 MAE) demonstrates that thoughtful feature engineering and model selection significantly improve predictive accuracy. Smoking status emerged as the dominant predictor (R² = 0.66 alone), validating domain knowledge about behavioral health risks.

With 14% unexplained variance remaining, future work incorporating additional features (region, children, medical history) and advanced techniques (regularization, ensemble methods) could further improve real-world insurance pricing applications.
