

# 🪨📄✂️ Rock-Paper-Scissors Image Classification using CNN

A Convolutional Neural Network (CNN) based computer vision project for classifying hand gestures into three categories: **Paper, Rock, and Scissors**.

This project implements an end-to-end image classification pipeline including image preprocessing, data augmentation, label encoding, CNN-based feature extraction, model training, validation, and quantitative evaluation.

---

## 📌 Overview

Rock-Paper-Scissors is a three-class image classification problem where the model must identify the hand gesture represented in an input image.

The objective of this project is to build and evaluate a CNN capable of learning discriminative visual features from hand gesture images and correctly classifying unseen samples.

### Classes

| Label | Class |
|------:|-------|
| 0 | Paper |
| 1 | Rock |
| 2 | Scissors |

---

## ✨ Key Features

- Multi-class image classification using CNN
- Image resizing to a fixed input resolution
- Grayscale image processing
- Data augmentation to improve generalization
- Numerical label encoding
- Train/validation/test evaluation
- Class-wise precision, recall, and F1-score analysis
- Generalization gap analysis
- Evaluation on 657 previously unseen test images

---

## 🗂️ Dataset Structure

The dataset is organized according to class labels:

```text
dataset/
├── Paper/
│   ├── image_001.jpg
│   ├── image_002.jpg
│   └── ...
│
├── Rock/
│   ├── image_001.jpg
│   ├── image_002.jpg
│   └── ...
│
└── Scissors/
    ├── image_001.jpg
    ├── image_002.jpg
    └── ...
````

The folder names are used as the original class labels before numerical encoding.

---

## 📊 Dataset Split

After preprocessing and dataset preparation, the data was divided into training, validation, and testing sets.

| Split      |    Images |    Labels |
| ---------- | --------: | --------: |
| Training   |     3,063 |     3,063 |
| Validation |       656 |       656 |
| Testing    |       657 |       657 |
| **Total**  | **4,376** | **4,376** |

### Input Shape

```text
224 × 224 × 1
```

The model receives **224×224 grayscale images with one channel**.

---

## 🔄 Data Preprocessing

The image preprocessing pipeline consists of the following steps:

### 1. Image Loading

Images are loaded from their respective class directories and associated with the corresponding class label.

### 2. Data Augmentation

Data augmentation was applied to increase the diversity of training samples and improve model generalization.

The augmentation process introduces variations such as:

* Rotation
* Width and height shifting
* Zooming
* Horizontal flipping

The objective is to expose the model to realistic variations of hand gestures.

### 3. Image Resizing

All images are resized to:

```text
224 × 224
```

### 4. Grayscale Conversion

Images are converted to grayscale, resulting in a single-channel representation:

```text
224 × 224 × 1
```

### 5. Label Encoding

The categorical labels are converted into numerical values:

```text
Paper     → 0
Rock      → 1
Scissors  → 2
```

---

## 🧠 CNN Model

A Convolutional Neural Network is used to automatically learn spatial and visual features from the input images.

The general architecture follows:

```text
Input Image
    │
    ▼
224 × 224 × 1
    │
    ▼
Convolutional Layers
    │
    ▼
Pooling Layers
    │
    ▼
Deep Feature Extraction
    │
    ▼
Flatten
    │
    ▼
Fully Connected Layers
    │
    ▼
Output Layer
    │
    ▼
3 Classes
```

The final layer contains three output neurons corresponding to:

```text
Paper
Rock
Scissors
```

---

## 📈 Results

### Overall Performance

| Metric               |      Score |
| -------------------- | ---------: |
| Training Accuracy    | **98.86%** |
| Validation Accuracy  | **92.68%** |
| Test Accuracy        | **89.65%** |
| Test Loss            | **0.3027** |
| Train–Validation Gap |  **6.17%** |

The model achieved **89.65% accuracy on the unseen test set**.

---

## 📋 Classification Report

| Class            | Precision |   Recall | F1-Score | Support |
| ---------------- | --------: | -------: | -------: | ------: |
| Paper            |      0.94 |     0.93 |     0.94 |     214 |
| Rock             |      0.80 |     0.99 |     0.89 |     218 |
| Scissors         |      0.98 |     0.77 |     0.86 |     225 |
| **Accuracy**     |           |          | **0.90** | **657** |
| **Macro Avg**    |  **0.91** | **0.90** | **0.90** | **657** |
| **Weighted Avg** |  **0.91** | **0.90** | **0.90** | **657** |

---

## 🔍 Performance Analysis

### Paper

Paper achieved:

* Precision: **94%**
* Recall: **93%**
* F1-score: **94%**

This indicates strong and relatively balanced classification performance.

### Rock

Rock achieved:

* Precision: **80%**
* Recall: **99%**
* F1-score: **89%**

The very high recall indicates that the model identifies almost all actual Rock samples. However, the lower precision indicates that some samples from other classes are incorrectly predicted as Rock.

### Scissors

Scissors achieved:

* Precision: **98%**
* Recall: **77%**
* F1-score: **86%**

The model is highly reliable when it predicts Scissors, but its lower recall indicates that some actual Scissors samples are incorrectly classified as other classes.

---

## 📉 Generalization Analysis

The model achieved:

```text
Training Accuracy   : 98.86%
Validation Accuracy : 92.68%
Test Accuracy       : 89.65%
```

The training-validation gap is:

```text
98.86% - 92.68% = 6.17%
```

The difference between training and validation performance suggests **moderate overfitting**.

The decrease from validation accuracy to test accuracy also indicates that further improvements in generalization could be beneficial.

Potential improvements include:

* Stronger regularization
* Better augmentation strategies
* Hyperparameter tuning
* Transfer learning
* Increasing dataset diversity
* Improving class-specific representation

---

## 🧪 Evaluation

The final model was evaluated on:

```text
657 unseen test images
```

Final test performance:

```text
Test Accuracy : 89.65%
Test Loss     : 0.3027
```

The classification report provides additional insight into class-specific behavior through precision, recall, and F1-score.

---

## 🛠️ Tech Stack

| Technology             | Purpose                      |
| ---------------------- | ---------------------------- |
| Python                 | Programming language         |
| TensorFlow             | Deep learning framework      |
| Keras                  | CNN implementation           |
| NumPy                  | Numerical computation        |
| OpenCV                 | Image processing             |
| Matplotlib             | Visualization                |
| Scikit-learn           | Evaluation and preprocessing |
| Jupyter / Google Colab | Development environment      |

---

## 📁 Repository Structure

```text
Recognintionof_RockPaperScissors/
│
├── dataset/
│   └── README.md
│
├── notebooks/
│   └── rock-paper-scissors-classification.ipynb
│
├── models/
│   └── rock_paper_scissors_model.keras
│
├── results/
│   ├── accuracy.png
│   ├── loss.png
│   ├── confusion_matrix.png
│   └── sample_predictions.png
│
├── requirements.txt
├── README.md
└── .gitignore
```

> The actual dataset may be excluded from the repository if it is large or subject to redistribution restrictions.

---

## 🚀 Installation

### Clone the Repository

```bash
git clone [https://github.com/Shimantoshaha01/Recognintionof_RockPaperScissors.git](https://github.com/Shimantoshaha01/Recognintionof_RockPaperScissors)
cd Recognintionof_RockPaperScissors
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

Example `requirements.txt`:

```text
tensorflow
numpy
opencv-python
matplotlib
scikit-learn
```

---

## ▶️ Usage

### 1. Prepare the Dataset

Place the dataset according to the following structure:

```text
dataset/
├── Paper/
├── Rock/
└── Scissors/
```

### 2. Run the Notebook

Open:

```text
notebooks/rock-paper-scissors-classification.ipynb
```

Run the notebook sequentially to:

1. Load the dataset
2. Inspect the images
3. Apply preprocessing
4. Perform data augmentation
5. Resize the images
6. Normalize pixel values
7. Encode class labels
8. Train the CNN
9. Evaluate the model
10. Generate predictions

---

## 📌 Example Prediction

The trained model produces a probability distribution across the three classes.

Example:

```text
Paper     : 0.05
Rock      : 0.91
Scissors  : 0.04
```

The predicted class is:

```text
Rock
```

---

## 🎯 Project Objectives

* Build a CNN-based multi-class image classifier.
* Apply image preprocessing techniques for deep learning.
* Investigate the effect of data augmentation.
* Train a CNN for Rock-Paper-Scissors recognition.
* Evaluate the model using multiple classification metrics.
* Analyze model generalization and class-wise performance.

---

## ⚠️ Limitations

The current model achieves **89.65% test accuracy**, but its performance is not uniform across all classes.

In particular:

* Scissors recall is relatively low at **77%**.
* Rock precision is relatively low at **80%**.
* Training accuracy (**98.86%**) is considerably higher than validation accuracy (**92.68%**), indicating some overfitting.

Therefore, the current model should be considered a **research/learning implementation rather than a production-ready classifier**.

---

## 🔮 Future Improvements

Several approaches could potentially improve performance.

### Transfer Learning

Evaluate pretrained architectures such as:

* MobileNetV2
* EfficientNet
* ResNet
* MobileNet

### Better Regularization

Experiment with:

* Dropout
* L2 regularization
* Batch normalization
* Early stopping

### Hyperparameter Optimization

Tune:

* Learning rate
* Batch size
* Number of convolutional filters
* Kernel size
* Dropout rate
* Optimizer

### Dataset Improvements

* Increase dataset size
* Add more diverse backgrounds
* Include different lighting conditions
* Include different hand orientations
* Improve class balance

### Deployment

The trained model could be extended into:

* Real-time webcam classification
* Streamlit web application
* Flask API
* Mobile application

---

## 📊 Final Summary

| Metric              |            Result |
| ------------------- | ----------------: |
| Classes             |             **3** |
| Input Size          | **224 × 224 × 1** |
| Training Samples    |         **3,063** |
| Validation Samples  |           **656** |
| Test Samples        |           **657** |
| Training Accuracy   |        **98.86%** |
| Validation Accuracy |        **92.68%** |
| Test Accuracy       |        **89.65%** |
| Test Loss           |        **0.3027** |

### Final Result

> **The CNN achieved 89.65% test accuracy on 657 unseen Rock-Paper-Scissors images.**

The results demonstrate that a CNN can effectively learn visual representations of hand gestures, while the class-wise metrics indicate opportunities for improving generalization and reducing confusion between visually similar gestures.

---

## 👨‍💻 Author

**Shimanto Kumar Shaha**

Computer Science & Engineering
Chittagong University of Engineering & Technology (CUET)

---

## ⭐ Acknowledgements

This project was developed as a practical implementation of **Deep Learning and Computer Vision**, focusing on CNN-based multi-class image classification.

