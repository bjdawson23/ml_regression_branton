# Heart Disease Classification Analysis - Machine Learning Project

**Author:** Branton Dawson  
**Course:** Applied Machine Learning  
**Date:** November 24, 2025  

## 📂 Project Links

- Notebook link: [Classification Mid_term](https://github.com/bjdawson23/ml_classification_branton/blob/main/classification_analysis.ipynb)

- Peer Review: [Peer_Review](https://github.com/bjdawson23/ml_classification_branton/blob/main/peer_review.md)

## 🎯 Project Overview

This repository contains a comprehensive machine learning analysis for predicting heart disease presence using the UCI Heart Disease Dataset. The project demonstrates professional data science methodologies by comparing multiple classification algorithms across different feature engineering approaches.

## 📊 Dataset & Objective

- **Dataset:** UCI Heart Disease Dataset (303 patient records, 14 clinical features)
- **Target:** Binary classification - Heart disease presence (0 = No, 1 = Yes)  
- **Algorithms Compared:** Decision Tree Classifier, Support Vector Machine (SVM), Neural Network (MLP)
- **Feature Cases:** Age groups, cholesterol levels, and maximum heart rate (thalach)

## 🏆 Key Results Summary

| Algorithm | Best Feature | Accuracy | Key Insight |
|-----------|--------------|----------|-------------|
| **SVM (Winner)** | thalach | **68.3%** | Superior with continuous physiological data |
| Decision Tree | age_group | 63.3% | Most interpretable, consistent across features |  
| SVM | age_group | 63.3% | Tied performance on categorical data |
| Decision Tree | chol_level | 60.0% | Cholesterol alone insufficient for prediction |

### 💡 Clinical Insights
- **Maximum heart rate (thalach)** emerged as the most predictive single feature
- **Age remains fundamental** - consistently strong across all modeling approaches
- **Algorithm choice matters** - SVM excels with continuous features, Decision Trees with categorical
- **Feature engineering impact** - Proper binning and categorization significantly affects model performance

## 🚀 Quick Start Guide

### Prerequisites
- Python 3.11+ installed on your system
- Git for version control
- VS Code with Python extension (recommended)

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/bjdawson23/ml_classification_branton.git
cd ml_classification_branton
```

### 2️⃣ Set Up Virtual Environment

**Option A: Using uv (Recommended)**
```bash
uv venv
uv python pin 3.12
uv sync --extra dev --extra docs --upgrade
```

**Option B: Using standard Python**
```bash
python -m venv .venv
```

### 3️⃣ Activate Virtual Environment

**Windows (PowerShell):**
```powershell
.\.venv\Scripts\activate
```

### 4️⃣ Install Required Packages
```bash
pip install -r requirements.txt
```

Required packages:
- `pandas` - Data manipulation and analysis
- `numpy` - Numerical computing  
- `scikit-learn` - Machine learning algorithms
- `matplotlib` - Data visualization
- `seaborn` - Statistical data visualization

### 5️⃣ Launch Jupyter Notebook
```bash
jupyter notebook
```

Navigate to `notebooks/ml_classification_branton/ml_classification_branton.ipynb` to run the analysis.

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

## 📚 Project Structure

```
ml_classification_branton/
├── README.md                           # This file - project overview and setup
├── requirements.txt                    # Python package dependencies  
├── peer_review.md                     # Peer review documentation
├── notebooks/
│   └── ml_classification_branton/
│       ├── ml_classification_branton.ipynb  # Main analysis notebook
│       └── data/
│           └── heart_disease_data.csv      # UCI Heart Disease dataset
└── .venv/                             # Virtual environment (created during setup)
```

## 🔬 Technical Methodology

### Data Preprocessing Pipeline
1. **Missing Value Handling**: Dropped 6 rows with NaN values (minimal 2% loss)
2. **Target Engineering**: Converted multi-class target (0,1,2,3,4) to binary classification
3. **Feature Engineering**: Created age groups and cholesterol risk categories
4. **Data Splitting**: Stratified train/test split (80/20) maintaining class balance

### Model Evaluation Framework
- **Algorithms**: Decision Tree, Support Vector Machine (RBF kernel), Neural Network (MLP)
- **Metrics**: Accuracy, Precision, Recall, F1-Score, Classification Report
- **Validation**: Stratified sampling with different random states for robust comparison
- **Visualization**: Decision trees, confusion matrices, performance comparisons

## 🎓 Learning Outcomes

### Technical Skills Demonstrated
- **Data Wrangling**: Pandas-based data cleaning and transformation
- **Feature Engineering**: Medical domain-aware feature creation and binning
- **Model Selection**: Systematic algorithm comparison with proper evaluation
- **Visualization**: Professional matplotlib/seaborn plotting for insights
- **Performance Analysis**: Multi-metric evaluation beyond simple accuracy

### Machine Learning Concepts Applied
- **Classification Theory**: Binary prediction with medical significance
- **Algorithm Comparison**: Understanding when different models excel
- **Feature Selection**: Impact of different predictors on model performance
- **Overfitting Detection**: Training vs test performance analysis
- **Clinical Interpretation**: Translating ML results to healthcare insights

## 🤝 Contributing & Collaboration

This project was developed as part of an applied machine learning course. For questions, suggestions, or collaboration opportunities:

- **Author**: Branton Dawson
- **Course**: Applied Machine Learning  

## 📄 License & Usage

This project is for educational purposes. The UCI Heart Disease Dataset is publicly available for research and educational use. Please cite appropriately if using this analysis as a reference.

---

## 🛠️ Development Workflow

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