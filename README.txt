---
language:
- id
metrics:
- f1
base_model:
- indobenchmark/indobert-base-p1
pipeline_tag: text-classification
library_name: transformers
tags:
- emotion-classification
- indobert
- twitter
---

# Indonesian Emotion Classification using IndoBERT

An NLP project for multiclass emotion classification in Indonesian text using the pre-trained IndoBERT model and Hugging Face Transformers.

## Objective

This project aims to classify Indonesian text into one of five emotion categories:

- Anger
- Fear
- Happy
- Love
- Sadness

The model is fine-tuned from IndoBERT and evaluated using Macro F1 Score, Weighted F1 Score, Accuracy, Precision, and Recall.

---

# Dataset

Dataset source:

- Indonesian Twitter Emotion Dataset https://www.kaggle.com/datasets/dennisherdi/indonesian-twitter-emotion

## Labels

| Label | Description |
|---------|-------------|
| anger | Anger emotion |
| fear | Fear or anxiety |
| happy | Happiness or joy |
| love | Affection or love |
| sadness | Sadness |

## Data Split

| Split | Percentage |
|---------|------------|
| Train | 70% |
| Validation | 15% |
| Test | 15% |

---

# Project Structure

```text
.
├── data/
├── notebooks/
├── models/
├── outputs/
├── train.py
├── evaluate.py
├── requirements.txt
├── README.md
└── flowchart.png
```

---

# Methodology

## 1. Data Preprocessing

Applied preprocessing steps:

- Lowercasing
- URL removal
- Mention removal
- Hashtag normalization
- Repeated character normalization
- Indonesian slang word normalization
- Whitespace normalization

Example:

Input:

```text
GAKKK suka banget sama pelayanan ini!!!
```

Output:

```text
tidak suka banget sama pelayanan ini!!!
```

---

## 2. Tokenization

Tokenizer:

```text
indobenchmark/indobert-base-p1
```

---

## 3. Model Fine-Tuning

Base Model:

```text
IndoBERT Base P1
```

Framework:

```text
Hugging Face Transformers
PyTorch
```

Training configuration:

| Parameter | Value |
|------------|---------|
| Learning Rate | 1e-5 |
| Batch Size | 8 |
| Epochs | 15 |
| Weight Decay | 0.01 |
| Warmup Ratio | 0.1 |
| FP16 | Enabled |
| Metric | Macro F1 |

---

# Results

## Test Performance

| Metric | Score |
|----------|----------|
| Accuracy | 0.74 |
| Macro F1 | 0.75 |
| Weighted F1 | 0.74 |
| Macro Precision | 0.76 |
| Macro Recall | 0.75 |

### Example Predictions

| Text | Prediction |
|--------|------------|
| aku sangat senang hari ini | happy |
| aku kecewa dengan hasilnya | sadness |
| aku takut menghadapi ujian besok | fear |
| aku sangat menyayanginya | love |
| aku marah dengan pelayanan ini | anger |

---

# Installation

Clone repository:

```bash
git clone https://github.com/kevin-sandy/indobert-emotion-classification-twitter.git
cd indobert-emotion-classification-twitter
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

# Training

```bash
python train.py
```

---

# Evaluation

```bash
python evaluate.py
```

---

# Inference

```python
from transformers import pipeline

classifier = pipeline(
    "text-classification",
    model="./models/best_model"
)

classifier("aku sangat senang hari ini")
```

Expected output:

```python
[
    {
        "label": "happy",
        "score": 0.95
    }
]
```

---

# Flowchart

The complete pipeline flowchart is available in:

```text
flowchart.png
```

Pipeline:

```text
Dataset
    ↓
Preprocessing
    ↓
Label Encoding
    ↓
Train / Validation / Test Split
    ↓
Tokenization
    ↓
IndoBERT Fine-Tuning
    ↓
Evaluation
    ↓
Prediction
```

---

# Technologies

- Python
- PyTorch
- Hugging Face Transformers
- Scikit-learn
- Pandas
- NumPy

---

# Author

Kevin Sandy Dimpos Manurung

NoLimit Indonesia – Data Scientist Hiring Test