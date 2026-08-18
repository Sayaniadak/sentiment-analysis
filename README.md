Yes — for **GitHub**, the README should be more project-oriented and concise, while still documenting the dissertation methodology. You can use this directly as your `README.md`:

# 📰 Political News Sentiment Analysis

A comparative study of **VADER, BERT, RoBERTa, and DistilBERT** for sentiment classification of political news articles.

## 📌 Project Overview

This project investigates whether fine-tuned Transformer-based NLP models can outperform traditional lexicon-based sentiment analysis for political news.

The study uses the **All the News** dataset, filters articles related to politics using keyword matching, and automatically generates sentiment labels using **VADER**. Three Transformer models are then fine-tuned and evaluated against the VADER baseline.

### Models Compared

* **VADER** — Traditional lexicon-based baseline
* **BERT** — `bert-base-uncased`
* **RoBERTa** — `roberta-base`
* **DistilBERT** — `distilbert-base-uncased`

---

## 📂 Dataset

**Dataset:** All the News
**Source:** Kaggle / Snapcrack

The dataset was filtered to identify political news articles using keyword-based matching.

### Automatic Labelling

VADER compound scores were converted into three sentiment classes:

| Compound Score  | Sentiment   |
| --------------- | ----------- |
| `> 0.05`        | 🟢 Positive |
| `< -0.05`       | 🔴 Negative |
| `-0.05 to 0.05` | ⚪ Neutral   |

The labelling approach follows the methodology described by **Samin et al. (2024)**.

---

## 🔬 Methodology

### 1. Data Preparation

* Load the All the News dataset
* Filter articles related to politics
* Clean and preprocess the text
* Generate sentiment labels using VADER
* Perform a stratified train/validation/test split

### 2. Dataset Split

```text
Training Set    → 70%
Validation Set  → 15%
Test Set        → 15%
```

Stratification was applied to preserve the distribution of sentiment classes across the three datasets.

### 3. Model Training

The following Transformer models were fine-tuned:

```text
BERT
RoBERTa
DistilBERT
```

VADER was used as the **non-trained baseline**.

### ⚙️ Training Configuration

| Parameter               |     Value |
| ----------------------- | --------: |
| Epochs                  |         3 |
| Learning Rate           |      2e-5 |
| Warmup Ratio            |       0.1 |
| Weight Decay            |      0.01 |
| Batch Size              |        16 |
| Maximum Sequence Length |       256 |
| Dataset Split           |  70/15/15 |
| GPU                     | NVIDIA T4 |

---

## 📊 Evaluation Metrics

The models are evaluated using:

* **Accuracy**
* **Macro Precision**
* **Macro Recall**
* **Macro F1-score**

Macro F1-score is particularly important because it gives equal importance to all sentiment classes.

---

## 🏆 Results

Final results are available in:

```text
final_results.csv
```

### Visualizations

#### Model Comparison

![Model Comparison](model_comparison_chart.png)

#### F1-Score Ranking

![F1 Ranking](f1_ranking.png)

### Confusion Matrices

#### VADER

![VADER Confusion Matrix](confusion_matrix_vader.png)

#### BERT

![BERT Confusion Matrix](confusion_matrix_bert.png)

#### RoBERTa

![RoBERTa Confusion Matrix](confusion_matrix_roberta.png)

#### DistilBERT

![DistilBERT Confusion Matrix](confusion_matrix_distilbert.png)

> **Note:** The final winning model and exact performance values should be taken from `final_results.csv`.

---

## 🛠️ Technology Stack

| Technology               | Purpose                                  |
| ------------------------ | ---------------------------------------- |
| Python                   | Programming language                     |
| PyTorch                  | Deep learning framework                  |
| HuggingFace Transformers | Transformer models                       |
| VADER                    | Sentiment baseline & automatic labelling |
| Pandas                   | Data processing                          |
| Scikit-learn             | Data splitting & evaluation              |
| Matplotlib               | Visualization                            |
| Google Colab             | Development environment                  |
| NVIDIA T4 GPU            | Model training                           |

---

## 📁 Project Structure

```text
Political-News-Sentiment-Analysis/
│
├── README.md
├── final_results.csv
│
├── model_comparison_chart.png
├── f1_ranking.png
│
├── confusion_matrix_vader.png
├── confusion_matrix_bert.png
├── confusion_matrix_roberta.png
├── confusion_matrix_distilbert.png
│
├── notebooks/
│   └── sentiment_analysis.ipynb
│
└── requirements.txt
```

---

## 🚀 Getting Started

### Clone the Repository

```bash
git clone https://github.com/<your-username>/<repository-name>.git
cd <repository-name>
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run the Notebook

Open:

```text
notebooks/sentiment_analysis.ipynb
```

The notebook contains the complete workflow:

```text
Dataset
   ↓
Political Article Filtering
   ↓
Text Preprocessing
   ↓
VADER Labelling
   ↓
Train / Validation / Test Split
   ↓
Transformer Fine-Tuning
   ↓
Model Evaluation
   ↓
Confusion Matrices
   ↓
Performance Comparison
```

---

## ⚠️ Limitations

### Automatic Labelling

VADER-generated labels may contain noise because they are not based on human annotation.

### Dataset Dependency

The study relies on a single news dataset, which may limit the generalisability of the results.

### English Language

The current implementation focuses exclusively on English-language news articles.

### Keyword-Based Filtering

Political articles are identified through keyword matching, which may result in false positives or false negatives.

---

## 🔮 Future Work

Potential extensions include:

* 🌍 **Multilingual sentiment analysis** using multilingual Transformer models
* 🔍 **Explainable AI** using SHAP and LIME
* 📡 **Real-time sentiment monitoring** of political news
* 👥 **Human-annotated datasets** for improved label quality
* 🤖 Evaluation of larger and more advanced language models
* 📈 Real-time dashboards for monitoring political sentiment trends

---

## 📚 Research Context

This project was developed as part of a dissertation on **sentiment analysis of political news using Natural Language Processing and Transformer-based models**.

The methodology incorporates VADER-based automatic labelling and comparative evaluation of fine-tuned BERT-family models.

---

## 👩‍💻 Author

**Sayani Adak**
B.Tech — Computer Science & Engineering (AI & ML)

---

## 📄 License

This project is intended for **academic and research purposes**.
