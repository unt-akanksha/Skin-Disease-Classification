# Skin Disease Classification

An image-classification project comparing a convolutional neural network trained from scratch with a fine-tuned ResNet50. The models classify images into five skin-condition categories. This repository contains the final end-to-end notebook, saved visualizations, and project documentation.

**Course project:** ADTA 5550, Deep Learning with Big Data
**Team:** Akanksha Tiwari

---

## Problem Statement

This project evaluates whether convolutional models can distinguish five skin-condition classes from images. It is an academic experiment, not a clinical screening or diagnostic tool.

---

## Dataset

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

The dataset is class-imbalanced. The notebook applies data augmentation during training. Dataset images are not included in this repository; see [`data/README.md`](data/README.md) for download and folder setup instructions.

## Models

- **Baseline CNN:** Three convolutional blocks trained from scratch, followed by a dense classification head.
- **ResNet50:** ImageNet-pretrained backbone with a custom classification head; the top 50 backbone layers were fine-tuned.

Both models use 224 × 224 RGB inputs and predict the same five classes.

---

## Results

| Model | Validation accuracy | Validation loss | Epochs |
|-------|--------------------:|---------------:|-------:|
| Baseline CNN | 92.30% | 0.2350 | 20 |
| ResNet50 (fine-tuned) | 57.13% | 1.0837 | 13 |

Metrics are from the notebook's saved model-comparison output on the 20% validation split. The baseline CNN outperformed fine-tuned ResNet50 by 35.17 percentage points on this split. These validation results do not establish performance on external data or clinical use; see the notebook for class-level errors, limitations, and future work. Training curves and sample images are available in [`results/`](results/).

---

## Repository Structure

```
Skin-Disease-Classification/
├── data/                  # Dataset (not tracked by git — see data/README.md)
├── notebooks/
│   └── Skin_Disease_Classification.ipynb  # Final end-to-end analysis and modeling
├── models/                # Generated model weights (not tracked)
├── results/               # Training curves and sample images
└── README.md
```

---

## Run the Notebook

**1. Clone the repo:**
```bash
git clone https://github.com/unt-akanksha/Skin-Disease-Classification.git
cd Skin-Disease-Classification
```

**2. Install the notebook dependencies** (Python, TensorFlow/Keras, NumPy, Pandas, Matplotlib, Seaborn, and scikit-learn):
```bash
pip install tensorflow numpy pandas matplotlib seaborn scikit-learn
```

**3. Download the dataset:**
See [`data/README.md`](data/README.md) for instructions.

**4. Open and run** [`notebooks/Skin_Disease_Classification.ipynb`](notebooks/Skin_Disease_Classification.ipynb) from top to bottom. Configure the dataset path as described in the notebook before running the data-loading cells. Training may require a GPU and can take substantial time.

---

## Tech Stack

Python, TensorFlow/Keras, NumPy, Pandas, Matplotlib, Seaborn, scikit-learn, and Jupyter Notebook.

---

## License

MIT License — see [LICENSE](LICENSE) for details.

> **Disclaimer:** This project is for academic purposes only and is not intended for clinical use.
