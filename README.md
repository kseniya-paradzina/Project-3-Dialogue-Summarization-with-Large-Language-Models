# Project 3: Large Language Models for Dialogue Summarization

This repository contains an end-to-end transformer-based approach to **abstractive dialogue summarization** using the **SAMSum dataset**. The project explores model training, evaluation, error analysis, and a downstream application using an action-first LLM prompting layer.

---

## 📌 Project Overview

The goal of this project is to build and evaluate a dialogue summarization system under realistic computational constraints. We fine-tune a **BERT–GPT-2 encoder–decoder model** and compare its performance against a simple extractive baseline.

Beyond summarization, we demonstrate how model-generated summaries can be used as inputs to downstream LLM-based systems, highlighting both practical use cases and error propagation challenges.

---

## 🧠 Model Architecture

- **Encoder**: BERT
- **Decoder**: GPT-2
- **Architecture**: Transformer-based encoder–decoder
- **Task**: Abstractive dialogue summarization

---

## 📂 Dataset

- **SAMSum**: A dataset of messenger-style conversations paired with human-written summaries.

---

## ⚙️ How to run
1. Open the notebook in Google Colab
2. Install dependencies
3. Run all cells top to bottom
___

## ⚙️ Training Setup

- Framework: HuggingFace Transformers
- Training strategy: Fine-tuning with `Seq2SeqTrainer`
- Hardware: Google Colab (CPU/GPU)
- Epochs: 1 (resource-constrained setup)

---

## 📊 Evaluation

We evaluate model performance using multiple complementary approaches:

### Baseline
- Simple extractive heuristic: concatenation of the first and last dialogue utterances.

### Metrics
- Custom implementation of **ROUGE-1** and **ROUGE-L**
- Official **ROUGE-1 / ROUGE-2 / ROUGE-L** using HuggingFace `evaluate`

### Official ROUGE Results (F1)
```
ROUGE-1: 0.1443
ROUGE-2: 0.0153
ROUGE-L: 0.1127
```
---

## 🔍 Qualitative Analysis

Qualitative inspection reveals a clear contrast between the baseline and the abstractive model:

- The baseline remains grounded in the dialogue but lacks abstraction.
- The model generates fluent and coherent summaries but occasionally exhibits **semantic drift and hallucinations**.

These examples illustrate a well-known trade-off in dialogue summarization: extractive methods achieve higher lexical overlap, while abstractive models offer better linguistic quality at the cost of factual reliability.

---

## 🔗 Downstream Application: Action-First Prompting

To demonstrate real-world applicability, we design an **action-first ChatGPT-style prompting layer** that consumes model-generated summaries and extracts:

- Key decisions
- Action items with owners and deadlines
- Open questions or unresolved issues

This experiment highlights how summarization errors can propagate into downstream LLM-based systems, emphasizing the importance of faithful and grounded summaries in production settings.

---

## ⚠️ Limitations

- Limited training data and compute resources
- ROUGE metrics do not fully capture semantic faithfulness
- Occasional hallucinations due to lack of explicit grounding or copy mechanisms

---

## 🚀 Future Work

- Fine-tune larger encoder–decoder models (e.g., BART, T5)
- Incorporate semantic metrics such as BERTScore
- Apply human feedback or RLHF-style fine-tuning
- Deploy the model as an API and integrate it into a real chat application

---

## 📁 Repository Structure
```
.
├── Project_3_Dialogue_Summarization_LLMs.ipynb
└── README.md
```

---

## ✅ Final Remarks

This project demonstrates a complete and realistic dialogue summarization pipeline, combining model development, evaluation, error analysis, and system-level integration. While not state-of-the-art, it provides valuable insights into the challenges of abstractive summarization and LLM-based system design under real-world constraints.

___ 

## Author: Kseniya Paradzina  
## Course: Large Language Models  


