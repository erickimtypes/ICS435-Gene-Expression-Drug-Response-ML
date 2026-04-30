# Gene Expression-Based Drug Response Prediction (ICS 435 Final Project)

## Overview
This project builds machine learning models to predict how cancer cell lines respond to drug treatments using gene expression data. The objective is to model the relationship between high-dimensional genomic features and drug response, measured as log fold change (LFC), using supervised learning techniques.

This work has applications in precision medicine, where predicting drug sensitivity can help guide treatment decisions and reduce ineffective therapies.

---

## Dataset

This project uses publicly available pharmacogenomic datasets:

- **Gene Expression (CCLE / DepMap)**
  - File: `OmicsExpressionTPMLogp1HumanProteinCodingGenes.csv`
  - ~19,000 gene features per cell line

- **Drug Response (PRISM Repurposing Dataset)**
  - File: `Repurposing_Public_24Q2_Extended_Primary_Data_Matrix.csv`
  - LFC values representing drug sensitivity

After merging:
- **902 overlapping cell lines**
- Final dataset consists of gene expression features (X) and drug response values (y)

---

## Project Pipeline

The project follows a complete machine learning workflow:

1. **Data Preprocessing**
   - Merge gene expression and drug response datasets
   - Filter for a single drug (AZ-628)
   - Handle missing values
   - Train/Validation/Test split (64% / 16% / 20%)

2. **Baseline Models**
   - Ridge Regression (baseline)
   - Support Vector Regression (SVR)
   - Random Forest
   - XGBoost

3. **Hyperparameter Optimization**
   - RandomizedSearchCV with 5-fold cross-validation
   - Models tuned: SVR, Random Forest, XGBoost

4. **Final Evaluation**
   - Best model: XGBoost
   - Evaluated on a held-out test set

---

## Results

### Final Model Performance (Tuned XGBoost)
- **Test RMSE:** 0.825  
- **Test R²:** 0.574  

The RMSE indicates that predictions are, on average, within ~0.825 LFC units of the true response.  
The R² value shows that the model explains approximately **57.4% of the variance** in drug response, which is strong performance given the noisy and high-dimensional nature of biological data.

### Key Findings
- Nonlinear models outperform linear models
- Hyperparameter tuning significantly improves performance
- XGBoost effectively captures complex gene–drug relationships


