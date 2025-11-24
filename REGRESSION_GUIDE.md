# Regression Analysis Guide

> This page provides a general guide for identifying and designing a regression project.

You have a regression problem when:

- You are predicting a **single target variable**.
- The target is **numerical and continuous**, such as:
  - price  
  - temperature  
  - fuel efficiency  
  - height, weight  
  - cost, revenue  
- The goal is to estimate or forecast a numeric quantity.

If all the above are true, you are working on a regression task.

The following lists key tasks for regression projects.

---

## 1. Identify the Target Variable

- What is the exact name of the target variable:
- Confirm the target is continuous and numeric:
- Confirm no unexpected values, missing values, or outliers that distort the target:
- Why is this target meaningful for prediction:

## 2. Review Feature Variables

- What features are available:
- Are they numerical, categorical, or mixed:
- Are any features irrelevant or redundant:
- Are any features ethically or legally restricted:
- Could any features cause leakage (contain future information):
- Provide at least one example of possible leakage in this domain:

## 3. Understand Relationships and Distributions

- What patterns or correlations appear between features and the target:
- Are any features strongly correlated with each other (multicollinearity):
- Are any transformations needed (log, square, scaling, normalization):
- Are there noticeable outliers:
- How were outliers handled:

## 4. Select the Regression Model

- What baseline model did you choose (e.g. Linear Regression):
- Why is it appropriate for this dataset:
- What assumptions does this model make (linearity, independence, variance):
- Are those assumptions approximately met:

## 5. Evaluate Model Performance

Common regression metrics include:

| Abbrev | Full Name                    | Definition                                                                                      | When to Use                                                                     |
|--------|------------------------------|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| MAE    | Mean Absolute Error          | Average size of prediction errors; treats all errors equally regardless of direction.           | A simple, easy-to-interpret metric when outliers should not dominate the score. |
| MSE    | Mean Squared Error           | Average of squared errors; penalizes larger errors more heavily.                                | When large mistakes are costly and should be penalized more.                    |
| RMSE   | Root Mean Squared Error      | Square root of MSE; returns error to original units, representing the typical prediction error. | To get error expressed in the same units as target and to penalize big errors. |
| R^2    | Coefficient of Determination | Measures how much variation in the target variable the model explains (1=perfect, 0=mean model).| To measure overall model fit and how well features explain target variation. |

Key questions:

- Which metrics did you use:
- How were these metrics chosen:
- What is the model’s performance:
- Is the performance reasonable for this application:
- What errors matter more to stakeholders (overestimating vs underestimating) and why:

## 6. Improve the Model

There are several ways to improve a regression model.
These techniques help address nonlinearity, poor scaling, irrelevant features, overfitting, or general lack of predictive power.

### Use Polynomial Features
- Adds curved relationships between features and the target.
- Useful when the baseline linear model underfits or when scatterplots show curved patterns.

### Add Scaling / Normalization 
- Ensures features are on comparable scales.  
- Especially important for models sensitive to feature magnitude (Linear Regression with regularization, Polynomial Regression).

### Improve Feature Selection (may require engineering additional features) 
- Removing irrelevant variables can reduce noise.
- Creating useful new combinations or transformations can reveal hidden structure (e.g. Body Mass Index from height and weight)

### Add Regularization (Ridge, Lasso)
- Helps prevent overfitting by shrinking coefficients or setting them exactly to zero.  
- Useful when there are many correlated features or unstable weights.

### Enhance Pipelines
- Combine preprocessing and modeling into one repeatable process.
- Improves reproducibility and reduces human error.

Key questions:

- What alternate models or improvements were tried (e.g., Polynomial Regression, Ridge, Lasso):
- Why did you try each improvement (what problem was it addressing):
- Which changes improved performance, based on metrics:
- Why do you think those changes helped:
- Which changes did NOT improve performance:
- Why might those approaches have failed or underperformed:
- If you had more time, which additional improvements might you try next:

## 7. Validate and Compare Models

- How were models compared:
- Which metrics were compared:
- Which model performed best:
- How do you know:
- Does the best-performing model generalize well:
- Discuss:

## 8. Real-World Interpretation

- What does the model tell us about how the features influence the target:
- What practical insights can stakeholders use:
- Is the model stable and reliable enough for real decisions:
- How do you know: 
- Any limitations or caveats:

---

Document your model development (and these questions) in a **PROJECT_SUMMARY.md**.
Add your opening content at the beginning and then answer all questions (see the midterm [PROJECT_SUMMARY_TEMPLATE.md](https://github.com/denisecase/ml-04/blob/main/PROJECT_SUMMARY_TEMPLATE.md) for more about front matter.)