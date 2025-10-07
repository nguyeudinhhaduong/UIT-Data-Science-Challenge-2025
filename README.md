# UIT Data Science Challenge 2025 — Hallucination Classification

This repository contains our solution for the **UIT Data Science Challenge 2025**, focusing on **text classification** to detect **hallucination types** in generative AI outputs.

---

## 📘 Overview

### 🧩 Task Description
The goal of this task is to **classify hallucination types** in the outputs of Large Language Models (LLMs).  

Each data sample includes:
- **Input:** User’s question or instruction  
- **Output:** Model-generated response  
- **Label:** One of three categories:
  - 🟢 **No** – Response is factual and grounded  
  - 🟡 **Intrinsic** – Hallucination caused by internal inconsistency  
  - 🔴 **Extrinsic** – Hallucination introducing external factual errors  

This task evaluates the **factual reliability and faithfulness** of LLM responses.

---

## 🧩 Dataset Format

| Field | Description |
|:------|:-------------|
| **Input** | User’s question or instruction |
| **Output** | Model-generated response |
| **Label** | One of `["No", "Intrinsic", "Extrinsic"]` |

**Example:**
```json
{
  "input": "Who is the current president of France?",
  "output": "The president of France is François Hollande.",
  "label": "Extrinsic"
}
```

---

## ⚙️ Models & Approaches

We experimented with several modeling strategies:

1. **Baseline Fine-tuning** — `MoritzLaurer/deberta-v3-base`  
2. **Enhanced Fine-tuning** — Improved preprocessing, data augmentation, and learning rate scheduling  
3. **Advanced Optimization** — Early stopping and custom evaluation metrics (Accuracy, F1-score)

---

## 🧠 Training Details

### Model: `MoritzLaurer/deberta-v3-base`

| Epoch | Training Loss | Validation Loss | Accuracy |
|:------:|:--------------:|:----------------:|:---------:|
| 1 | 0.3983 | 0.3723 | 0.8870 |
| 2 | 0.3400 | 0.3590 | 0.8954 |
| 3 | 0.3074 | 0.4101 | 0.8787 |
| 4 | 0.1800 | 0.4587 | 0.8991 |
| 5 | 0.1442 | 0.6436 | 0.8722 |
| 6 | 0.1388 | 0.6059 | 0.8833 |
| 7 | 0.1032 | 0.6055 | 0.8843 |

**Best Model:**
- Validation **F1 = 0.7910**
- Validation **Accuracy = 0.806**
- Training stopped early at **Epoch 11**

---

## 📊 Experiment Results

### Training Summary — *NLi (MoritzLaurer mDeBERTa-v3)*

| Step | Training Loss | Validation Loss | Accuracy | F1 |
|:----:|:--------------:|:----------------:|:---------:|:--:|
| 200 | — | 0.5919 | 0.7787 | 0.7776 |
| 400 | — | 0.6026 | 0.8065 | 0.8064 |
| 600 | 0.6053 | 0.6698 | 0.7991 | 0.7978 |
| 800 | 0.6053 | 0.8097 | 0.7815 | 0.7814 |
| 1000 | 0.2834 | 0.9077 | 0.7769 | 0.7772 |

---

### Hard NLI Training Summary

| Epoch | Training Loss | Validation F1 | Improvement |
|:------:|:--------------:|:--------------:|:-------------:|
| 1 | 0.708 | 0.6795 | ✅ New best |
| 2 | 0.271 | 0.7582 | ✅ Improved |
| 3 | 0.234 | 0.7621 | ✅ Improved |
| 4 | 0.209 | 0.7757 | ✅ Improved |
| 5 | 0.189 | 0.7796 | ✅ Improved |
| 6 | 0.173 | 0.7791 | — |
| 7 | 0.160 | 0.7844 | ✅ Improved |
| 8 | 0.145 | **0.7910** | 🏆 Best model |
| 9 | 0.134 | 0.7834 | — |
| 10 | 0.125 | 0.7885 | — |
| 11 | 0.116 | 0.7864 | — |

> 🧩 **Best checkpoint:** Epoch 8 → F1 = 0.7910  
> ⏹️ Early stopping after epoch 11 to prevent overfitting.

---

## 🚀 Final Evaluation

| Dataset | F1 Score | Accuracy |
|:---------:|:----------:|:-----------:|
| **Public Test** | 0.81 | 0.81 |
| **Private Test (Final Leaderboard)** | **0.80** | **0.80** |

🛪️ **Result:** The fine-tuned DeBERTa-v3 model achieved strong generalization on unseen hallucination data.

---

## 📂 Repository Structure

| File | Description |
|------|--------------|
| `finetuning_moritzlaurer_mdeberta_v3.ipynb` | Main fine-tuning script |
| `finetuning-model-timpal0lmdeberta-v3-base-squad2` | Main fine-tuning script |
| `hcmus-foursight- classification for hard nli-crossencoder` | Main hard fine-tuning script |
| `hcmus-foursight-processdata.ipynb` | Data preprocessing & augmentation |
| `hcmus-foursight-submit-for-private-test.ipynb` | Inference & submission script |
| `Classification-Aimon-s-hallucination.ipynb` | Baseline hallucination classification model |
| `README.md` | Project documentation (this file) |

---

## 👥 Team Information

**Team:** HCMUS Foursight  
**Institution:** University of Information Technology (UIT), VNU-HCM  
**Challenge:** UIT Data Science Challenge 2025  
**Task:** Hallucination Classification (No / Intrinsic / Extrinsic)

---

## 🏁 Summary

Our final model achieved:
- 🥇 **F1 = 0.81** (Public Test)
- 🥈 **F1 = 0.80** (Private Test)

These results demonstrate that **DeBERTa-v3**, with **optimized fine-tuning**, **data augmentation**, and **early stopping**, provides **robust performance** for hallucination detection in LLM outputs.

---

## 🔗 References

- [Hugging Face Model — Nguyenhhh/vihallu_model_mdeberta_nli_hard30](https://huggingface.co/Nguyenhhh/vihallu_model_mdeberta_nli_hard30)  
- [Hugging Face Model — Nguyenhhh/vihallu_model_mdeberta_nli_hard01](https://huggingface.co/Nguyenhhh/vihallu_model_mdeberta_nli_hard01)
- 
- [UIT Data Science Challenge 2025](https://github.com/nguyeudinhhaduong/UIT-Data-Science-Challenge-2025)

