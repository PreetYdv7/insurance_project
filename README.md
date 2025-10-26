# Practice Project: Insurance Cost Analysis

This project conducts an end-to-end analysis of a medical insurance dataset to understand the factors driving annual insurance costs and to build a robust model for predicting them. The dataset includes key policyholder attributes: `age`, `gender`, `bmi`, `no_of_children`, `smoker` status, and `region`.

## Project Workflow

### 1. Data Cleaning

The analysis begins with essential data cleaning. The dataset is loaded from a CSV, and proper headers are assigned. Missing values, initially marked as `'?'`, are converted to `NaN`, and the corresponding rows are dropped to ensure the integrity of the models.

### 2. Exploratory Data Analysis (EDA)

EDA provides critical insights:

- A regression plot shows a positive, albeit scattered, correlation between **BMI and charges**.
- A boxplot reveals a stark difference in cost distribution between **smokers and non-smokers**, with smokers facing significantly higher charges.
- This is quantitatively confirmed by a correlation matrix, which identifies **`smoker`** status as the single most influential predictor, showing a strong positive correlation ($r \approx 0.79$) with `charges`.

### 3. Model Development & Evaluation

For model development, several regression algorithms are built and compared:

- **Simple Linear Regression** (using only `smoker`): $R^2 = 0.623$
- **Multiple Linear Regression** (all features): $R^2 = 0.751$
- **Polynomial Regression (Degree 2) with Pipeline**: To capture non-linear relationships, this model was built using `StandardScaler` and `PolynomialFeatures`, boosting the $R^2$ to $0.846$.

### 4. Model Refinement

For final validation, the data was split into training and testing sets. A Ridge Regression model was tested, but the top-performing model was a **Polynomial Ridge Regression (Degree 2)**. This model achieved the highest $R^2$ score of **0.878** on the unseen test data, demonstrating its ability to accurately explain nearly 88% of the variance in insurance charges.
