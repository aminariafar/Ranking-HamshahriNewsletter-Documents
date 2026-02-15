# 📚 Persian Information Retrieval System -- Hamshahri Corpus

This project implements a complete **Information Retrieval (IR) system**
for ranking Persian documents using the **Hamshahri Corpus**.

The system includes full preprocessing, indexing, multiple ranking
models, and systematic evaluation across varying retrieval depths.

------------------------------------------------------------------------

## ✨ Project Overview

The goal of this project is to design and compare multiple document
ranking models capable of retrieving relevant Persian news articles for
a given query.

The system works on the **Hamshahri Corpus (2003--2007)** and evaluates
performance using official relevance judgments.

------------------------------------------------------------------------

## 🧱 Repository Structure

    .
    ├── HamshahriCorpus/              # News articles (organized by year)
    │   ├── 2003/
    │   ├── 2004/
    │   ├── 2005/
    │   ├── 2006/
    │   └── 2007/
    │
    ├── Queries/                      # 50 test queries (1.q, 2.q, ...)
    ├── RelativeAssessment/
    │   └── judgements.txt            # Ground-truth relevance labels
    │
    ├── persian_stopwords.txt         # Persian stopword list
    ├── ranking_hamshahri_documents.ipynb # Main implementation notebook
    └── README.md

    # Note: The "HamshahriCorpus" folder is compressed into a .zip file.

------------------------------------------------------------------------

## 🔍 Dataset

**Hamshahri Corpus**

-   Persian news collection (2003--2007)
-   Large-scale benchmark dataset for Persian IR research
-   Includes:
    -   50 evaluation queries
    -   Relevance judgments for each query

This dataset presents realistic challenges such as: - Persian text
normalization - Inconsistent punctuation - Noisy tokens - Mixed
character encodings

------------------------------------------------------------------------

## 🧹 1. Preprocessing Pipeline

A robust preprocessing pipeline was implemented to improve retrieval
effectiveness:

-   Persian character normalization\
-   Removal of punctuation and unwanted symbols\
-   Removal of English characters\
-   Tokenization\
-   Stopword removal\
-   Term cleaning\
-   Alphabetical sorting of terms\
-   Creation of unique term lists

This ensures high-quality indexing and reduces noise in ranking.

------------------------------------------------------------------------

## 🗂 2. Indexing

The following core IR data structures were built:

### 📌 Vocabulary

All unique terms across the corpus after preprocessing.

### 📌 Inverted Index

Maps each term → list of document IDs containing it.

### 📌 Term Statistics

-   **TF (Term Frequency)**
-   **DF (Document Frequency)**
-   **IDF (Inverse Document Frequency)**

IDF formula:

IDF(t) = log(N / DF(t))

These structures enable efficient document scoring.

------------------------------------------------------------------------

## 📈 3. Ranking Models Implemented

Four ranking models were implemented as independent modules:

### 🔹 1. Okapi BM25

-   Probabilistic ranking model\
-   Handles term frequency saturation\
-   Includes document length normalization

### 🔹 2. Language Model (LM)

-   Query likelihood approach\
-   Uses smoothing (Dirichlet or Jelinek--Mercer)\
-   Addresses zero-probability issues

### 🔹 3. Vector Space Model (VSM)

-   TF-IDF weighting\
-   Cosine similarity\
-   Classic geometric interpretation

### 🔹 4. Hybrid Model

-   Weighted score fusion of BM25, LM, and VSM\
-   Improves robustness across query types

------------------------------------------------------------------------

## 📊 4. Evaluation

Evaluation was performed using:

RelativeAssessment/judgements.txt

For each query:

-   Let n = number of relevant documents\
-   Retrieve top n × α documents\
-   α sampled at 20 values in range:

1 ≤ α ≤ 10

------------------------------------------------------------------------

### 📏 Metrics Computed

For each model and each α:

-   Precision\
-   Recall\
-   F1-score

Metrics were averaged across all 50 queries.

------------------------------------------------------------------------

### 📈 Visualization

Performance curves were plotted showing:

-   Precision vs α\
-   Recall vs α\
-   F1-score vs α\
-   All four models compared together

This enables clear comparison of trade-offs and model behavior.


------------------------------------------------------------------------

## 🎓 Educational Context

Demonstrates:

-   End-to-end IR implementation\
-   Large-scale indexing\
-   Probabilistic & vector ranking\
-   Evaluation under varying retrieval thresholds

------------------------------------------------------------------------

## 🚀 Skills Demonstrated

-   Persian text preprocessing\
-   Inverted indexing\
-   TF-IDF modeling\
-   BM25 implementation\
-   Language modeling with smoothing\
-   Hybrid ranking systems\
-   Retrieval evaluation metrics\
-   Experimental analysis