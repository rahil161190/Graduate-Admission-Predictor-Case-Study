# Graduate-Admission-Predictor-Case-Study

An end-to-end regression pipeline to estimate “Chance of Admit” from applicant profiles.

## 🚀 Project Overview
- **Goal**: Predict admission probability (continuous target) using GRE, TOEFL, CGPA, SOP, LOR, University Rating, Research.  
- **Models**: Linear Regression, Ridge, Lasso (α=0.1→0.01), plus OLS analysis with statsmodels.  
- **Key Achievements**:  
  - High R² (~0.82) and low RMSE (~0.061) on test set  
  - Identified CGPA, GRE, TOEFL as strongest predictors  
  - Tuned Lasso to match Linear/Ridge performance, reducing underfitting  
  - Dropped SOP & University Rating after p-value and VIF checks without loss  

## 📊 Methodology
1. **EDA & Cleaning**  
   - 500 records, no missing values or duplicates  
   - Checked distributions, skewness, kurtosis, correlations  
2. **Preprocessing**  
   - Standard scaling of all features  
   - VIF analysis to confirm no multicollinearity  
3. **Model Training & Tuning**  
   - Compare baseline Linear, Ridge (α=0.1), and Lasso (α=0.1→0.01)  
   - Evaluate MSE, RMSE, R²  
   - Use OLS for coefficient significance and assumptions testing  
4. **Assumptions Testing**  
   - Residual normality, homoscedasticity, zero mean errors  
   - Confirmed no major violations  

## 📈 Results
| Model           |  MSE   |  RMSE  |   R²   |
| --------------- | :----: | :----: | :----: |
| Linear          | 0.0037 | 0.0609 |  0.818 |
| Ridge (α=0.1)   | 0.0037 | 0.0609 |  0.818 |
| Lasso (α=0.1)   | 0.0150 | 0.1224 |  0.267 |
| Lasso (α=0.01)  | 0.0038 | 0.0617 |  0.814 |

- **OLS Summary**: Adj R² = 0.818; SOP & Rating p-values > 0.05 → removed.

## 💡 Key Insights
- **Top Predictors**: CGPA, GRE Score, TOEFL Score  
- **Regularization**: Lasso α=0.01 balances bias–variance, matching Ridge performance  
- **Feature Selection**: Dropping non-significant variables simplifies model with no loss  

