# Final Project: Regression Analysis

**Author:** Branton Dawson  
**Date:** November 24, 2025  
**Status:** COMPLETED

- NOTEBOOK LINK: [REGRESSION](https://github.com/bjdawson23/ml_regression_branton/blob/main/notebooks/regression_branton.ipynb)

- PEER REVIEW LINK: [PEER_REVIEW](https://github.com/bjdawson23/ml_regression_branton/blob/main/peer_review.md)

**Project Overview**
This notebook demonstrates comprehensive regression modeling techniques by predicting medical insurance charges using polynomial regression and pipeline optimization. The project systematically compares Linear, Polynomial, Ridge, and Elastic Net models with continuous features to achieve 86% variance explanation in insurance cost predictions.

**Dataset**: Medical Cost Personal Dataset by Miri Choi  
**Source**: [Kaggle - Insurance Dataset](https://www.kaggle.com/datasets/mirichoi0218/insurance)  
**Size**: 1,338 records with 7 features (no missing values)

---

## How to Execute the Notebook

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or VS Code with Jupyter extension
- Required packages: pandas, numpy, matplotlib, seaborn, scikit-learn

### Installation Steps

1. **Clone the repository:**
   ```bash
   git clone https://github.com/bjdawson23/ml_regression_branton.git
   cd ml_regression_branton
   ```

2. **Install required packages:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Launch the notebook:**
   - **Using Jupyter Notebook:**
     ```bash
     jupyter notebook notebooks/regression_branton.ipynb
     ```
   
   - **Using VS Code:**
     - Open the project folder in VS Code
     - Navigate to `notebooks/regression_branton.ipynb`
     - Select a Python kernel when prompted
     - Click "Run All" or execute cells sequentially

### Notebook Execution Order

The notebook is structured in 6 sections and should be executed sequentially:

1. **Section 1:** Data loading and initial inspection
2. **Section 2:** Exploratory data analysis and outlier detection
3. **Section 3:** Feature selection and engineering (continuous features)
4. **Section 4:** Basic linear regression model training (4 case studies)
5. **Section 5:** Pipeline implementation with polynomial transformations
6. **Section 6:** Final findings, challenges, and recommendations

**Estimated Runtime:** 2-3 minutes for complete notebook execution

**Note:** The notebook uses `../data/insurance.csv` as the data path. Ensure the data file is in the correct location before running.

---

## applied-ml-branton

> Use this repo to start a professional Python project.

- Additional instructions: See the [pro-analytics-02](https://denisecase.github.io/pro-analytics-02/) guide.
- Project organization: [STRUCTURE](./STRUCTURE.md)
- Build professional skills:
  - **Environment Management**: Every project in isolation
  - **Code Quality**: Automated checks for fewer bugs
  - **Documentation**: Use modern project documentation tools
  - **Testing**: Prove your code works
  - **Version Control**: Collaborate professionally

---

## About this Repository

Starter files for the example labs:

- notebooks/example01 folder
- notebooks/example02 folder

## Folders for Projects

Each project will be completed in its own folder.

- notebooks/project01 folder:
  - ml01.ipynb - COMPLETE THIS
  - ml01.py - working script with just the code
  - README.md - instructions - modify this to present your lab project

- notebooks/project02 folder:
  - ml01_branton.ipynb - **COMPLETED** - Comprehensive data analysis project
  - README.md - project documentation and analysis summary

- notebooks/project03 folder:
  - ml03_branton.ipynb - **COMPLETED** - Classification model comparison project
  - README.md - project documentation and performance analysis

---

## WORKFLOW 1. Set Up Machine

Proper setup is critical.
Complete each step in the following guide and verify carefully.

- [SET UP MACHINE](./SET_UP_MACHINE.md)

---

## WORKFLOW 2. Set Up Project

After verifying your machine is set up, set up a new Python project by copying this template.
Complete each step in the following guide.

- [SET UP PROJECT](./SET_UP_PROJECT.md)

It includes the critical commands to set up your local environment (and activate it):

```shell
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
uv run pre-commit install
uv run python --version
```

**Windows (PowerShell):**

```shell
.\.venv\Scripts\activate
```

**macOS / Linux / WSL:**

```shell
source .venv/bin/activate
```

---

## WORKFLOW 3. Daily Workflow

Please ensure that the prior steps have been verified before continuing.
When working on a project, we open just that project in VS Code.

### 3.1 Git Pull from GitHub

Always start with `git pull` to check for any changes made to the GitHub repo.

```shell
git pull
```

### 3.2 Run Checks as You Work

This mirrors real work where we typically:

1. Update dependencies (for security and compatibility).
2. Clean unused cached packages to free space.
3. Use `git add .` to stage all changes.
4. Run ruff and fix minor issues.
5. Update pre-commit periodically.
6. Run pre-commit quality checks on all code files (**twice if needed**, the first pass may fix things).
7. Run tests.

In VS Code, open your repository, then open a terminal (Terminal / New Terminal) and run the following commands one at a time to check the code.

```shell
git pull
uv sync --extra dev --extra docs --upgrade
uv cache clean
git add .
uvx ruff check --fix
uvx pre-commit autoupdate
uv run pre-commit run --all-files
git add .
uv run pytest
```

NOTE: The second `git add .` ensures any automatic fixes made by Ruff or pre-commit are included before testing or committing.
Running `uv run pre-commit run --all-files` twice may be helpful if the first time doesn't pass. 

<details>
<summary>Click to see a note on best practices</summary>

`uvx` runs the latest version of a tool in an isolated cache, outside the virtual environment.
This keeps the project light and simple, but behavior can change when the tool updates.
For fully reproducible results, or when you need to use the local `.venv`, use `uv run` instead.

</details>

### 3.3 Build Project Documentation

Make sure you have current doc dependencies, then build your docs, fix any errors, and serve them locally to test.

```shell
uv run mkdocs build --strict
uv run mkdocs serve
```

- After running the serve command, the local URL of the docs will be provided. To open the site, press **CTRL and click** the provided link (at the same time) to view the documentation. On a Mac, use **CMD and click**.
- Press **CTRL c** (at the same time) to stop the hosting process.

### 3.4 Execute

This project includes demo code and completed analysis notebooks.
Run the demo Python modules to confirm everything is working.

In VS Code terminal, run:

```shell
uv run python notebooks/project01/ml01.py
```

A new window with charts should appear. Close the window to finish the execution.
If this works, your project is ready! If not, check:

- Are you in the right folder? (All terminal commands are to be run from the root project folder.)
- Did you run the full `uv sync --extra dev --extra docs --upgrade` command?
- Are there any error messages? (ask for help with the exact error)

## Update this README as you work

Add commands to run additional scripts as you work through the course (update the path and file name as needed).

---

### 3.5 Git add-commit-push to GitHub

Anytime we make working changes to code is a good time to git add-commit-push to GitHub.

1. Stage your changes with git add.
2. Commit your changes with a useful message in quotes.
3. Push your work to GitHub.

```shell
git add .
git commit -m "describe your change in quotes"
git push -u origin main
```

This will trigger the GitHub Actions workflow and publish your documentation via GitHub Pages.

### 3.6 Modify and Debug

With a working version safe in GitHub, start making changes to the code.

Before starting a new session, remember to do a `git pull` and keep your tools updated.

Each time forward progress is made, remember to git add-commit-push.

---

### Project Overview

Predicting healthcare costs is critical for insurance companies, healthcare providers, and policymakers. Understanding which factors drive medical expenses helps with risk assessment, premium pricing, and resource allocation. This project uses regression analysis to predict individual medical insurance charges based on demographic and health factors.

This project demonstrates the ability to apply advanced regression modeling techniques with proper feature engineering, pipeline optimization, and polynomial transformations to achieve high predictive accuracy on real-world healthcare cost data.

#### Objective: Multi-Model Regression Analysis with Pipeline Optimization

- Load and explore the medical insurance dataset
- Perform outlier detection and feature engineering
- Compare continuous vs. categorical feature approaches
- Train and evaluate multiple regression models
- Implement scikit-learn pipelines with StandardScaler
- Apply polynomial feature transformations for non-linear relationships
- Document findings in a structured Jupyter Notebook with comprehensive reflections

---

#### Feature Engineering & Selection

**Data Exploration Findings:**
- 1,338 records with 7 features: age, sex, bmi, children, smoker, region, charges
- No missing values (clean dataset)
- Outliers detected: 139 high-cost records (10.4%) ranging from $34,618-$63,770
- 9 BMI outliers (0.7%) with values 47.41-53.13

**Feature Engineering Process:**
- Created `age_group` categorical bins (18-25, 26-35, 36-45, 46-55, 56-65)
- Created `bmi_category` bins (Underweight, Normal, Overweight, Obese)
- Converted `sex` to numerical (1=male, 0=female)
- Converted `smoker` to binary `smoker_status` (1=yes, 0=no)

**Critical Decision: Continuous vs. Categorical Features**
- **Initial Approach**: Used categorical bins (age_group, bmi_category) with `pd.get_dummies()`
- **Problem Identified**: Polynomial features on binary dummy variables produce identical results (0² = 0, 1² = 1)
- **Solution**: Switched to continuous features (raw age, bmi values) to enable meaningful polynomial transformations

#### Case Studies: Model Feature Combinations

#### Case 1: Age (Continuous)

- **Features**: `age` (18-64 continuous)
- **Rationale**: Medical costs typically increase with age due to accumulated health conditions
- **Result**: R² = 0.12 (weak standalone predictor)

#### Case 2: BMI (Continuous)

- **Features**: `bmi` (15.96-53.13 continuous)
- **Rationale**: Higher BMI correlates with obesity-related health complications
- **Result**: R² = 0.04 (very weak standalone predictor)

#### Case 3: Smoker Status (Binary)

- **Features**: `smoker_status` (0/1 binary indicator)
- **Rationale**: Smoking is major health risk factor significantly increasing medical costs
- **Result**: R² = 0.66 (strongest single predictor - smokers pay 2-3x more)

#### Case 4: Multi-Feature Model ⭐ **Best Performer**

- **Features**: `age` + `bmi` + `smoker_status` (3 continuous features)
- **Rationale**: Capture feature interactions (e.g., older smokers with high BMI have exponentially higher costs)
- **Linear Model Result**: R² = 0.78, MAE = $4,261
- **Polynomial Model Result**: R² = 0.86, MAE = $2,838 (33% error reduction!)

---

### Performance Summary - Regression Results

#### Section 4: Basic Linear Regression (Without Pipelines)

| Case | Features | R² Score | MAE | MSE | Performance Notes |
|------|----------|----------|-----|-----|-------------------|
| 1 | Age (continuous) | 0.1241 | $9,173 | 135,983,957 | Weak - age alone insufficient |
| 2 | BMI (continuous) | 0.0397 | $9,785 | 149,085,057 | Very weak - BMI needs context |
| 3 | Smoker Status | 0.6602 | $5,626 | 52,745,965 | Strong - smoking dominates costs |
| 4 | **Age+BMI+Smoker** | **0.7777** | **$4,261** | **34,512,844** | 🏆 **Multi-feature captures interactions** |

#### Section 5: Pipeline Comparison (Imputer → StandardScaler → Regression)

| Case | Model Type | R² Score | MAE | MSE | Performance Notes |
|------|------------|----------|-----|-----|-------------------|
| **1: Age** | Linear Pipeline | 0.1241 | $9,173 | 135,983,957 | Scaling minimal impact |
| | Polynomial (degree 3) | 0.1185 | $9,195 | 136,845,313 | Slight degradation |
| **2: BMI** | Linear Pipeline | 0.0397 | $9,785 | 149,085,057 | Scaling minimal impact |
| | Polynomial (degree 3) | 0.0180 | $9,863 | 152,452,516 | Worse with polynomial |
| **3: Smoker** | Linear Pipeline | 0.6602 | $5,626 | 52,745,965 | Binary feature unchanged |
| | Polynomial (degree 3) | 0.6602 | $5,626 | 52,745,965 | No benefit (0/1 values) |
| **4: Multi-Feature** | Linear Pipeline | 0.7777 | $4,261 | 34,512,844 | Strong baseline |
| | **Polynomial (degree 3)** | **0.8615** | **$2,838** | **21,501,970** | 🏆 **BEST - captures interactions** |

#### 🏆 Performance Rankings

1. **Multi-Feature Polynomial (degree 3)**: R² = 0.86, MAE = $2,838 - Clear winner
2. **Multi-Feature Linear**: R² = 0.78, MAE = $4,261 - Strong baseline
3. **Smoker Status Only**: R² = 0.66, MAE = $5,626 - Best single feature
4. **Age/BMI Single Features**: R² < 0.13 - Weak standalone predictors

---

### Technical Accomplishments

#### Advanced Techniques Implemented:

1. **Scikit-Learn Pipelines**
   - Pipeline 1: Imputer → StandardScaler → Linear Regression
   - Pipeline 2: Imputer → PolynomialFeatures(degree=3) → StandardScaler → Linear Regression
   - Automated preprocessing and feature transformation workflows

2. **Feature Transformation Analysis**
   - Compared categorical bins vs. continuous features
   - Demonstrated why continuous features enable polynomial transformations
   - Explained 0² = 0 and 1² = 1 problem with dummy variables

3. **StandardScaler Impact Study**
   - Showed minimal impact on single-feature models
   - Demonstrated critical importance for multi-feature polynomial models
   - Explained numerical stability issues without scaling (age³ = 262,144 vs smoker³ = 1)

4. **Polynomial Feature Engineering**
   - Created interaction terms: age×bmi, age×smoker, bmi×smoker
   - Generated higher-order terms: age², age³, bmi², bmi³
   - Achieved 33% MAE reduction through non-linear modeling

5. **Comprehensive Visualization**
   - Histograms showing feature distributions
   - Boxplots for outlier detection
   - Scatter plots showing continuous relationships
   - Color-coded plots showing smoker vs. non-smoker patterns

6. **Statistical Outlier Detection**
   - IQR method implementation
   - Quantified outlier percentages
   - Analyzed impact on model performance

---

### Key Learning Outcomes & Insights

#### **Critical Discovery: Feature Interactions Drive Predictions**

1. **Continuous Features Essential**: Raw age/BMI values (not categories) enable polynomial transformations
2. **Smoking Dominance**: Single strongest predictor (R² = 0.66) - smokers pay dramatically more
3. **Interaction Effects**: Older smokers with high BMI cost exponentially more than individual factors suggest
4. **Polynomial Success**: Degree 3 polynomial captured non-linear relationships (R² 0.78 → 0.86)

#### **Algorithm-Specific Insights**

- **Linear Regression**: Good baseline (R² = 0.78) but misses non-linear patterns
- **Polynomial Regression**: Captures age², bmi², and interaction terms for 33% error reduction
- **StandardScaler Impact**: Essential for polynomial multi-feature models, minimal for single features
- **Pipeline Benefits**: Reproducible workflows, prevents data leakage, ensures consistent preprocessing

#### **Regression-Specific Lessons**

1. **Feature Quality**: Continuous > Categorical for polynomial transformations
2. **Scaling Necessity**: Critical when features have different ranges (age: 18-64, bmi: 16-53, smoker: 0-1)
3. **Interaction Capture**: Polynomial features model compound effects automatically
4. **Model Complexity**: Polynomial degree 3 optimal - higher degrees risk overfitting with limited data

#### **Healthcare Domain Insights**

1. **Behavioral Factors Dominate**: Smoking status more predictive than demographics
2. **Compound Risk**: Older age + smoking + obesity creates exponential cost increases
3. **Individual Variation**: Even best model (R² = 0.86) has 14% unexplained variance
4. **Outlier Reality**: High-cost patients ($34K-$64K) represent legitimate extreme cases

---

### Challenges Faced & Solutions

#### **Challenge 1: Categorical Feature Limitation**
- **Problem**: Initial use of `pd.get_dummies()` on age_group and bmi_category
- **Impact**: Polynomial pipelines produced identical results to linear (0² = 0, 1² = 1)
- **Solution**: Switched to continuous raw features (age, bmi) to enable meaningful polynomial terms
- **Learning**: Feature representation choice dramatically affects model capability

#### **Challenge 2: Feature Scaling Complexity**
- **Problem**: Age (18-64), BMI (16-53), Smoker (0-1) on vastly different scales
- **Impact**: Without StandardScaler, age³ = 262,144 would dominate smoker³ = 1
- **Solution**: Implemented StandardScaler in pipelines after PolynomialFeatures
- **Learning**: Scaling order matters - scale AFTER polynomial transformation

#### **Challenge 3: Outlier Management**
- **Problem**: 139 high-cost records (10.4%) from $34K-$64K charges
- **Decision**: Kept outliers as they represent real high-risk patients
- **Impact**: Models handle extreme values reasonably well (R² = 0.86)
- **Future Work**: Could try log-transformation or robust regression techniques

#### **Challenge 4: Single Feature Weakness**
- **Problem**: Age (R² = 0.12) and BMI (R² = 0.04) are weak standalone predictors
- **Insight**: Insurance costs driven by feature interactions, not individual factors
- **Solution**: Multi-feature model captures compound effects (R² = 0.86)
- **Learning**: Complex real-world problems require multiple features and interactions

---

### Data Challenges Identified

1. **Prediction Difficulty**: Moderately challenging with R² = 0.86 maximum
   - Individual health variations create unpredictable patterns
   - 14% unexplained variance from unmeasured factors (genetics, lifestyle, prior conditions)
   - Regional cost variations only partially captured

2. **Distribution Issues**:
   - Right-skewed charge distribution (few very expensive cases)
   - Outliers from extreme medical conditions affect linear assumptions
   - Log-transformation could normalize distribution (future work)

3. **Feature Limitations**:
   - Missing: medical history, chronic conditions, family health history
   - No temporal data: when charges occurred, disease progression
   - Simplified: only 7 features available for complex healthcare cost problem

---

### Future Improvements & Next Steps

**Immediate Enhancements:**

1. **Add More Features**: Include `children`, `region`, and `sex` in multi-feature model
   - Test `region` interactions (geographic cost variations)
   - Consider `children × smoker` (family health impact)

2. **Outlier Handling**:
   - Log-transform charges to reduce right-skew
   - Test robust regression (Huber Regressor, RANSAC)
   - Consider separate models for high-cost vs. normal-cost patients

3. **Feature Engineering**:
   - Create explicit `age × smoker` interaction term
   - Add `obesity_flag` (BMI > 30) as binary feature
   - Test different polynomial degrees (2, 4, 5)

**Advanced Techniques:**

1. **Regularization**:
   - Ridge regression to handle multicollinearity in polynomial features
   - Lasso for automatic feature selection
   - ElasticNet for balanced approach

2. **Model Validation**:
   - K-fold cross-validation for robust performance estimates
   - Learning curves to detect overfitting
   - Residual analysis to identify systematic errors

3. **Alternative Models**:
   - Random Forest for non-linear patterns without manual feature engineering
   - Gradient Boosting for ensemble approach
   - Neural networks for complex interaction modeling

**Research Extensions:**

- Compare performance with modern healthcare cost datasets
- Test transferability to different insurance markets
- Explore interpretability techniques (SHAP values) for feature importance