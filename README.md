# Data4Good 2025 — Factuality Verification via NLI Reframing

**Regional Champions | Data4Good 2025**  
**Final Test Score: 99.11% Balanced Accuracy**

This repository contains our winning solution to the **Data4Good 2025 National Analytics Competition**, focused on detecting factual errors in AI-generated educational responses.  
The core contribution is a **problem reframing**: treating factuality verification as a **Natural Language Inference (NLI)** task, combined with selective LLM arbitration for ambiguous cases.

---

## Problem Context

Large language models increasingly assist learners, but confidently stated incorrect answers pose serious risks in education.  
The task is to classify AI-generated responses as:

- **Factual** — supported by provided context  
- **Contradiction** — conflicts with known facts  
- **Irrelevant** — unrelated or unsupported  

Naive classification approaches fail due to missing context, ambiguity, and distributional quirks in real educational data.

---

## Key Insight

**Factuality verification is not a flat classification problem.**  
It is an *inference problem* between a claim and its context.

Reframing the task as **Natural Language Inference (entailment / contradiction / neutral)** revealed structure that standard classifiers miss and enabled consistent generalization across edge cases.

---

## Solution Overview

Our system uses a **controlled, two-regime pipeline**:

1. **NLI Backbone (Primary Path)**  
   - DeBERTa-v3 Large fine-tuned for inference between answer and context  
   - High confidence and stability when sufficient context exists

2. **LLM Arbitration (Selective Path)**  
   - Activated only for ambiguous or no-context samples  
   - Used as a *judge*, not a generator  
   - Reduces brittle false positives without inflating cost

3. **Explicit Decision Logic**  
   - Context presence is treated as a first-class signal  
   - No silent assumptions, no blind ensembling

This design prioritizes **causality, robustness, and deployability** over brute-force tuning.

---

## Dataset

- ~21,000 training samples  
- ~2,000 held-out test samples  
- Each sample consists of `(question, context, AI answer, label)`  
- ~9% of samples contain **no usable context**, a key failure mode addressed explicitly

---

## Evaluation Protocol

- **Primary metric:** Balanced Accuracy  
- Cross-validation with strict train/validation separation  
- Drift checks between train and test distributions  
- Final leaderboard score aligned with offline validation

---

## Results

- **Final Test Performance:** 99.11% balanced accuracy  
- **Validation Performance:** 99.78%  
- **Error Reduction:** 96% reduction vs baseline  
- **Rank:** 1st place (Regional Champions)

Performance gains were driven by *problem structure*, not model size escalation.


---

## What This Repository Is (and Is Not)

**This is:**
- A principled, end-to-end solution to factuality verification  
- A demonstration of correct task framing under ambiguity  
- A reproducible competition-grade pipeline

**This is not:**
- A prompt-engineering demo  
- A leaderboard-only hack  
- A model zoo

---

## Limitations

- Some samples are genuinely ambiguous even for humans  
- The LLM arbitration step depends on external APIs  
- Not designed for open-ended generation tasks

These limits are explicit and intentional.

---

## Team

**Georgia Institute of Technology**  
- Subhajit Bag  
- Soham Pradhan  
- Aditya Ghosh  
- Deepak Alagusubramanian  

---

## Competition

**Data4Good 2025**  
Organized by **Purdue University**, **Johns Hopkins Carey Business School**, and **INFORMS**  
Theme: *Trustworthy AI for Education*  
National Finals: Johns Hopkins, Washington DC

---

> Correct answers build trust.  
> Correct *reasoning* sustains it.


## Repository Structure

