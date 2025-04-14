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
A binary label `is_viral` was created:
```python
is_viral = upvotes >= 500


To avoid label leakage, we removed:

upvotes, comments, upvote_ratio from the feature set during modeling

🤖 Models Used
Model	Notes
Logistic Regression	Baseline, interpretable
Random Forest	Best performance
XGBoost	Comparable performance to RF
📈 Evaluation Metrics
Accuracy

Precision, Recall, F1-Score (Class 1 focused)

Confusion Matrix

Feature Importance (Random Forest)

🧪 A/B Testing with Chi-Square Hypothesis Tests
Hypotheses Tested
Hypothesis	Group A	Group B	Result
Long vs. Short Titles	< 80 chars	≥ 80 chars	✅ p < 0.001
Text vs Link Posts	link	text	✅ p < 0.001
Positive vs Negative Sentiment	≤ 0	> 0	✅ p = 0.043
Before vs After 12 PM	< 12	≥ 12	❌ p = 0.191
Summary:
Statistical testing validated model-driven insights, revealing that content format and tone have significant effects on virality, while posting time does not.

📊 Key Results
Random Forest Accuracy: 81%

F1-score (viral class): 0.66

Top Features: title_length, title_word_count, hour_posted, text_empty, is_text_post

Feature importance visualized and explained
