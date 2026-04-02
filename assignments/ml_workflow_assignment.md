# ML Workflow Assignment

## Task 1: Identifying the Label and Data Leakage Column

**Label column:** `repeat_purchase_flag`

**Justification:** This column represents the target variable we are trying to predict — whether a customer made a repeat purchase within 30 days (1) or not (0). It is the ground truth outcome that the model needs to learn to predict.

**Column that would introduce data leakage if used as a feature:** `discount_used_on_repeat_order`

**Justification:** This column contains information about the discount applied on the repeat purchase order itself. Since it only exists for customers who actually made a repeat purchase (and is likely missing or not applicable for non-repeat customers), including it as a feature would allow the model to directly see information from the future/target event, causing severe data leakage and making the model unrealistically accurate during training but useless in production.

## Task 2: Steps that should have been completed before training a Gradient Boosting model

1. **Exploratory Data Analysis (EDA)**  
   - **Why it matters:** Before training any model, we must understand the data distribution, check for missing values, outliers, class imbalance in the target (`repeat_purchase_flag`), relationships between features and the target, and correlations among features. Skipping EDA can lead to building a model on flawed or misunderstood data, resulting in poor generalization or wasted effort on irrelevant/complex models.

2. **Data Preprocessing and Feature Engineering**  
   - **Why it matters:** Real-world datasets often contain missing values, categorical variables, skewed distributions, or require creating new meaningful features (e.g., `recency_score`, `monetary_value`, customer tenure, etc.). Proper preprocessing (handling missing values, scaling, encoding) and thoughtful feature engineering should be done before training a complex model like Gradient Boosting. Jumping straight to modeling without this step usually leads to suboptimal performance and makes it harder to interpret or improve the model later.

---

**Note:** In a proper ML workflow, we should follow these steps in order:  
1. Problem Understanding & Business Objective  
2. Data Collection & Understanding  
3. Exploratory Data Analysis (EDA)  
4. Data Cleaning & Preprocessing  
5. Feature Engineering  
6. Data Splitting (Train/Validation/Test)  
7. Baseline Modeling  
8. Model Training & Hyperparameter Tuning  
9. Evaluation & Interpretation  
10. Deployment & Monitoring  

Training a Gradient Boosting model should come much later in the pipeline, not as the first modeling step.
