# Gojek App Review Sentiment Analysis

![Python](https://img.shields.io/badge/Python-3.x-blue)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-orange)
![NLP](https://img.shields.io/badge/NLP-Indonesian-green)

## Project Overview

This project analyzes **20,000 Gojek app reviews** to classify user sentiment and compare three machine learning algorithms:

- Random Forest
- Support Vector Machine (SVM)
- Multinomial Naive Bayes

The analysis also investigates class imbalance and extracts business insights from user feedback.

## Objectives

1. Understand the review dataset and sentiment distribution.
2. Preprocess Indonesian-language review text.
3. Transform text using TF-IDF.
4. Compare Random Forest, SVM, and Naive Bayes.
5. Evaluate the effect of class balancing.
6. Select the final model using Macro F1.
7. Translate review patterns into business insights.

## Dataset

The dataset contains 20,000 Gojek app reviews with fields such as review content, rating, review date, and application metadata.

Sentiment labels are derived from the rating:

| Rating | Sentiment |
|---|---|
| 1–2 | Negative |
| 3 | Neutral |
| 4–5 | Positive |

### Sentiment Distribution

| Sentiment | Reviews | Share |
|---|---:|---:|
| Negative | 12,479 | 62.40% |
| Neutral | 2,216 | 11.08% |
| Positive | 5,305 | 26.53% |

> Note: These labels are rating-based proxies rather than independent human annotations.

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
TF-IDF (Unigram + Bigram)
        ↓
Random Forest / SVM / Naive Bayes
        ↓
Class Imbalance Handling
        ↓
Model Comparison
        ↓
Final Model Selection
        ↓
Sentiment & Business Insights
```

## Baseline Model Results

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Random Forest | 75.40% | 50.04% |
| SVM | **76.82%** | 52.45% |
| Naive Bayes | 71.58% | 44.30% |

The baseline SVM achieves the highest accuracy.

## Balanced Model Results

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Random Forest Balanced | 75.00% | 49.75% |
| SVM Balanced | 71.28% | 55.92% |
| **Naive Bayes Balanced** | **65.82%** | **57.68%** |

## Final Model

### Naive Bayes Balanced

The final model is selected using **Macro F1** rather than accuracy because the sentiment classes are imbalanced.

- Accuracy: **65.82%**
- Macro F1: **57.68%**
- Neutral Recall: **45.15%**

Although baseline SVM has higher accuracy, Naive Bayes Balanced provides the strongest Macro F1 and substantially improves detection of the minority Neutral class.

## Business Insights

### 1. Negative feedback dominates the collected review set
Negative reviews represent approximately **62.4%** of the collected dataset, making negative feedback the primary area for further investigation.

### 2. Application experience is a recurring topic
Terms related to the **application, features, usage, problems, and errors** appear repeatedly in the review vocabulary.

### 3. Driver experience is an important customer touchpoint
The term **driver** appears across positive, neutral, and negative reviews, suggesting that driver interactions can contribute to both positive and negative customer experiences.

### 4. Ordering and transaction experience deserve further investigation
Recurring vocabulary around **orders, payments, transactions, promotions, and balance** indicates potential areas for deeper customer-journey analysis.

### 5. Neutral sentiment is difficult to classify
The Neutral class is the most challenging class for the tested models. Class balancing improves Neutral detection, particularly for Naive Bayes.

## Key Takeaway

This project demonstrates that model selection should not rely on accuracy alone when the target classes are imbalanced. Combining model evaluation with text-based exploration provides a more complete view of user feedback and potential product/service improvement areas.

## Tools

- Python
- Pandas
- NumPy
- Scikit-learn
- Sastrawi
- Matplotlib
- Seaborn
- WordCloud

## Repository Structure

```text
gojek-sentiment-analysis/
├── README.md
├── notebook/
│   └── Gojek_App_Review_Sentiment_Analysis.ipynb
├── images/
│   ├── sentiment_distribution.png
│   ├── model_comparison.png
│   ├── confusion_matrix_final.png
│   ├── wordcloud_negative.png
│   ├── wordcloud_neutral.png
│   └── wordcloud_positive.png
├── data/
│   └── README.md
├── requirements.txt
└── .gitignore
```

## Disclaimer

The project analyzes a collected review dataset and is intended for portfolio and educational purposes. Business implications are exploratory and should be validated with additional operational or customer-level data before being used for business decisions.
