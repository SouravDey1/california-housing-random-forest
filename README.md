# California House Price Prediction — Random Forest
### Regression · Ensemble Learning · Python · Scikit-learn

![Python](https://img.shields.io/badge/Python-3.11-blue?style=flat&logo=python)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-ML-orange?style=flat&logo=scikit-learn)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?style=flat&logo=pandas)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter)
![RMSE](https://img.shields.io/badge/RMSE-0.528-brightgreen?style=flat)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)

---

## Overview

This project predicts California median house prices using **Random Forest Regression** and compares it against a baseline **Decision Tree Regressor** to demonstrate the power of ensemble learning.

The project uses the California Housing dataset — a real-world dataset from the 1990 US Census — covering 20,640 housing blocks across California. By comparing a single decision tree against an ensemble of 100 trees, the project quantifies exactly how much ensemble methods improve prediction accuracy.

---

## Problem Statement

Predicting house prices is a classic regression problem with real-world implications for buyers, sellers, banks, and urban planners. The goal here is to predict the **median house value** (in $100,000s) for a California district using demographic and geographic features.

---

## Dataset

**Source:** `sklearn.datasets.fetch_california_housing` — no download needed

**Size:** 20,640 housing block records · 8 features · No missing values

| Feature | Description |
|---|---|
| `MedInc` | Median income of households in the block (in $10,000s) |
| `HouseAge` | Median age of houses in the block |
| `AveRooms` | Average number of rooms per household |
| `AveBedrms` | Average number of bedrooms per household |
| `Population` | Block population |
| `AveOccup` | Average number of household members |
| `Latitude` | Block latitude |
| `Longitude` | Block longitude |
| `MedHouseVal` | **Target** — Median house value ($100,000s) |

---

## Project Workflow

```
Data Loading → EDA → Geo Visualisation → Train/Test Split → Decision Tree → Random Forest → Comparison
```

**1. Exploratory Data Analysis**
- Geographic scatter plot (Latitude vs Longitude) coloured by house value — revealing clear coastal vs inland price patterns
- Correlation heatmap across all 8 features
- Distribution analysis of target variable

**2. Baseline Model — Decision Tree Regressor**
- `DecisionTreeRegressor()` with default parameters
- Single tree, no ensemble
- Prone to overfitting on training data

**3. Ensemble Model — Random Forest Regressor**
- `RandomForestRegressor()` with default parameters (100 trees)
- Aggregates predictions across 100 decision trees
- Reduces variance through bagging (Bootstrap Aggregation)

**4. Model Comparison**
- Same train/test split (70/30) applied to both models
- Evaluated using RMSE (Root Mean Squared Error)

---

## Results

| Model | RMSE | Improvement |
|---|---|---|
| Decision Tree Regressor | 0.7423 | Baseline |
| **Random Forest Regressor** | **0.5280** | **29% better** |

### Key Takeaway

> Random Forest reduced prediction error by **29%** compared to a single Decision Tree — on the same data, with the same split, with no feature engineering.
>
> The improvement comes entirely from the ensemble mechanism: 100 trees each trained on a random subset of data and features, their predictions averaged to cancel out individual errors.

### Feature Importance Insight
Geographic features (Latitude, Longitude) and median income (`MedInc`) are the strongest predictors of house value in California — consistent with real-world understanding of coastal premium pricing.

---

## Tech Stack

| Tool | Purpose |
|---|---|
| Python 3.11 | Core language |
| Pandas | Data manipulation |
| NumPy | Numerical operations |
| Scikit-learn | Decision Tree, Random Forest, metrics |
| Seaborn | Heatmap, distribution plots |
| Matplotlib | Geographic scatter plot |
| Jupyter Notebook | Development environment |

---

## How to Run

**1. Clone the repository**
```bash
git clone https://github.com/SouravDey1/california-housing-random-forest.git
cd california-housing-random-forest
```

**2. Install dependencies**
```bash
pip install pandas numpy scikit-learn seaborn matplotlib jupyter
```

**3. Open the notebook**
```bash
jupyter notebook project_random_forest.ipynb
```

> No dataset download needed — the California Housing dataset loads directly via Scikit-learn.

---

## Repository Structure

```
california-housing-random-forest/
│
├── project_random_forest.ipynb   # Full notebook — EDA, models, comparison
└── README.md                     # This file
```

---

## What I Learned

- How **ensemble learning** reduces variance through bagging — averaging 100 imperfect models beats one "perfect" model
- Why **Decision Trees overfit** — a single tree memorises training data; a forest generalises better
- How to use **geographic visualisation** (lat/lon scatter plots) for spatial data EDA
- That **default Random Forest parameters** often outperform heavily tuned single models — ensemble diversity is that powerful
- The meaning of **RMSE in context**: an RMSE of 0.528 means the model's predictions are off by ~$52,800 on average for a house — reasonable for a default model on real-world data
- Why **feature importance** matters: MedInc and geography dominate because California house prices are driven by location and affordability

---

## Author

**Sourav Dey**
Final-Year EEE Student · Ahsanullah University of Science and Technology (AUST)
📧 sourav41dey@gmail.com
🔗 [LinkedIn](https://www.linkedin.com/in/sourav-dey-754298251/)
🐙 [GitHub](https://github.com/SouravDey1)

---

*Part of my Data Science & Machine Learning portfolio.*

*Other projects:*
- [Diabetes Prediction — KNN](https://github.com/SouravDey1/diabetes-knn-classification)
- [Ad Click Prediction — Logistic Regression](https://github.com/SouravDey1/ad-click-logistic-regression)
- [E-Commerce Spending Prediction — Linear Regression](https://github.com/SouravDey1/ecommerce-linear-regression)
