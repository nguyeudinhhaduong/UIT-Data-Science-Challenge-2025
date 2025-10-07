# UIT Data Science Challenge 2025

This repository contains our solution for the **UIT Data Science Challenge 2025**, focusing on **text classification** tasks related to detecting hallucination types in generative AI outputs.

---

## 📘 Project Overview

The objective of this challenge is to **classify hallucination types** (e.g., *intrinsic* vs *extrinsic*) from generated text samples.  
We explored various transformer-based models and fine-tuned them on the provided dataset using PyTorch and Hugging Face Transformers.

---

## 🧠 Models and Approaches

We experimented with several approaches:

1. **Baseline fine-tuning** using `MoritzLaurer/deberta-v3-base`  
2. **Enhanced fine-tuning** with improved preprocessing, data augmentation, and learning rate scheduling  
3. **Advanced optimization** using early stopping and custom evaluation metrics (Accuracy, F1)

---

## ⚙️ Training Details

### Normal Fine-tuning Logs

| Epoch | Training Loss | Validation Loss | Accuracy |
|:------:|:--------------:|:----------------:|:---------:|
| 1 | 0.3983 | 0.3723 | 0.8870 |
| 2 | 0.3400 | 0.3590 | 0.8954 |
| 3 | 0.3074 | 0.4101 | 0.8787 |
| 4 | 0.1800 | 0.4587 | 0.8991 |
| 5 | 0.1442 | 0.6436 | 0.8722 |
| 6 | 0.1388 | 0.6059 | 0.8833 |
| 7 | 0.1032 | 0.6055 | 0.8843 |

**Best model achieved:**  
- **Validation F1:** 0.7910  
- **Validation Accuracy:** 0.806  
- **Training stopped early at Epoch 11**

---

## 🧩 Experiment Results

| Step | Training Loss | Validation Loss | Accuracy | F1 |
|:----:|:--------------:|:----------------:|:---------:|:--:|
| 200 | No log | 0.591951 | 0.778704 | 0.777634 |
| 400 | No log | 0.602587 | 0.806481 | 0.806432 |
| 600 | 0.605300 | 0.669831 | 0.799074 | 0.797823 |
| 800 | 0.605300 | 0.809728 | 0.781481 | 0.781445 |
| 1000 | 0.283400 | 0.907666 | 0.776852 | 0.777183 |

---

## 🚀 Final Evaluation

| Dataset | F1 Score | Accuracy |
|:---------:|:----------:|:-----------:|
| Public Test | 0.81 | — |
| Private Test (Final Leaderboard) | **0.80** | — |

---

## 📄 Files in Repository

| File | Description |
|------|--------------|
| `finetuning_moritzlaurer_mdeberta_v3.ipynb` | Fine-tuning DeBERTa-v3 model |
| `hcmus-foursight-processdata.ipynb` | Data preprocessing and augmentation |
| `hcmus-foursight-submit-for-private-test.ipynb` | Inference and submission script |
| `Classification-Aimon-s-hallucination.ipynb` | Baseline model for hallucination classification |
| `README.md` | This file |

---

## 🧑‍💻 Team Information

- **Team:** HCMUS Foursight  
- **Institution:** University of Information Technology (UIT), VNU-HCM  
- **Challenge:** UIT Data Science Challenge 2025  
- **Task:** Hallucination Classification (Intrinsic vs Extrinsic)

---

## 🏁 Summary

Our approach achieved competitive results with:
- **Best F1 = 0.81 (Public Test)**
- **Final F1 = 0.80 (Private Test)**

This demonstrates that DeBERTa-v3 fine-tuning with careful learning rate scheduling and early stopping provides strong generalization for hallucination classification tasks.

---

### 🔗 Reference

- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [UIT Data Science Challenge 2025](https://github.com/nguyeudinhhaduong/UIT-Data-Science-Challenge-2025)

