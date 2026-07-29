# Superstore Sales Prediction using Machine Learning

## Project Overview

This project focuses on analyzing and predicting transaction-level sales based on the Superstore dataset.

The main objectives are:

- Explore sales and profitability patterns through Exploratory Data Analysis (EDA)
- Identify important business drivers influencing sales performance
- Prepare the dataset for machine learning
- Build regression models to predict transaction-level sales
- Compare different ensemble learning approaches
- Optimize models using GridSearchCV

The project follows a complete data science workflow, including data cleaning, feature engineering, model training, evaluation, and model comparison.

---

# Dataset

The project uses the **Sample Superstore Dataset**, which contains transactional sales data including:

- Product categories and sub-categories
- Customer segments
- Regional information
- Shipping modes
- Quantity and discount information
- Sales and profit values

The dataset contains transaction-level records, allowing the prediction task to focus on individual sales transactions.

---

# Exploratory Data Analysis (EDA)

The exploratory analysis investigates sales and business performance across different dimensions.

Key areas analyzed:

- Sales distribution by category and sub-category
- Customer segment performance
- Regional sales patterns
- Profitability analysis
- Impact of discounts on profit margins
- Shipping mode distribution

## Key Findings

### Product Performance

Technology products generate the highest total revenue despite having fewer transactions compared to Office Supplies.

This indicates that Technology products achieve a higher average sales value per transaction.

### Profitability

Technology is also the strongest category regarding total profit.

However, some sub-categories show significant losses due to aggressive discount strategies.

### Discount Impact

The analysis shows that high discounts are strongly associated with reduced profitability.

Extreme discounts, especially between 50% and 80%, frequently lead to negative profit margins.

---

# Feature Engineering

To prepare the data for machine learning:

## Categorical Encoding

Categorical variables were transformed using one-hot encoding:

- Ship Mode
- Segment
- Region
- Category
- Sub-Category

## Feature Removal

The following columns were removed:

- Country
- City
- State
- Postal Code
- Profit

The Profit column was excluded because the prediction task focuses on sales prediction and including profit would introduce target leakage.

---

# Machine Learning Approach

## Prediction Task

The goal of the machine learning model is:

> Predict transaction-level sales based on available customer, product, and operational features.

This is a regression problem because the target variable (`Sales`) is a continuous numerical value.

---

# Models

Two ensemble regression models were evaluated:

## 1. Random Forest Regressor

Random Forest combines multiple decision trees to improve prediction stability and reduce overfitting compared to a single decision tree.

A baseline model was trained first, followed by hyperparameter optimization using GridSearchCV.

Optimized parameters included:

- Number of trees (`n_estimators`)
- Maximum tree depth (`max_depth`)
- Minimum samples required for splitting (`min_samples_split`)
- Minimum samples per leaf (`min_samples_leaf`)

---

## 2. Gradient Boosting Regressor

Gradient Boosting was used as a second ensemble approach.

Unlike Random Forest, which builds trees independently, Gradient Boosting builds trees sequentially, where each new tree focuses on correcting previous errors.

The model was evaluated both as a baseline and with GridSearchCV optimization.

---

# Model Optimization

Hyperparameter optimization was performed using:

**GridSearchCV with 5-fold cross-validation**

The objective was to identify parameter combinations that minimize the Root Mean Squared Error (RMSE).

Evaluation metrics:

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- R² Score

---

# Model Comparison

The evaluated models were:

| Model | Description |
|---|---|
| Random Forest Baseline | Default Random Forest configuration |
| Random Forest Grid Search | Optimized Random Forest |
| Gradient Boosting Baseline | Default Gradient Boosting configuration |
| Gradient Boosting Grid Search | Optimized Gradient Boosting |

The results showed that hyperparameter optimization did not automatically improve performance.

The baseline models achieved better generalization on the test dataset than some tuned configurations.

This demonstrates that:

- More complex optimization does not always lead to better predictions
- Parameter selection depends strongly on the dataset
- Model evaluation on unseen data is essential

---

# Conclusion

This project demonstrates a complete machine learning workflow for transaction-level sales prediction.

The main steps included:

1. Data exploration and business analysis
2. Feature engineering and data preparation
3. Regression model development
4. Hyperparameter optimization
5. Model comparison and evaluation

The analysis showed that ensemble learning models can capture complex relationships within sales data. However, the experiments also highlighted that baseline models can sometimes outperform optimized versions when the selected parameter ranges do not contain the ideal configuration.

The final model selection was based on test performance using RMSE and R² as the main evaluation criteria.

---

# Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Jupyter Notebook
