# Predictive Modeling for Health Insurance
## Project Overview
This project aims to predict health insurance claims using regression analysis. The goal is to estimate future claim costs based on customer demographics, health factors, and past claim history. The objective is to estimate future claim costs based on factors such as age, hereditary disease, and customer's health. This can aid insurance companies in setting accurate premiums and improving risk assessment.
## Data
- **Dataset Source:** [Kaggle Health Insurance Dataset](https://www.kaggle.com/datasets/sureshgupta/health-insurance-data-set/data)
- **Description:** The dataset includes 15,000 records with 13 features.
  - age: Age of the policyholder
  - sex: Gender of the policyholder
  - weight: Weight of the policyholder in kg
  - bmi: Body mass index of the policyholder
  - hereditary_diseases: Indicates if a policyholder has hereditary diseases (no-disease=0; disease=1)
  - no_of_dependents: Number of dependents of the policyholder
  - smoker: Indicates if the policyholder is a smoker (non-smoker=0; smoker=1)
  - bloodpressure: Blood pressure reading of the policyholder
  - diabetes: Indicates if the policyholder has diabetes (non-diabetic=0; diabetic=1)
  - regular_ex: Indicates if the policyholder regularly exercises (no-exercise=0; exercise=1)
  - job_title: Job title of the policyholder
  - city: The city where the policyholder resides
  - claim: The amount claimed by the policyholder
- **Preprocessing:**
  - **Data Cleaning:** Addressed missing values using K-Nearest Neighbors (KNN) and mode imputation for categorical features.
  - **Normalization:** Scaled the bloodpressure feature using StandardScaler for consistency in comparisons.
  - **Log:** Applied log transformation to claim to handle its right-skewness and stabilize variance.
## Methodology
- **Exploratory Data Analysis (EDA):**
   - **Distribution of Claim Costs:** Claim costs are right-skewed with a median of $9,546 and a mean of $12,543.
   - **Correlation Analysis:** Strong positive correlation with claim and smoker (correlation coefficient of 0.76), indicating that smoking status has a significant impact on claim costs.
   - **Feature Importance:** In Random Forest model, `smoker` and `age` were identified as the top two predictors of claim cost.
   - **Claim Amount Trends:** Noted a right skew in claim amounts with a notable peak at the high end, suggesting that most claims are clustered around a maximum threshold. This suggests that there exists a maximum a claim may have, causing anything above to be at near that maximum.
   - **Cluster Analysis:** 3 distinct customer clusters were found in the data.
     - The first cluster had younger individuals with lower BMI and lower claim amounts. The second cluster was older but medium for others. The last cluster was widely distributed amongst every feature but had high claim amount.
     - This suggests that for the first cluster, since they are younger, they are more likely to be fit, causing any health issues to be minor. For the second cluster, they are a bit older and average in health, causing average claim amounts. For the third cluster, it shows that those who have very high claim amounts could be any customer since the distribution is wide in every feature.

- **Model Selection:**
   - **Base Models:** Random Forest Regression was used as the baseline model with the lowest RMSE of 2419.83.
   - **Ensemble Models:** Decision Tree Bagging model with RMSE of 2715.16. Random Forest and catboost Stacking model with RMSE of 2488.24.
   - **Best model:** The Random Forest model emerged as the best performer due to its accuracy and robustness, with an RMSE of 2419.83. It provided the most accurate predictions with reduced error margins.

- **Evaluation Metrics:**
   - **Root Mean Squared Error (RMSE):** Provided error in the same units as the target and highlighted larger errors more.
- **Error Analysis:**
  - **Residual Analysis:** Residuals (differences between actual and predicted claim costs) are larger for higher claim values. This indicates potential bias in the model.
  - **Model Comparison:** Error metric (RMSE) for the Random Forest model is lower compared to Decision Forest, highlighting its robustness. However, residuals analysis indicates that the model can still improve, particularly in handling outliers and having only sightly marginal differences to true values.
## Results
- **Model Performance:**
  - **Random Forest:** This model was preferred due to its superior accuracy and ability.
  
- **Key Insights:**
  - **Clustering Insights:** Three distinct customer segments were identified: Cluster 1: Younger, healthier individuals with lower claim amounts. Cluster 2: Moderately aged individuals with average health and claims. Cluster 3: Older individuals with high claim amounts and significant health issues.
  - **High Impact Features:** `smoker` and `age` were found to be the most influential factors in determining claim amount. Being a smoker and older age lead to higher claims.
## Additional Resources
- **Detailed Write-Up:** [View Article](https://scribe.rip/@jazzed_olivine_llama_204/predictive-modelling-for-health-insurance-claims-910c7e99bfc5)
- **PDF Version of Jupyter Notebook:** [View PDF](https://drive.proton.me/urls/Y0630XYC1C#9YAGAVl9QbX4)
