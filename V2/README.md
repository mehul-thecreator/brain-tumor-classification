# Brain Tumor Classification using MobileNetV2

A deep learning project that classifies brain MRI images into four categories using Transfer Learning with MobileNetV2 and TensorFlow/Keras.

## Overview

This project uses a pretrained MobileNetV2 convolutional neural network (CNN) to classify brain MRI scans into four categories:

- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

The model uses transfer learning with ImageNet pretrained weights, followed by fine-tuning to improve classification performance.

## Dataset

**Brain Tumor MRI Dataset**

- Source: [Mendeley Data – Brain Tumor MRI Dataset](https://data.mendeley.com/datasets/zwr4ntf94j)
- Image size: 224 × 224 pixels
- Dataset splits: Training, Validation and Testing (depending on dataset version).
- Classes: 4

The notebook also includes an exact duplicate image check between training and testing datasets to identify potential data leakage.

## Technologies & Libraries

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- Google Colab
- PIL (Pillow)

## Model Architecture

The project uses **MobileNetV2**, pretrained on ImageNet, as its feature extraction backbone.

The classification architecture consists of:

1. MobileNetV2 (pretrained ImageNet weights).
2. Global Average Pooling 2D.
3. Dropout layer (0.3).
4. Dense output layer with Softmax activation.

## Data Preprocessing & Augmentation

MRI images are resized to 224 × 224 pixels.

The following data augmentation techniques are applied:

- Random Horizontal Flip
- Random Rotation
- Random Zoom
- Random Translation
- Random Contrast
- Random Brightness

These transformations help improve the model's ability to generalize to unseen images.

## Training Approach

Training is performed in two stages.

### 1. Transfer Learning

- Load MobileNetV2 with ImageNet pretrained weights.
- Freeze the pretrained base model.
- Train the classification head.
- Adam optimizer with a learning rate of 0.001.
- Early stopping based on validation loss.

### 2. Fine-Tuning

- Unfreeze the MobileNetV2 base model.
- Keep the first layers frozen.
- Fine-tune the last 40 layers.
- Reduce the learning rate to 0.00001.
- Continue training with early stopping.

## Model Evaluation

The model is evaluated using:

- Training Accuracy
- Validation Accuracy
- Testing Accuracy
- Classification Report
- Confusion Matrix

Training and validation accuracy/loss curves are also generated to visualize the learning process.

## Prediction

The notebook supports two prediction methods:

1. **Test Dataset Predictions:** Displays randomly selected test images alongside their actual and predicted classifications.
2. **Custom MRI Image Prediction:** Allows users to upload their own MRI images and view the predicted tumor category with confidence scores for all four classes.

## Model Export

The trained model is saved in Keras format:

`brain_tumor_model.keras`


## How to Run

1. Open the notebook in Google Colab.
2. Select a GPU runtime (T4 GPU recommended).
3. Download the dataset from Mendeley Data.
4. Upload the dataset ZIP file to Google Drive.
5. Update the `ZIP_PATH` variable in the notebook.
6. Execute the notebook cells sequentially.
7. Train and evaluate the model.
8. Upload custom MRI images to test predictions.

## Result
model failed to successfully identify tumour in unseen image provided despite training on different dataset.