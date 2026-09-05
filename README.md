# Gojek App Review Sentiment Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange)
![NLP](https://img.shields.io/badge/NLP-Indonesian-green)

## Project Overview

This project analyzes **20,000 Gojek app reviews** to classify user sentiment and compare three machine learning approaches:

- Random Forest
- Support Vector Machine (SVM)
- Multinomial Naive Bayes

The workflow covers data understanding, rating-based sentiment labeling, Indonesian text preprocessing, TF-IDF feature extraction, model comparison, class imbalance handling, error analysis, and business insights.

## Objectives

1. Understand the characteristics and sentiment distribution of the review dataset.
2. Preprocess Indonesian-language app reviews for machine learning.
3. Convert text into numerical features using TF-IDF.
4. Compare Random Forest, SVM, and Multinomial Naive Bayes.
5. Investigate the effect of class balancing on minority-class detection.
6. Select a final model using Macro F1 because the sentiment classes are imbalanced.
7. Extract recurring themes from user feedback for business interpretation.

---

## Dataset

The dataset contains **20,000 Gojek app reviews** with information including:

- Review content
- Rating score
- Review date
- Application metadata
- Review engagement information

The original dataset is not included in this public repository.

### Rating-Based Sentiment Labeling

Sentiment labels were derived from review ratings:

| Rating | Sentiment |
|---|---|
| 1–2 | Negative |
| 3 | Neutral |
| 4–5 | Positive |

> **Note:** The sentiment labels are rating-based proxies rather than independent human annotations.

### Sentiment Distribution

| Sentiment | Reviews | Share |
|---|---:|---:|
| Negative | 12,479 | 62.40% |
| Neutral | 2,216 | 11.08% |
| Positive | 5,305 | 26.53% |

The collected review set is imbalanced, with Negative reviews representing the majority class.

---

## Methodology

```text
20,000 Gojek Reviews
        ↓
Data Understanding
        ↓
Rating-Based Sentiment Labeling
        ↓
Indonesian Text Preprocessing
        ↓
Train-Test Split (80:20)
        ↓
TF-IDF Feature Extraction
        ↓
Baseline Models
        ↓
Class Imbalance Handling
        ↓
Balanced Models
        ↓
Model Comparison
        ↓
Error Analysis
        ↓
Final Model Selection
        ↓
Business Insights

---

### Text Preprocessing

The review text was processed through several stages:

- Lowercasing
- URL removal
- Text normalization
- Punctuation and symbol cleaning
- Tokenization
- Indonesian stopword removal
- Indonesian stemming using Sastrawi

### Feature Extraction

Text data was transformed into numerical features using **TF-IDF** with unigram and bigram features.

The train-test split was performed before fitting TF-IDF to avoid data leakage.

---

## Baseline Model Results

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Random Forest | 75.40% | 50.04% |
| **SVM** | **76.82%** | 52.45% |
| Naive Bayes | 71.58% | 44.30% |

The baseline **SVM achieves the highest accuracy** among the tested baseline models.

However, accuracy alone is not sufficient for evaluating performance because the sentiment classes are imbalanced.

---

## Class Imbalance Handling

Balanced versions of the three models were evaluated to investigate their ability to improve minority-class detection.

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Random Forest Balanced | 75.00% | 49.75% |
| SVM Balanced | 71.28% | 55.92% |
| **Naive Bayes Balanced** | 65.82% | **57.68%** |

---

## Final Model

### Naive Bayes Balanced

The final model was selected using **Macro F1** rather than accuracy because the sentiment classes are imbalanced.

| Metric | Result |
|---|---:|
| Accuracy | **65.82%** |
| Macro F1 | **57.68%** |
| Neutral Recall | **45.15%** |

Although baseline SVM achieves the highest accuracy at **76.82%**, Naive Bayes Balanced achieves the highest Macro F1 at **57.68%** across all tested models.

The balanced Naive Bayes model also improves detection of the minority Neutral class, reaching approximately **45% Neutral recall**.

---

## Business Insights

### 1. Negative Feedback Dominates the Collected Review Set

Negative reviews account for approximately **62.4%** of the 20,000 collected reviews, compared with **26.5% Positive** and **11.1% Neutral**.

This makes negative feedback the main area for deeper investigation.

### 2. Application Experience Is a Recurring Discussion Area

Review vocabulary contains recurring terms related to the **application, features, usage, problems, and errors**.

These themes can be investigated further to identify potential product or usability issues.

### 3. Driver Experience Is an Important Customer Touchpoint

The term **driver** appears across positive, neutral, and negative reviews.

This indicates that driver-related experiences are relevant across different sentiment categories and may warrant deeper investigation.

### 4. Ordering and Transaction Experience Deserve Further Investigation

Terms related to **orders, messaging, payment, transactions, promotions, and balance** appear in the review vocabulary.

These topics can be investigated further to identify potential friction points in the customer journey.

### 5. Class Balancing Improves Minority-Class Detection

Neutral sentiment is the most difficult class to classify.

The balanced experiments substantially improve Neutral detection, particularly for Naive Bayes, whose Neutral recall reaches approximately **45%**.

---

## Key Takeaway

The analysis demonstrates that **model selection should not rely on accuracy alone**, especially when the target classes are imbalanced.

While baseline SVM achieves the highest accuracy at **76.82%**, **Naive Bayes Balanced achieves the strongest Macro F1 at 57.68%** and provides substantially better detection of the minority Neutral class.

Combining machine learning evaluation with text-based exploration provides a more complete perspective on customer feedback and potential areas for product and service improvement.

---

## Tools & Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Sastrawi
- Matplotlib
- Seaborn
- WordCloud
- Jupyter Notebook

---

## Repository Structure

```text
gojek-app-review-sentiment-analysis/
│
├── README.md
├── Gojek_App_Review_Sentiment_Analysis.ipynb
├── requirements.txt
├── .gitignore
│
├── data/
│   └── README.md
│
└── images/
    ├── confusion_matrix_random_forest.png
    ├── confusion_matrix_svm.png
    ├── confusion_matrix_naive_bayes.png
    ├── wordcloud_negative.png
    ├── wordcloud_neutral.png
    └── wordcloud_positive.png

---
## Disclaimer

This project is developed for **portfolio and educational purposes**.

The sentiment labels are derived from review ratings, where ratings **1–2 are classified as Negative, 3 as Neutral, and 4–5 as Positive**. Therefore, the labels represent **rating-based sentiment proxies** rather than manually annotated sentiment.

The business insights presented in this project are **exploratory findings from the collected review data** and should be further validated with additional data before being used for business decision-making.
