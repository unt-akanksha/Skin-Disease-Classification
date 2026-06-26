# 🩺 Skin Disease Classification using CNN

A deep learning project that classifies dermatoscopic images into 5 skin disease categories using a custom CNN and transfer learning with ResNet50.

> **Course Project — ADTA 5550 Section 400 - Deep Learning with Big Data (Summer 2026 8W1)**  
> **Team:** Tiwari, Akanksha · Amusa, Olaribigbe · Selvaraj, Kavinraaj
> **Deadline:** July 19, 2025

---

## 📌 Problem Statement

Skin diseases are often misdiagnosed in under-served regions due to a lack of specialist access. This project builds a CNN-based image classifier that can screen for 5 skin conditions from dermatoscopic images, framed as a **screening aid** (not a diagnostic tool).

---

## 📁 Dataset

**Source:** [Skin Disease Classification Dataset — Mendeley Data](https://data.mendeley.com/datasets/3hckgznc67/1)  
**DOI:** 10.17632/3hckgznc67.1  
**Published:** July 2024 · Self-collected from hospitals across multiple countries

| Class | Images |
|-------|--------|
| Acne | 1,148 |
| Vitiligo | 2,016 |
| Hyperpigmentation | 700 |
| Nail Psoriasis | 2,520 |
| SJS-TEN | 3,164 |
| **Total** | **9,548** |

⚠️ Dataset is **class-imbalanced** — addressed via data augmentation during training.

> The dataset is not included in this repo. See [`data/README.md`](data/README.md) for download instructions.

---

## 🧠 Model Architecture

### Part A — Baseline CNN (from scratch)
- 3 convolutional blocks (32 → 64 → 128 filters)
- BatchNormalization + MaxPooling + Dropout after each block
- Dense head: 256 units → 5-class softmax output
- Optimizer: Adam (lr=0.001)
- Input size: 224×224×3

### Part B — Transfer Learning (ResNet50)
- Base: ResNet50 pretrained on ImageNet (175 layers)
- Phase 1: Frozen base, train classification head only
- Phase 2: Unfreeze top layers, fine-tune at lr=1e-5
- Custom head: GlobalAveragePooling → Dense(256) → Dropout(0.5) → Dense(5)

---

## 📊 Results

| Model | Val Accuracy | Val Loss |
|-------|-------------|----------|
| Baseline CNN | <!-- fill after training --> | <!-- fill --> |
| ResNet50 (Phase 1) | <!-- fill --> | <!-- fill --> |
| ResNet50 (Fine-tuned) | <!-- fill --> | <!-- fill --> |

> Training curves and confusion matrix available in [`results/`](results/)

---

## 📂 Project Structure

```
Skin-Disease-Classification/
├── data/                  # Dataset (not tracked by git — see data/README.md)
├── notebooks/
│   ├── 01_eda.ipynb           # Exploratory Data Analysis
│   ├── 02_preprocessing.ipynb # Data preprocessing pipeline
│   └── 03_model_training.ipynb# CNN + Transfer Learning
├── models/                # Saved model weights (not tracked by git)
├── results/               # Training curves, confusion matrix, metrics
├── utils/
│   └── config.py          # Shared config (image size, classes, etc.)
├── requirements.txt
└── README.md
```

---

## ▶️ How to Run

**1. Clone the repo:**
```bash
git clone https://github.com/unt-akanksha/Skin-Disease-Classification.git
cd Skin-Disease-Classification
```

**2. Install dependencies:**
```bash
pip install -r requirements.txt
```

**3. Download the dataset:**
See [`data/README.md`](data/README.md) for instructions.

**4. Run notebooks in order:**
```
01_eda.ipynb → 02_preprocessing.ipynb → 03_model_training.ipynb
```

---

## 🛠️ Tech Stack

![Python](https://img.shields.io/badge/Python-3.9-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.20-orange)
![Keras](https://img.shields.io/badge/Keras-3.x-red)

- Python 3.9
- TensorFlow / Keras
- NumPy, Pandas, Matplotlib, Seaborn
- Scikit-learn
- Jupyter Notebook

---

## 👥 Team

| Name | GitHub | Lane |
|------|--------|------|
| Akanksha Tiwari | [@unt-akanksha](https://github.com/unt-akanksha) | CNN Modeling |
| [Teammate 2] | [@username] | Data + EDA |
| [Teammate 3] | [@username] | Evaluation + Slides |

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

> **Disclaimer:** This project is for academic purposes only and is not intended for clinical use.
