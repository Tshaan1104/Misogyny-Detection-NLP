Unmasking Misogyny: Hierarchical Detection in Hindi-English Code-Mixed Digital Discourse
📌 Overview

Online misogyny is a growing issue in digital spaces, particularly in India, where Hindi-English code-mixed comments are common on platforms like YouTube. Detecting such misogynistic attitudes is challenging due to linguistic complexity, cultural nuances, and class imbalance.

This project proposes a hierarchical classification system that detects misogyny in Hindi-English code-mixed comments by performing:

Sentiment Classification → Optimistic, Pessimistic, Neutral

Comment Categorization → Suggestion, Appreciation, Criticism, Offensive, None

The ultimate goal is to make online spaces safer by automating misogyny detection in multilingual contexts.

👩‍💻 Authors
 Tiwari Shaan

📊 Dataset

Source: Singh et al. (2025) — YouTube comments on women’s safety

Size: 12,698 comments

Subtask 1 (Sentiment)

Optimistic: 1,629

Pessimistic: 3,929

Neutral: 7,140

Subtask 2 (Categorization)

Suggestion: 639

Appreciation: 405

Criticism: 2,436

Offensive: 1,493

None: 7,725

⚙️ Methodology
🔹 Preprocessing

Lowercasing

Removing emoticons, URLs, and noise

🔹 Dataset Balancing

Subtask 1: Random oversampling (minority classes → match Neutral)

Subtask 2: Hybrid oversampling + undersampling

🔹 Feature Extraction

paraphrase-multilingual-MiniLM-L12-v2 (Sentence-BERT family)

Chosen for better handling of code-mixed semantics compared to mBERT / FastText

🔹 Models Tested

MLP (Multi-Layer Perceptron) ✅ Best performer

BiLSTM

Decision Tree

Logistic Regression

SVM

KNN

Multinomial Naïve Bayes

🔹 Evaluation Metrics

Macro / Weighted Precision, Recall, F1-score

Accuracy comparison

🚀 Results
Subtask	Best Model	Accuracy	Highlight
Sentiment Classification	MLP	75%	Balanced performance across Optimistic & Pessimistic
Comment Categorization	MLP	73%	High F1-score (0.90) on minority class Appreciation

🔑 Key Insights

MLP outperformed all baselines.

Sentence-level embeddings from MiniLM captured nuances in Hindi-English better than traditional models.

BiLSTM underperformed (F1: 0.36/0.17) due to oversampling sensitivity.

Severe class imbalance remained the biggest challenge.

📌 Challenges

Code-mixing complexity → Hindi-English switching within comments.

Class imbalance → “Neutral” & “None” dominating the dataset.

Deep learning limitations → BiLSTM struggled with small minority classes.

✅ Conclusion

We developed a hierarchical classification pipeline for misogyny detection in Hindi-English YouTube comments.

Achieved ~75% accuracy (Sentiment) and ~73% accuracy (Categorization) with MLP.

Demonstrated that MiniLM embeddings + MLP outperform baselines.

Contributes to building safer online spaces via automated detection in multilingual settings.

📂 Repository Structure (Suggested)
├── Misogyny Detection Using NLP    # Code Notebook
|──Misogynistic_Attitude_Detection_DataSet
├── results/               # Saved metrics, plots, model comparisons
├── README.md              # Project documentation
└── Requirements.txt       # Dependencies

🔧 Installation & Usage
1️⃣ Clone the repo
git clone https://github.com/your-username/unmasking-misogyny.git
cd unmasking-misogyny

📚 References

Founta et al. (2019) – RNNs on large-scale tweets

Guest et al. (2021) – MLP vs. SVM on misogyny detection

Pamungkas et al. (2018) – Cross-lingual SVM + RNN

Nayak et al. (2020) – LSTM + transfer learning

García-Díaz et al. (2023) – BETO embeddings for Spanish

Singh et al. (2025) – mBERT on Hindi-English misogyny detection

Aluru et al. (2020) – XLM-RoBERTa + augmentation