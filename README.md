
# Census Income Classifier
 
Census Income Classifier is a machine learning project that predicts whether a person earns more or less than $50,000 a year, based on details like their age, education, job, and hours worked per week.
 
By combining **data analysis**, **fairness-focused feature selection**, and a **side-by-side test of two different Machine Learning models**, this project shows which approach a lender should actually use to speed up loan screening.
 
---
 
## Table of Contents
 
1. [Features](#features)
2. [How It Works](#how-it-works)
3. [Why It Matters](#why-it-matters)
4. [Tech Stack](#tech-stack)
5. [Example Output](#example-output)
6. [Contributors](#contributors)
---
 
## Features
 
- **Income Prediction** — Sorts each person into one of two groups: earns over $50K, or earns $50K or less.
- **Two Models Compared** — Trains a Logistic Regression model and a neural network on the same data, then scores both.
- **Fairness Check** — Removes race, sex, and country of origin from the data so the model can't learn to discriminate on them.
- **Automatic Tuning** — Tests five different model settings and picks the one that scores best.
- **Explainable Results** — Charts show exactly which details push a prediction toward higher income and which push it lower.
---
 
## How It Works
 
1. **Load the Data:** Reads in 32,561 census records, each with 14 details about a person plus their actual income bracket.
2. **Explore the Data:**
   - Charts show that about 3 out of 4 people earn $50K or less, so the two groups are uneven.
   - Box plots show that people who work more hours tend to earn more.
   - Finds gaps in the data: some records are missing age, job type, or hours worked.
3. **Clean the Data:**
   - Removes details that don't help or could cause bias.
   - Fills in missing numbers with the median, and missing categories with the most common answer.
   - Converts text answers like "Married" into numbers the model can read.
4. **Train Model 1:** A Logistic Regression model learns from 80% of the data and is tested on the other 20%.
5. **Train Model 2:** A neural network with three layers learns from the same data over 15 rounds of training.
6. **Compare:** Both models are scored on how often they're right and how well they catch high earners.
---
 
## Why It Matters
 
- **Reviewing applications by hand is slow.** A lender checking every application manually spends hours on cases a model could sort in seconds.
- **People decide inconsistently.** Two reviewers can look at the same application and reach different conclusions. A model applies the same rules every time.
- **Census data carries old biases.** If a model learns from decades of unequal outcomes, it repeats them. This project cuts out the details most likely to cause that.
- **Fancier isn't always better.** The neural network took far more work to build and barely beat the simple model — which is the actual finding here.
---
 
## Tech Stack
 
- **Language:** Python 3
- **Environment:** Jupyter Notebook
- **Data Handling:** Pandas, NumPy
- **Machine Learning:** Scikit-learn (Logistic Regression, grid search, scaling)
- **Neural Network:** TensorFlow / Keras
- **Charts:** Matplotlib, Seaborn
- **Dataset:** U.S. Census income data (`censusData.csv`)
---
 
## Example Output
 
**Best settings found by the tuner:**
 
```
Best parameters: {'C': 1, 'penalty': 'l2'}
```
 
**Final scores:**
 
```
  Metric  LogisticRegression  Neural Network
Accuracy            0.844285        0.844530
F1 Score            0.649200        0.675600
```
 
**What this means:** Both models got about 84 out of every 100 predictions right. The neural network was slightly better at spotting high earners, but not by enough to matter.
 
**What the model learned:** Capital gains, more years of education, being married, working longer hours, and being older all made a high-income prediction more likely. Being never married, being listed as someone's child, and working in service jobs made it less likely.
 
**Recommendation:** Use the Logistic Regression model. It's just as accurate, trains in seconds instead of minutes, and you can show anyone exactly why it made a given call.
 
---
 
## Contributors
 
- **Ethan** — Built the entire project: data cleaning, both models, testing, and written analysis.
Created as an individual capstone for the Break Through Tech AI/ML program.
