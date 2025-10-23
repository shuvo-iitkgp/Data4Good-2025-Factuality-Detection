# 🧠 Data4Good-2025-Factuality-Detection

Detecting factuality in AI-generated educational responses using transformer-based models and retrieval-augmented context understanding.  
This project was developed for the **Data4Good 2025 Competition** — a national analytics challenge organized by **Purdue University**, **Johns Hopkins Carey Business School**, and **INFORMS**.

---

## 🌍 Overview

Large Language Models (LLMs) are transforming education but also risk spreading misinformation through confident yet incorrect answers.  
This project builds an **end-to-end NLP pipeline** to classify AI-generated answers as:

- ✅ **Factual** — the answer is correct and grounded in context  
- ❌ **Contradiction** — the answer conflicts with known facts  
- 🚫 **Irrelevant** — the answer is unrelated to the question  

---

## ⚙️ Key Highlights

- **Modeling Approach:**  
  - Retrieval-augmented context selection (BM25 + semantic ranking)  
  - Cross-Encoder using **DeBERTa-v3 Large** for multi-class factuality classification  
  - Auxiliary NLI task to improve contradiction detection  
  - Two-stage cascade: Irrelevance filter → Factual vs. Contradiction classifier  
  - Class-balanced **Focal Loss** and **Temperature Calibration**

- **Evaluation:**  
  Custom weighted confusion-matrix scoring — equal emphasis on each class (factual / contradiction / irrelevant).

- **Dataset:**  
  21K training and 2K test examples of (question, context, answer) triplets provided by the Data4Good 2025 organizing committee.

- **Results:**  
  +9 pp macro-F1 improvement over baselines; strongest gains on minority classes (contradiction, irrelevant).

---

## 🧩 Tech Stack

**Python**, **PyTorch**, **Transformers (HuggingFace)**, **scikit-learn**, **BM25 / Rank-BM25**, **Pandas**, **Matplotlib**

---

## 📊 Competition Context

- Organized by: *Purdue University* x *Johns Hopkins Carey Business School* x *INFORMS*  
- Theme: *AI for Education & Trustworthiness*  
- Goal: Develop responsible AI solutions to ensure factual integrity in digital learning environments  
- Regional Winners → National Championship (Johns Hopkins, Washington D.C.)

---

## 🧠 Learning Takeaways

- Hands-on experience with **LLM factuality detection** and **hallucination mitigation**  
- Explored **retrieval-augmented classification** and **context-window optimization**  
- Built explainable, reproducible NLP pipelines with documented CV and calibration

---

## 📁 Repository Structure

