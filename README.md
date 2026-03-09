# rtl-sdr-signal-classification
Signal Classification Of RTL-SDR Acquired Data Using Machine Learning and Deep Learning
# Signal Classification of RTL-SDR Acquired Data using Machine Learning and Deep Learning

## Overview
This project presents an end-to-end system for **automatic radio signal classification** using data captured from a **Software Defined Radio (RTL-SDR)** receiver.  

The system captures real-world radio signals and classifies them into different categories using **Machine Learning and Deep Learning models**.

The three signal types used in this project are:

- AM Broadcast Radio
- FM Broadcast Radio
- VHF Airband Voice

The project demonstrates how **signal processing, feature engineering, and machine learning** can be combined to build an intelligent spectrum sensing system. 

---

## Project Workflow

### 1. Signal Capture
Radio signals were captured using **RTL-SDR hardware** and **GNU Radio flowgraphs**.

Three receiver pipelines were implemented:

- AM Broadcast receiver
- FM Broadcast receiver
- Airband receiver

Captured IQ samples were stored for dataset generation.

---

### 2. Dataset Preparation

Each captured signal was converted into **CSV files containing features**.

Dataset distribution:

| Signal Type | Samples |
|--------------|--------|
| AM Broadcast | 274 |
| FM Broadcast | 270 |
| Airband Voice | 161 |
| **Total** | **705** |

Each sample contains:

- Raw IQ samples
- Time domain features
- Frequency domain features
- Statistical descriptors

Initial dataset size: 
705 samples × 17430 features


---

### 3. Data Preprocessing

The following preprocessing steps were applied:

- Missing value handling
- Feature scaling using **StandardScaler**
- Feature separation:
  - Raw IQ features
  - Statistical features

---

### 4. Dimensionality Reduction

Since the dataset contained thousands of features, **Principal Component Analysis (PCA)** was applied.
4096 raw IQ features → 136 PCA components


Variance retained: **95%**

Final dataset:
705 samples × 138 features


---

### 5. Machine Learning Models

Four models were trained and evaluated.

#### Logistic Regression
- Baseline classifier
- Linear decision boundary
- Fast training

Accuracy: **~82-83%**

---

#### Support Vector Machine (SVM)
- RBF kernel
- Non-linear decision boundaries

Accuracy: **~94%**

---

#### Multi-Layer Perceptron (MLP)
- Fully connected neural network
- ReLU activations
- Dropout and L2 regularization

Accuracy: **~96%**

---

#### 1D Convolutional Neural Network (CNN)

Architecture includes:

- Conv1D layers
- Batch Normalization
- MaxPooling
- Global Average Pooling
- Dense layers
- Dropout
- Gaussian noise augmentation

Accuracy: **~97-98%**

CNN achieved the **best performance** by learning spectral patterns directly from the signal features.

---

## Model Performance Comparison

| Model | Accuracy |
|------|---------|
| Logistic Regression | ~83% |
| SVM (RBF) | ~94% |
| MLP | ~96% |
| CNN | **~97-98%** |

---

## Technologies Used

### Hardware
- RTL-SDR Receiver
- V-Dipole Antenna

### Software
- GNU Radio
- Python
- Google Colab

### Libraries
- NumPy
- Pandas
- Scikit-learn
- TensorFlow / Keras
- SciPy
- Matplotlib
- Seaborn


---

## How to Run the Project

### 1. Install dependencies
pip install numpy pandas scikit-learn tensorflow scipy matplotlib seaborn librosa

---

### 2. Prepare Dataset

Place the dataset zip file in the working directory.

---

### 3. Run preprocessing and training
python Python_Code.py

This will:

- Extract dataset
- Preprocess features
- Apply PCA
- Train models
- Evaluate results

---

## Results

The CNN model demonstrated the **highest classification accuracy** by learning spectral features automatically.

The system proves that **low-cost SDR hardware combined with machine learning can effectively classify real radio signals**.

---

## Future Work

Future improvements may include:

- Classification of additional signals (ADS-B, LTE, WiFi)
- Real-time signal classification
- End-to-end deep learning using raw IQ samples
- Deployment on embedded SDR platforms (Jetson / Raspberry Pi)
- Robust models for noisy RF environments

---

## References

Key references used in this project include:

- Chen et al. – SigNet Deep Learning Framework for Radio Signals
- Scholl – Deep Learning for HF Signal Classification
- Swinney – ML for Discrete Frequency Signal Classification
- Xiong et al. – LinksIQ Modulation Recognition

---

## License

This project is for academic and educational purposes.
