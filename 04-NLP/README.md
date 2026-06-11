# 04 — Natural Language Processing (NLP)

<div align="center">

[![Natural Language Processing](../assets/nlp_banner.png)](../README.md)

</div>

> My notes from the Natural Language Processing sessions of the Pupilica AI Bootcamp.

---

## What's in this folder

| File / Resource | Action / Type | Description |
|:---|:---|:---|
| `NLP_Training.ipynb` | [![Training Notebook](https://img.shields.io/badge/Jupyter-Training-orange?logo=jupyter&style=flat-square)](./NLP_Training.ipynb) | Notebook covering text cleaning, vectorization (TF-IDF), custom Word2Vec training, classification, and pre-trained transformers |

---

## Topics Covered & Methodologies

### 1. Text Preprocessing (Noise Reduction)
Text is naturally unstructured and noisy. Cleaning maps sentences into clean, comparable token structures:
- **Tokenization**: Breaking down continuous text streams into distinct word tokens (using NLTK's `word_tokenize`).
- **Stopwords & Punctuation Filtering**: Removing structural filler words (e.g. `the`, `is`, `and`) and special characters (`string.punctuation`) that lack semantic sentiment signals.
- **Stemming**: Chopping off suffixes heuristically (using the `PorterStemmer`). Can lead to over-stemming (collapsing distinct words to the same stem) or under-stemming (leaving related words separate).
  - *Example*: `running`, `runs` $\rightarrow$ `run`.
- **Lemmatization**: Reducing words to their linguistically valid base vocabulary dictionary form (lemma) using `WordNetLemmatizer`. Takes POS (part-of-speech) tags into account.
  - *Example*: `better` $\rightarrow$ `good`, `was` $\rightarrow$ `be`.

### 2. Numerical Text representation (Vectorization)
Converting documents into matrices where columns represent features:
- **Bag-of-Words (BoW)**: Summarizes documents by counting occurrences of each vocabulary word, throwing away grammatical syntax and word ordering.
- **TF-IDF (Term Frequency-Inverse Document Frequency)**: A statistical weighting metric that increases with the number of times a word appears in a document, but is balanced by how common that word is across the entire corpus.
  - **Term Frequency (TF)**:
    $$\text{TF}(t, d) = \frac{\text{Count of term } t \text{ in document } d}{\text{Total terms in document } d}$$
  - **Inverse Document Frequency (IDF)**:
    $$\text{IDF}(t, D) = \log\left(\frac{\text{Total number of documents } |D|}{1 + \text{Number of documents containing term } t}\right)$$
  - **TF-IDF Weight**:
    $$\text{TF-IDF}(t, d, D) = \text{TF}(t, d) \times \text{IDF}(t, D)$$

### 3. Word Embeddings (Word2Vec)
Maps words to dense, low-dimensional continuous vector spaces. Words with similar contextual distributions end up physically closer in the vector space, capturing semantic relationships:
- **Continuous Bag-of-Words (CBOW)**: Predicts a central target word given its surrounding context words.
- **Skip-gram**: Predicts surrounding context words given a single central target word. Recommended for larger datasets and rare words.
- **Vector Arithmetic**: Captures semantic dimensions algebraically:
  $$\vec{v}(\text{"king"}) - \vec{v}(\text{"man"}) + \vec{v}(\text{"woman"}) \approx \vec{v}(\text{"queen"})}$$

### 4. Sentiment Classification
- Preprocessed a reviews dataset using tokenization, stopword removal, and lemmatization.
- Vectorized the cleaned reviews using Scikit-Learn's `TfidfVectorizer`.
- Trained a `LogisticRegression` classification model to predict positive ($1$) vs. negative ($0$) labels.
- Measured effectiveness using standard evaluation metrics: Accuracy, Precision, Recall, and F1-Score.

### 5. Attention & Transformer Models
Modern state-of-the-art NLP models (BERT, GPT) replace RNNs with parallelizable **Self-Attention Mechanisms**:
- **Self-Attention**: Computes dynamic relationships between all words in a sequence simultaneously using Query ($Q$), Key ($K$), and Value ($V$) projections.
- **Scaled Dot-Product Attention**:
  $$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^T}{\sqrt{d_k}}\right)V$$
  Where $d_k$ is the dimensionality of the keys, scaling the dot-product to prevent vanishing gradients in the softmax.
- **Hugging Face Pipeline API**: Leveraging large scale pre-trained weights for zero-shot text classification, sentiment extraction, and text generation without custom local training.

---

## Key Things I Want to Remember
- Traditional TF-IDF matrices are highly sparse and ignore word order or meaning. Embeddings (Word2Vec) solve this by creating dense vectors that map semantic relationships.
- Transformers handle long-range dependencies better than recurrent models (RNNs/LSTMs) because self-attention connects any two tokens directly, regardless of distance.
- Pre-trained models can be quickly adapted for custom downstream tasks (fine-tuning) with minimal training data.

---

[← Deep Learning](../03-Deep-Learning/)
