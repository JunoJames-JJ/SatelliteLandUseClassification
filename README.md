<div align="center">

# Satellite Land Use Classification
### CNN, ResNet-18 Transfer Learning, Grad-CAM & AI-Assisted Interpretation

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat-square&logo=pytorch&logoColor=white)
![Gradio](https://img.shields.io/badge/Gradio-FF7C00?style=flat-square&logo=gradio&logoColor=white)
![Gemini](https://img.shields.io/badge/Gemini%20API-4285F4?style=flat-square&logo=googlegemini&logoColor=white)
![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=flat-square)

</div>

---

## 🎯 Objective

Automatically classify land use types (forests, rivers, highways, residential areas, and more) from satellite images using deep learning - and go a step further by making the model's decisions genuinely understandable, combining visual explanation (Grad-CAM) with AI-generated natural language explanation (Gemini).

## 📂 Dataset

**EuroSAT** - ~27,000 satellite images captured by the Sentinel-2 satellite, across **10 land use categories**: Annual Crop, Forest, Herbaceous Vegetation, Highway, Industrial, Pasture, Permanent Crop, Residential, River, and Sea Lake. Each image is 64×64 pixels, balancing efficient training with enough visual detail for classification.

## ❓ Problem Statement

Satellite images contain valuable land use information, but manually analyzing large volumes of imagery is slow and doesn't scale. This project automates land use classification with deep learning - and adds explainability, so predictions aren't a black box.

---

## 🧪 Methodology

### 1. Data Preprocessing
- **Resizing:** all images standardized to 64×64 pixels
- **Normalization:** pixel values normalized using a predefined mean and standard deviation, stabilizing training

### 2. Baseline Model - SimpleCNN
A convolutional neural network built from scratch:
- **Convolutional layers** extract features like edges, textures, and shapes (roads, crops, buildings)
- **Pooling layers** reduce spatial size while keeping the most important features
- **Fully connected layers** combine extracted features into a final 10-class prediction

### 3. Advanced Model - ResNet-18 (Transfer Learning)
- Pre-trained on ImageNet, giving the model a head start on complex visual patterns
- Final fully connected layer adapted to output the 10 EuroSAT classes
- Images upscaled to 224×224 to match ResNet's expected input size

### 4. Explainability - Grad-CAM
Grad-CAM (Gradient-weighted Class Activation Mapping) highlights which regions of an image most influenced the model's prediction, generating a heatmap (red = high importance, blue = low importance) - confirming the model focuses on meaningful land features, not background noise.

### 5. AI-Assisted Interpretation - Gemini API
Beyond the heatmap, the **Gemini API** turns each prediction into a plain-language explanation - given a predicted class and confidence score, it generates a short, human-readable explanation of the result, making the model's output accessible to non-technical users.

### 6. Interactive Interface - Gradio
A full **Gradio web app** ties everything together: upload a satellite image and get back the predicted class, confidence score, Grad-CAM heatmap, and an AI-generated explanation - all in one interface.

---

## 📊 Results

| Model | Test Accuracy |
|---|---|
| SimpleCNN (baseline) | 90.81% |
| **ResNet-18 (transfer learning)** | **94.12%** |

The ResNet-18 model outperformed the CNN baseline, and its confusion matrix showed a much stronger diagonal - more accurate predictions across nearly all classes, with especially strong performance on visually distinct categories like Sea Lake and Residential. This demonstrates the real advantage transfer learning offers over training a smaller model from scratch, even on a relatively small 64×64 image dataset.

---

## 🛠️ Tech Stack

- **PyTorch** / **torchvision** - model architecture and training
- **ResNet-18** (pre-trained, ImageNet weights) - transfer learning backbone
- **Grad-CAM** - visual model explainability
- **Google Gemini API** - natural language explanation generation
- **Gradio** - interactive web interface
- **scikit-learn** - evaluation metrics (classification report, confusion matrix)

## 🚀 How to Run

Open [`Pytorch_Capstone_Final_Version.ipynb`](Pytorch_Capstone_Final_Version.ipynb) in Google Colab (GPU runtime recommended), and run the cells in order. You'll need:
- A **Kaggle API key** (for downloading the EuroSAT dataset)
- A **Gemini API key** (for the AI-generated explanations)

The final cells launch the Gradio interface, giving you a live, shareable link to try the model interactively.
