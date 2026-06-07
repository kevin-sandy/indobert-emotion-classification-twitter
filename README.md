# 🇮🇩 Indonesian Emotion Classification with IndoBERT

Multiclass emotion classification for Indonesian text using **IndoBERT** and **Hugging Face Transformers**. This project was developed as part of the **NoLimit Indonesia Data Scientist Hiring Test**.

## Overview

The objective of this project is to classify Indonesian text into five emotion categories:

* 😡 Anger
* 😨 Fear
* 😊 Happy
* ❤️ Love
* 😢 Sadness

The model is fine-tuned from **IndoBERT Base P1** and evaluated using standard classification metrics such as Accuracy, Precision, Recall, and F1 Score.

---

## Dataset

**Source:**
https://www.kaggle.com/datasets/dennisherdi/indonesian-twitter-emotion

### Emotion Labels

| Label   | Description       |
| ------- | ----------------- |
| anger   | Anger emotion     |
| fear    | Fear or anxiety   |
| happy   | Happiness or joy  |
| love    | Affection or love |
| sadness | Sadness           |

### Data Split

| Split      | Ratio |
| ---------- | ----- |
| Train      | 70%   |
| Validation | 15%   |
| Test       | 15%   |

---

## Project Structure

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

## Methodology

### 1. Data Preprocessing

The following preprocessing steps were applied:

* Lowercasing
* URL removal
* Mention removal
* Hashtag normalization
* Repeated character normalization
* Indonesian slang normalization
* Whitespace normalization

### Example

**Input**

```text
GAKKK suka banget sama pelayanan ini!!!
```

**Output**

```text
tidak suka banget sama pelayanan ini!!!
```

---

### 2. Tokenization

Tokenizer used:

```text
indobenchmark/indobert-base-p1
```

---

### 3. Model Fine-Tuning

**Base Model**

```text
indobenchmark/indobert-base-p1
```

**Framework**

* PyTorch
* Hugging Face Transformers

### Training Configuration

| Parameter         | Value    |
| ----------------- | -------- |
| Learning Rate     | 1e-5     |
| Batch Size        | 8        |
| Epochs            | 15       |
| Weight Decay      | 0.01     |
| Warmup Ratio      | 0.1      |
| FP16              | Enabled  |
| Evaluation Metric | Macro F1 |

---

## Results

### Test Set Performance

| Metric            | Score |
| ----------------- | ----- |
| Accuracy          | 0.74  |
| Macro Precision   | 0.76  |
| Macro Recall      | 0.75  |
| Macro F1 Score    | 0.75  |
| Weighted F1 Score | 0.74  |

### Classification Report

| Label   | Precision | Recall | F1-Score |
| ------- | --------- | ------ | -------- |
| anger   | 0.79      | 0.80   | 0.80     |
| fear    | 0.71      | 0.68   | 0.69     |
| happy   | 0.80      | 0.77   | 0.79     |
| love    | 0.74      | 0.79   | 0.76     |
| sadness | 0.75      | 0.72   | 0.74     |

---

## Sample Predictions

| Text                             | Predicted Emotion |
| -------------------------------- | ----------------- |
| aku sangat senang hari ini       | happy             |
| aku kecewa dengan hasilnya       | sadness           |
| aku takut menghadapi ujian besok | fear              |
| aku sangat menyayanginya         | love              |
| aku marah dengan pelayanan ini   | anger             |

---

## Installation

Clone the repository:

```bash
git clone https://github.com/kevin-sandy/indobert-emotion-classification-twitter.git
cd indobert-emotion-classification-twitter
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Training

Train the model:

```bash
python train.py
```

---

## Evaluation

Evaluate the trained model:

```bash
python evaluate.py
```

---

## Inference

```python
from transformers import pipeline

classifier = pipeline(
    task="text-classification",
    model="./models/best_model",
    tokenizer="./models/best_model"
)

result = classifier("aku sangat senang hari ini")

print(result)
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

## Workflow

```text
Dataset
   │
   ▼
Preprocessing
   │
   ▼
Label Encoding
   │
   ▼
Train / Validation / Test Split
   │
   ▼
Tokenization
   │
   ▼
IndoBERT Fine-Tuning
   │
   ▼
Evaluation
   │
   ▼
Prediction
```

The complete workflow visualization is available in:

```text
flowchart.png
```

---

## Technologies

* Python
* PyTorch
* Hugging Face Transformers
* Scikit-learn
* Pandas
* NumPy

---

## Author

**Kevin Sandy Dimpos Manurung**

Data Science Undergraduate

Project submitted for the **NoLimit Indonesia Data Scientist Hiring Test**.
