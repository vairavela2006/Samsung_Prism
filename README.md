# Samsung_Prism
# Contextual Spell Correction using LoRA

## 📌 Project Overview
This project implements a **Contextual Spell Correction system** using a **Masked Language Model (MiniLM)** fine-tuned with **LoRA (Low-Rank Adaptation)**.  
Unlike traditional spell checkers, this model corrects spelling errors **based on sentence context** and selects the correct word **only from a restricted set of candidate words**.

The approach is efficient, lightweight, and suitable for real-time applications.

---

## 🎯 Key Objectives
- Perform **context-aware spell correction**
- Restrict predictions to **predefined candidate words**
- Use **LoRA** for parameter-efficient fine-tuning
- Support **multilingual input (English + Korean)**
- Avoid full vocabulary generation

---

## 🧠 Core Idea
Given a sentence containing a `[MASK]` token and a list of candidate corrections, the model:
1. Predicts token probabilities at the `[MASK]` position
2. Filters logits to **only candidate tokens**
3. Selects the best candidate using softmax

This ensures **controlled, accurate, and context-driven correction**.

---

## 🏗️ Model Architecture
- **Base Model**: MiniLM (Masked Language Model)
- **Fine-Tuning**: LoRA adapters on attention layers
- **Task Type**: Token-level classification
- **Prediction**: Restricted candidate selection

---

---

## 📊 Dataset Format
Each data sample contains:
```json
{
  "sentence": "She loves to drink [MASK] in the morning.",
  "candidates": ["coffee", "cofee", "coffi"],
  "label": "coffee"
}

---

---

## Why LoRA is Useful

For Contextual Spell Correction, LoRA (Low-Rank Adaptation) is used to efficiently fine-tune a large language model without updating all its parameters.

1. Efficient Fine-Tuning

Only 0.5% – 2% of the model parameters are trained

Requires less GPU memory

Easily runs on Google Colab

This helps the model focus on context-based correction rather than memorizing spelling rules.

2. Prevents Overfitting

Spell-correction datasets are generally small

LoRA freezes the core language model weights

Preserves grammar and semantic knowledge

This is important for accurate contextual understanding.

3. Faster Training

Significantly reduces training time

Enables multiple experiments in a short time

This is ideal for academic projects and deadlines.

4. Language-Agnostic

The same LoRA technique works for:

English

Korean

Multilingual models

This makes LoRA suitable for English + Korean (EN + KO) datasets.

5. Better Generalization

Learns error-correction patterns

Does not depend only on dictionary replacements

Example:

Wrong : I went too the market
Right : I went to the market


LoRA helps the model understand contextual word usage, not just spelling.

## Overfitting

What is Overfitting?

Overfitting occurs when a model learns the training data too well, including its noise and mistakes, and performs poorly on new, unseen data.

Simple Real-Life Example

If you memorize answers instead of understanding concepts:

Same questions → high score ✅

New questions → low score ❌

This situation is called overfitting.
