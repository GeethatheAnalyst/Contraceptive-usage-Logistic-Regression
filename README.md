# Contraceptive Usage Prediction — Logistic Regression

This project is a classification problem — instead of predicting a number like rent price, the model predicts a category: does a woman use contraception or not? That shift from regression to classification changes how you think about what "good performance" actually means.

---

## What I was trying to predict

Given socio-demographic information about a woman — her age, education level, number of children, husband's occupation, standard of living index, media exposure, and religion — predict whether she uses contraception.

---

## The dataset

Contraceptive Method Dataset (`Contraceptive_method_dataset.xlsx`) — survey data collected from married women in Indonesia, covering demographic and socio-economic factors alongside contraceptive usage.

---

## What I did

**Step 1 — Understanding the target variable**
The target column `Contraceptive_method_used` was binary — Yes or No. Before anything else, I checked the class balance to make sure the model wouldn't just learn to predict the majority class.

**Step 2 — Encoding categorical features**
All categorical columns needed to be converted to numbers before the model could use them. I was careful about *how* I encoded them:

- Ordinal features (like education level: Uneducated → Primary → Secondary → Tertiary) were encoded as 1–4 to preserve the natural order
- Binary features (like Wife_Working: Yes/No) were encoded as 0 and 1

Using the wrong encoding here — for example treating education as unordered categories — would have lost meaningful information.

**Step 3 — Train-test split**
Split the data 70% training and 30% testing using scikit-learn's `train_test_split`. The model learns from the 70% and is evaluated on the 30% it has never seen.

**Step 4 — Building the model**
Built the logistic regression model using scikit-learn's `LogisticRegression`. Logistic regression works well here because the relationship between the features and the outcome is reasonably linear in log-odds terms.

**Step 5 — Evaluation**
Evaluated using a confusion matrix and a full classification report (precision, recall, F1-score).

The model achieved **0.84 recall** on the test set.

---

## Why recall was the metric that mattered here

This is worth explaining properly.

In a health-related dataset like this, the two types of errors are not equal:
- **False Positive** — predicting someone uses contraception when they don't → minor issue
- **False Negative** — predicting someone doesn't use contraception when they do → a bigger problem in a health/policy context

Recall measures how well the model catches actual positive cases (contraceptive users). At 0.84, the model correctly identified 84% of real contraceptive users — missing only 16%. That's what matters here, not overall accuracy.

---
