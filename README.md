# Vision Transformer vs CNN for OCT Classification with Explainable AI

This repository contains a comparative study of **Vision Transformers (ViT)** and **Convolutional Neural Networks (CNN/ResNet baseline)** for medical image classification on the **OCT2017 dataset**.  
Both models are evaluated with **Explainable AI (XAI) techniques** such as SHAP, LIME, Grad-CAM, and attention visualization.

---

## Comparative Results

### Model Performance (Test Set)

| Model | Accuracy | Precision | Recall | F1 Score | ROC AUC |
|-------|----------|-----------|--------|----------|---------|
| **Vision Transformer (ViT)** | **94.80%** | **95.16%** | **94.80%** | **94.81%** | **≈0.985** |
| CNN (ResNet Baseline) | 85.00% | 88.00% | 85.00% | 84.58% | 0.9870 |
| **Improvement (ViT – CNN)** | **+9.80 pp** | **+7.16 pp** | **+9.80 pp** | **+10.23 pp** | – |

---

### Key Findings
- Vision Transformers outperform CNNs by **+9.80 percentage points in accuracy**.  
- ViT maintains **balanced performance across classes**, unlike CNNs which show variable recall.  
- **Self-attention** in ViT captures global dependencies, critical for subtle medical features.  
- Training: both models trained for 20 epochs (~11 hours each).

---

### CNN Detailed Results
- **Best Validation Accuracy:** 88.76% (Epoch 19)  
- **Per-class Performance (Test):**
  - CNV: Precision 0.73, Recall 0.99, F1 0.84  
  - DME: Precision 0.99, Recall 0.53, F1 0.69  
  - DRUSEN: Precision 0.99, Recall 0.90, F1 0.94  
  - NORMAL: Precision 0.83, Recall 1.00, F1 0.91  
- **Weighted F1 Score:** 0.8458  
- **Mean ROC AUC:** 0.9870  

---

### Vision Transformer Detailed Results
- **Test Accuracy:** 94.80%  
- **Macro F1 Score:** 0.9481  
- **Per-class Performance (Test):**
  - CNV: Precision 0.880, Recall 0.996, F1 0.934  
  - DME: Precision 0.987, Recall 0.924, F1 0.955  
  - DRUSEN: Precision 0.982, Recall 0.896, F1 0.937  
  - NORMAL: Precision 0.957, Recall 0.976, F1 0.966  
- **ROC AUC (macro):** ≈0.985  

---

## Comparative Analysis

### Executive Summary
Vision Transformers significantly outperformed CNNs in OCT classification, achieving **94.8% accuracy vs 85.0%**, with more consistent class-wise performance and better interpretability.

### Architectural Advantages
**ViT Strengths**
- Global receptive field from the first layer  
- Self-attention captures long-range dependencies  
- Better suited for subtle medical patterns  
- Consistent per-class performance  

**CNN Limitations**
- Limited receptive field in early layers  
- Struggles with global context  
- Highly variable recall (53%–100%)  
- Unreliable detection of certain pathologies (DME)  

### Clinical Implications
- **ViT Benefits**:  
  – Reliable detection across disease types  
  – Higher precision → fewer false positives  
  – Balanced recall → fewer missed diagnoses  
- **CNN Issues**:  
  – Poor recall for DME (53%) → unacceptable for deployment  
  – Inconsistent performance undermines trust in diagnosis  

### Explainability Comparison
- **ViT**: Attention maps highlight informative patches across the image.  
- **CNN**: Grad-CAM is useful but less consistent and less global.  

---

## Notebooks Overview

- **`notebooks/VIT_Medical_Image_XAI.ipynb`**  
  – ViT implementation achieving **94.80% accuracy**  
  – XAI: SHAP, LIME, Attention maps  
  – Full training + evaluation pipeline  

- **`notebooks/CNN_Medical_Image_Comparison.ipynb`**  
  – CNN/ResNet baseline with **85.0% accuracy**  
  – Grad-CAM visualization for interpretability  
  – Benchmark for ViT comparison  

---

## Repository Structure
