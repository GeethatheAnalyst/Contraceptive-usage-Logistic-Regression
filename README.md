# Contraceptive Usage Prediction — Logistic Regression

Unlike my linear regression project where I was predicting a number, this one was about predicting a yes or no. That difference sounds small but it changes everything — how you build the model, how you evaluate it, and most importantly, how you decide whether it's actually good enough.

---

## What the project is about

The dataset is survey data from married women in Indonesia. Based on things like a woman's age, how many children she has, her education level, her husband's occupation, and whether she's exposed to media — the model tries to predict whether she uses contraception or not.

It's the kind of dataset where getting the prediction wrong isn't just a number on a scorecard. That kept me more careful than usual.

---

## The dataset

- <a href="https://github.com/GeethatheAnalyst/Contraceptive-usage-Logistic-Regression/blob/main/Contraceptive_method_dataset.xlsx">Contraceptive Method Dataset</a> collected from married Indonesian women, covering demographic and socio-economic factors alongside contraceptive usage.

---

## How I approached it

**Encoding the features**
Before anything else, all the categorical columns needed to be turned into numbers. But I didn't just slap numbers on them randomly.

For education level — Uneducated, Primary, Secondary, Tertiary — I encoded them as 1, 2, 3, 4 in that order. There's a real hierarchy there and the model should know that Tertiary is "more" than Primary, not just different. For binary columns like Wife_Working, 0 and 1 was enough.

It's a small decision but the wrong encoding here would have quietly broken the model without any obvious error message.

**Train-test split**
70% of the data for training, 30% held back for testing. The model never sees the test set during training — that's how you know whether it actually learned something or just memorised the data.

**Building the model**
Used scikit-learn's LogisticRegression. Straightforward to set up — the real thinking was in what came before and after, not the model call itself.

**Evaluating the results**
This is where it got interesting. The model hit **0.84 recall** on the test set.

---

## Why I cared about recall more than accuracy

When I first looked at the results, overall accuracy seemed fine. But I kept coming back to one question — what kind of mistake is worse here?

There are two ways to be wrong:
- Predict someone uses contraception when they don't — not ideal, but manageable
- Predict someone doesn't use contraception when they actually do — in a health or policy setting, this is the one you really want to avoid

Recall is the metric that tells you how many actual contraceptive users the model caught. At 0.84, it found 84 out of every 100 real users correctly. That felt like the right thing to optimise for here — not just chasing a high accuracy number.

---

## What I took away from this

The technical part — fitting a logistic regression model — honestly wasn't the hardest part. What took more thought was figuring out which metric actually mattered and why. That's something I want to carry into every project going forward.

---

## Tools used

- Python 3
- Pandas, NumPy
- scikit-learn (LogisticRegression, train_test_split, confusion_matrix, classification_report)
- Matplotlib, Seaborn
- Jupyter Notebook

---

## Files in this repo

- <a href="https://github.com/GeethatheAnalyst/Contraceptive-usage-Logistic-Regression/blob/main/Logistic%20Regression%20Project.ipynb">Full notebook</a> with code and outputs 

---

## Dataset

Contraceptive Method Dataset provided as part of ML coursework at RRC Technologies, Thanjavur.
