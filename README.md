# 🔥 Predicting Reddit Post Virality using Machine Learning and A/B Testing

## 📌 Problem Statement
The goal of this project is to build a machine learning model that can predict whether a Reddit post will go viral, using only early metadata and content features. To strengthen the model's interpretability and validate key hypotheses, A/B testing (Chi-Square Tests) was conducted on critical content strategies.

---

## 🧠 Approach

### 🗂 Data Collection
- Reddit post data was extracted using the `PRAW` (Python Reddit API Wrapper) for multiple subreddits.
- Collected fields: title, selftext, flair, created time, score, upvote ratio, number of comments, etc.

### ⚙️ Feature Engineering
- `title_length`, `title_word_count`
- `text_length`, `text_empty`
- `sentiment_title` (TextBlob polarity score)
- `hour_posted`, `day_of_week`
- `flair`, `is_text_post`, `subreddit`

### 🎯 Target Variable

A binary label `is_viral` was created based on the number of upvotes.  
Posts with `upvotes ≥ 500` were labeled as viral (`1`), otherwise non-viral (`0`)

## 🤖 Models Used

| Model               | Notes                                |
|---------------------|--------------------------------------|
| Logistic Regression | Baseline model, interpretable        |
| Random Forest       | Best performance, good feature insight |
| XGBoost             | Strong performance, flexible and robust |

---

## 📈 Evaluation Metrics

- **Accuracy**
- **Precision, Recall, F1-Score** (with focus on Class 1 — viral)
- **Confusion Matrix**
- **Feature Importance** (analyzed via Random Forest)

---

## 🧪 A/B Testing using Chi-Square Tests

### Hypotheses Tested

| Hypothesis                         | Group A       | Group B        | Result          |
|------------------------------------|---------------|----------------|------------------|
| Long vs. Short Titles              | `< 80 chars`  | `≥ 80 chars`   | ✅ p < 0.001     |
| Text vs. Link Posts                | `link`        | `text`         | ✅ p < 0.001     |
| Positive vs. Negative Sentiment    | `≤ 0`         | `> 0`          | ✅ p = 0.043     |
| Before vs. After 12 PM Posting     | `< 12`        | `≥ 12`         | ❌ p = 0.191     |

### 🧠 Summary:

Statistical testing validated key model-driven insights:
- Content **format** and **tone** significantly impact virality.
- **Posting time** (before vs after 12 PM) showed no significant difference.

---

## 📊 Key Results

- **Random Forest Accuracy:** 81%
- **F1-score (viral class):** 0.66
- **Top 5 Most Important Features:**
  - `title_length`
  - `title_word_count`
  - `hour_posted`
  - `text_empty`
  - `is_text_post`
- Feature importance was visualized and aligned closely with A/B testing outcomes, supporting model interpretability.










