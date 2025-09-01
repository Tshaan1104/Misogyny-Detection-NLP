# Unmasking Misogyny: Hierarchical Detection in Hindi-English Code-Mixed Digital Discourse

---

## 📑 Table of Contents

- [Overview](#overview)
- [Authors](#authors)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Results](#results)
- [Key Insights](#key-insights)
- [Challenges](#challenges)
- [Conclusion](#conclusion)
- [Repository Structure](#repository-structure)
- [Installation & Usage](#installation--usage)
- [References](#references)

---

## 📌 Overview

Online misogyny is a growing issue in digital spaces, especially in India where Hindi-English code-mixed comments are common (e.g., YouTube). Detecting such attitudes is challenging due to linguistic complexity and class imbalance.

This project proposes a **hierarchical classification system** for misogyny detection in Hindi-English code-mixed comments, consisting of:

- **Sentiment Classification:** Optimistic, Pessimistic, Neutral
- **Comment Categorization:** Suggestion, Appreciation, Criticism, Offensive, None

The goal: **Make online spaces safer by automating misogyny detection in multilingual contexts.**

---

## 👩‍💻 Authors

- **Tiwari Shaan**

---

## 📊 Dataset

- **Source:** Singh et al. (2025) — YouTube comments on women’s safety
- **Size:** 12,698 comments

### Subtask 1: Sentiment

| Label        | Count  |
|--------------|--------|
| Optimistic   | 1,629  |
| Pessimistic  | 3,929  |
| Neutral      | 7,140  |

### Subtask 2: Categorization

| Label         | Count  |
|---------------|--------|
| Suggestion    | 639    |
| Appreciation  | 405    |
| Criticism     | 2,436  |
| Offensive     | 1,493  |
| None          | 7,725  |

---

## ⚙️ Methodology

### 🔹 Preprocessing

- Lowercasing
- Removing emoticons, URLs, and noise

### 🔹 Dataset Balancing

- **Subtask 1:** Random oversampling (minority classes → match Neutral)
- **Subtask 2:** Hybrid oversampling + undersampling

### 🔹 Feature Extraction

- **Model:** `paraphrase-multilingual-MiniLM-L12-v2` (Sentence-BERT family)
- Chosen for handling code-mixed semantics better than mBERT / FastText

### 🔹 Models Tested

- **MLP (Multi-Layer Perceptron) ✅ Best performer**
- BiLSTM
- Decision Tree
- Logistic Regression
- SVM
- KNN
- Multinomial Naïve Bayes

### 🔹 Evaluation Metrics

- Macro / Weighted Precision, Recall, F1-score
- Accuracy comparison

---

## 🚀 Results

| Subtask                | Best Model | Accuracy | Highlight                                   |
|------------------------|------------|----------|---------------------------------------------|
| Sentiment Classification | MLP        | 75%      | Balanced performance across all classes     |
| Comment Categorization  | MLP        | 73%      | High F1-score (0.90) on minority class      |
|                        |            |          | Appreciation                                |

---

## 🔑 Key Insights

- MLP outperformed all baselines.
- Sentence-level embeddings from MiniLM captured Hindi-English nuances better than traditional models.
- BiLSTM underperformed (F1: 0.36/0.17) due to oversampling sensitivity.
- Severe class imbalance remained the biggest challenge.

---

## 📌 Challenges

- **Code-mixing complexity:** Frequent Hindi-English switching within comments.
- **Class imbalance:** “Neutral” & “None” dominate the dataset.
- **Deep learning limitations:** BiLSTM struggled with small minority classes.

---

## ✅ Conclusion

- Developed a hierarchical pipeline for misogyny detection in Hindi-English YouTube comments.
- Achieved ~75% accuracy (Sentiment), ~73% accuracy (Categorization) with MLP.
- Demonstrated that MiniLM embeddings + MLP outperform baselines.
- Contributes to safer online spaces via automated detection in multilingual settings.

---

## 📂 Repository Structure

```text
├── Misogyny Detection Using NLP         # Code Notebook
├── Misogynistic_Attitude_Detection_DataSet
├── results/                            # Saved metrics, plots, model comparisons
├── README.md                           # Project documentation
└── Requirements.txt                    # Dependencies
```

---

## 🔧 Installation & Usage

1. **Clone the repo**
    ```sh
    git clone https://github.com/Tshaan1104/Misogyny-Detection-NLP
    cd Misogyny-Detection-NLP
    ```
2. **Install dependencies**
    ```sh
    pip install -r Requirements.txt
    ```
3. **Run the code notebook**
    - Open `Misogyny Detection Using NLP` in Jupyter Notebook or your preferred environment.

---

## 📚 References

- Founta et al. (2019) – RNNs on large-scale tweets
- Guest et al. (2021) – MLP vs. SVM on misogyny detection
- Pamungkas et al. (2018) – Cross-lingual SVM + RNN
- Nayak et al. (2020) – LSTM + transfer learning
- García-Díaz et al. (2023) – BETO embeddings for Spanish
- Singh et al. (2025) – mBERT on Hindi-English misogyny detection
- Aluru et al. (2020) – XLM-RoBERTa + augmentation

---