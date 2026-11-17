# Brain Tumor Classification using Deep Learning

A deep learning project that classifies brain MRI images into four categories using **Transfer Learning with MobileNetV2** and TensorFlow/Keras.

## Overview

This project uses a pretrained MobileNetV2 model to classify brain MRI scans into the following four categories:

- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

The model uses transfer learning to leverage features learned from ImageNet and applies them to brain MRI image classification.

## Dataset

**Brain Tumor Classification (MRI)**

- Source: [Kaggle – Brain Tumor Classification (MRI)](https://www.kaggle.com/datasets/sartajbhuvaji/brain-tumor-classification-mri)
- Training images: Used for training and validation.
- Testing images: Reserved for final model evaluation.
- Image dimensions: 224 × 224 pixels.
- Number of classes: 4.

20% of the training dataset is allocated for validation.

## Technologies & Libraries

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- KaggleHub
- Google Colab

## Model Architecture

The project uses **MobileNetV2**, a pretrained convolutional neural network (CNN).

The architecture consists of:

1. MobileNetV2 pretrained on ImageNet.
2. Global Average Pooling 2D.
3. Dropout layer (0.3).
4. Dense output layer with Softmax activation.

### Training Approach

The model is trained in two stages:

**1. Feature Extraction**
- Load pretrained MobileNetV2 weights.
- Freeze the base model layers.
- Train the classification head.
- Adam optimizer with a learning rate of 0.001.

**2. Fine-Tuning**
- Unfreeze the last 40 layers of MobileNetV2.
- Train selected layers with a lower learning rate of 0.00001.
- Use early stopping to reduce overfitting.

### Data Augmentation

The following augmentation techniques are applied during training:

- Random Horizontal Flip
- Random Rotation
- Random Zoom

## Evaluation

The model is evaluated using:

- Training accuracy
- Validation accuracy
- Testing accuracy
- Classification Report
- Confusion Matrix

Training and validation accuracy/loss graphs are also generated to visualize model performance.

## Model Export

The trained model is saved in Keras format:

`brain_tumor_model.keras`

This allows the model to be reused for predictions or integrated into applications using TensorFlow/Keras.

## How to Run

1. Open the notebook in Google Colab.
2. Select a GPU runtime (T4 GPU recommended).
3. Run the notebook cells sequentially.
4. The dataset will be downloaded automatically using KaggleHub.
5. Train and evaluate the model.
6. Save the trained model.
7. Upload MRI images to test individual predictions.

## Result
model failed to successfully identify tumour in unseen image provided.