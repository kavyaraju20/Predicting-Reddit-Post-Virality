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







