# 📊 Telegram E-commerce Vendor Analysis

This project analyzes e-commerce activity on Telegram channels to evaluate vendors for potential **lending opportunities** using **data science and NLP techniques**.

---

## 🗂️ Project Overview

We scraped vendor data from Ethiopian Telegram-based e-commerce channels and built a pipeline to:

- Analyze **channel activity and consistency**
- Evaluate **market reach and customer engagement**
- Extract **product pricing** using a custom NER model
- Interpret predictions using **SHAP** and **LIME**
- Combine these into a **Lending Score** to rank vendors for business financing opportunities

---

## 📥 Data Collected

- **Fields:** `channel`, `message_id`, `date`, `text`, `views`
- Scraped directly from Telegram using Python + Telethon

---

## 📈 Analysis Modules

### ✅ Activity & Consistency
- **Metric:** Average posts per week
- Purpose: Measures if the vendor is actively posting products

### ✅ Market Reach & Engagement
- **Metrics:** 
  - Average views per post (customer reach)
  - Top-performing post (with product name & price using NER)

### ✅ Product Pricing Insights (NER)
- Fine-tuned **Amharic NER model** using Transformers
- Extracted product prices from posts
- Computed **average price point per vendor**

---

## 🔍 Model Interpretability

### SHAP (SHapley Additive Explanations)
- Interpreted NER model predictions at token level
- Visualized important tokens influencing entity classification

### LIME (Local Interpretable Model-agnostic Explanations)
- Provided localized explanation for individual product posts
- Identified which parts of the sentence influenced predictions

---

## 💸 Lending Score

A final **Lending Score** was computed for each vendor using:

```python
Score = (Normalized Avg Views × 0.6) + (Normalized Posting Frequency × 0.4)
🏆 Top 5 Vendors (Example Output)
Rank	Channel	Score	Avg Views	Posts/Week
1	Leyueqa	0.73	42,504	14.3
2	qnashcom	0.66	24,772	30.7
3	ethio_brand_collection	0.58	36,954	8.3
4	MerttEka	0.52	25,719	17.5
5	AwasMart	0.49	8,814	36.9