# 🧠 COVID-19 CT Scan Classification using Deep Learning

## 📘 Project Overview

This project explores the use of deep learning models to classify CT scan slices of human lungs into three diagnostic categories:

- **COVID-19 Positive**
- **Common Pneumonia**
- **Normal (Healthy)**

The primary goal is to build an AI-driven solution that supports rapid, accurate, and scalable diagnosis of COVID-19 using CT imaging, which is often faster and more sensitive than traditional RT-PCR testing.

---

## 📌 Problem Statement

CT imaging plays a critical role in early detection of COVID-19, especially in cases where RT-PCR may fail or delay diagnosis. However, manual analysis of CT slices is time-consuming and subjective.

This project asks:  
**Can deep learning models be used to accurately classify CT scan slices into COVID-19, pneumonia, or normal classes to support rapid diagnosis?**

---

## 🎯 Motivation

- RT-PCR tests are time-consuming and may give false negatives.
- CT imaging provides detailed information but requires expert radiologists.
- Deep learning, especially CNNs, can automate CT analysis for speed and consistency.
- This helps healthcare systems scale faster diagnosis with limited resources.

---

## 📂 Dataset Information

### 🔗 Source
- **Dataset**: [Large COVID-19 CT Slice Dataset – Kaggle](https://www.kaggle.com/datasets)
- **Content**: CT scan slices labeled as COVID-19, pneumonia, or normal
- **Total Images Used**: ~17,000 (80% training, 20% validation)

### 🧾 Features
| Feature                 | Value                            |
|-------------------------|----------------------------------|
| Number of Classes       | 3 (COVID-19, Pneumonia, Normal) |
| Image Format            | JPEG / PNG                      |
| Preprocessed Image Size | 160x160 pixels                  |
| Color Space             | RGB                             |
| Normalization           | Scaled to [0, 1]                |

---

## 🛠️ Data Preprocessing

- **Resized** all images to `160x160`
- **Converted** BGR → RGB
- **Normalized** pixel values from `[0–255]` to `[0–1]`
- **Saved** images with preserved class-wise structure

These steps ensure consistent input for CNN architectures.

---

## 🧠 Models Used

The following deep learning models were evaluated:

| Model           | Description                                  |
|------------------|----------------------------------------------|
| **VGG16**         | Simple CNN with 3x3 conv layers              |
| **VGG19**         | Deeper version of VGG16 (best performer)     |
| **ResNet50**      | Residual learning to handle vanishing grads  |
| **DenseNet121**   | Dense connections for feature reuse          |
| **EfficientNetB0**| Lightweight, balanced scaling                |
| **EfficientNetB3**| Larger variant of B0 with improved accuracy  |
| **InceptionV3**   | Multi-scale feature extraction               |
| **Xception**      | Depthwise separable convolutions             |
| **MobileNetV2**   | Optimized for mobile devices and efficiency  |
| **NASNetMobile**  | Auto-optimized for speed and size            |

---

## 📈 Results Summary

### 🔬 Validation Accuracy (from model training):

| Model           | Accuracy (%) | Notes                          |
|------------------|--------------|--------------------------------|
| **VGG19**         | **81.54%**     | Best performing model         |
| Xception        | 72.97%       | Efficient and accurate         |
| InceptionV3     | 71.48%       | Multi-resolution learning      |
| DenseNet121     | 70.25%       | Excellent feature reuse        |
| ResNet50        | 69.17%       | Stable with deep layers        |
| NASNetMobile    | 69.00%       | Mobile-optimized               |
| MobileNetV2     | 66.60%       | Fast, mobile-friendly          |
| VGG16           | 66.25%       | Simple and effective baseline  |
| EfficientNetB3  | 47.88%       | Scaled-up but underperforming  |
| EfficientNetB0  | 44.40%       | Fastest, but lowest accuracy   |

### 📊 External Test Accuracy (from other studies):

| Model           | Accuracy (%) | Source                  |
|------------------|--------------|--------------------------|
| VGG-19           | 70.35        | Lou et al.              |
| VGG-16           | 68.12        | Perumal et al.          |
| InceptionV3      | 69.50        | Mahapatra et al.        |
| DenseNet121      | 67.20        | Ezzoddin et al.         |
| ResNet50         | 65.44        | Garg et al.             |
| EfficientNetB0   | 66.78        | Chetoui et al.          |
| Xception         | 67.98        | Hasani et al.           |
| MobileNetV2      | 61.10        | Nasiri et al.           |
| EfficientNetB3   | 68.05        | Derived from B0 variant |
| NASNetMobile     | 62.40        | Forum experiment        |

---

## 🧾 Conclusion

- **VGG19** was the most accurate model on this dataset, achieving **81.54%**.
- **Xception** and **InceptionV3** also showed strong performance.
- Lightweight models (EfficientNetB0, MobileNetV2) were faster but less accurate.
- These results show that **CNN-based models can effectively aid in fast, automated diagnosis of COVID-19** using CT images.
- With further tuning, these models can assist real-world medical workflows, improving speed, reliability, and reach of diagnostic services.

---

## 🚀 How to Use

### 📦 Prerequisites:
- Python 3.x
- TensorFlow / Keras
- OpenCV
- NumPy, Matplotlib

### 🛠️ Steps:
1. Clone the repo and download the dataset from Kaggle
2. Run the preprocessing script to resize and normalize images
3. Train the selected model(s) using the prepared dataset
4. Evaluate and compare performance across models

---

## 📚 References

- COVID CT Dataset – [Kaggle](https://www.kaggle.com/)
- Perumal et al., Lou et al., Mahapatra et al., and others (see Appendix)

---

## 💡 Future Work

- Apply data augmentation to enhance generalization
- Explore ensemble learning or attention mechanisms
- Deploy as a web app for real-time COVID-19 CT scan classification
