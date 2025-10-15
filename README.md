
# 🧬 Machine Learning Models for Biological Data Analysis

Welcome to a showcase of **cutting-edge machine learning** applied to real-world biological and medical problems! This repository features five interactive Jupyter notebooks, each a self-contained pipeline for tackling a unique challenge in genomics, clinical prediction, or cancer research.

---

## 🚀 Project Portfolio

### 1️⃣ Leukemia Classification ([notebook](leukemia_classification.ipynb))
**Can we distinguish between two deadly blood cancers using only gene expression?**

- **Goal:** Predict Acute Lymphoblastic Leukemia (ALL) vs Acute Myeloid Leukemia (AML)
- **Data:** Thousands of gene features per patient
- **Techniques:** Feature selection, logistic regression, cross-validation
- **Impact:** Early diagnosis, personalized treatment, biomarker discovery

### 2️⃣ Asthma Prediction ([notebook](asthma_prediction.ipynb))
**Who is at risk for asthma? Can we predict it before symptoms appear?**

- **Goal:** Predict asthma diagnosis from demographics, environment, and clinical tests
- **Data:** Synthetic patient records with 17 features
- **Techniques:** Data scaling, logistic regression, metrics visualization
- **Impact:** Preventive care, risk stratification, public health insights

### 3️⃣ DNA Sequence Classification ([notebook](dna_classification.ipynb))
**What secrets are hidden in raw DNA? Can ML classify species and disease risk?**

- **Goal:** Classify DNA as Bacteria, Virus, Human, or Plant; predict disease risk level
- **Data:** Thousands of DNA sequences, annotated
- **Techniques:** k-mer analysis, random forest, multi-class ROC/PR curves
- **Impact:** Genomic medicine, pathogen detection, personalized health

### 4️⃣ Brain Tumor Classification ([notebook](brain_tumor_classification.ipynb))
**Can we decode brain tumor types from gene expression?**

- **Goal:** Multi-class prediction of tumor type (5 classes)
- **Data:** Gene expression profiles from patient samples
- **Techniques:** Random forest, label encoding, multi-class evaluation
- **Impact:** Precision oncology, treatment planning, research

### 5️⃣ Breast Cancer Histological Type ([notebook](histological_type_model.ipynb))
**Can ML distinguish subtle differences in breast cancer subtypes?**

- **Goal:** Classify ductal vs lobular carcinoma from gene expression
- **Data:** High-dimensional breast cancer datasets
- **Techniques:** PCA, SMOTE for class imbalance, pipeline modeling
- **Impact:** Improved diagnosis, targeted therapies, clinical decision support

---

## ✨ Features & Innovations

- **End-to-end ML pipelines:** Data cleaning, feature engineering, model selection, evaluation
- **Stunning 3×3 grid visualizations:** Confusion matrices, ROC curves, precision-recall curves, and metric comparisons for both train and test sets
- **Advanced techniques:** GridSearchCV, SMOTE, PCA, feature selection, label encoding
- **Clear, step-by-step documentation:** Each notebook guides you from raw data to actionable insights

---

## 🛠️ Getting Started

1. **Clone the repository:**
   ```bash
   git clone https://github.com/alenissacsam/Machine-Learning-Models_Biology.git
   cd Machine-Learning-Models_Biology
   ```
2. **Install dependencies:**
   ```bash
   pip install numpy pandas scikit-learn matplotlib seaborn imbalanced-learn joblib
   ```
3. **Open any notebook in Jupyter and run cells sequentially from top to bottom.**

---

## 📁 Repository Structure

```
Machine-Learning-Models_Biology/
│
├── leukemia_classification.ipynb
├── asthma_prediction.ipynb
├── dna_classification.ipynb
├── brain_tumor_classification.ipynb
├── histological_type_model.ipynb
├── README.md
└── .git/
```

---

## 📊 Visualization Example

Each notebook ends with a **3×3 grid of performance plots**:

- 🔵 Train vs 🟢 Test confusion matrices
- 📈 ROC curves (train/test/combined)
- 📉 Precision-Recall curves (train/test/combined)
- 🏆 Metrics bar chart (accuracy, precision, recall, F1)

This makes it easy to spot overfitting, compare models, and understand strengths/weaknesses at a glance!

---

## 📜 License
MIT

## 👤 Author
**Alenis Sacsam**

---
**Questions or collaboration? Open an issue on GitHub!**
