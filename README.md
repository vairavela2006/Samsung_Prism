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

