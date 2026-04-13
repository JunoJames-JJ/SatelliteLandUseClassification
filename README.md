# SatelliteLandUseClassification
Satellite Land Use Classification using CNN, Grad-CAM, and AI-Assisted  Interpretation - Deep Learning with Pytorch 

## OBJECTIVE: 

The goal of this project is to automatically classify different types of land use (such as forests, 
rivers, highways, and residential areas) from satellite images using deep learning techniques. 
The project also aims to provide visual and AI-based explanations to better understand how the 
model makes its predictions.  

## DATASET DESCRIPTION: 

The project uses the EuroSAT dataset, which contains approximately 27,000 satellite images 
captured by the Sentinel-2 satellite.  

The dataset is divided into 10 land use categories, including Annual Crop, Forest, Herbaceous 
Vegetation, Highway, Industrial, Pasture, Permanent Crop, Residential, River, and Sea Lake.  

Each image is 64×64 pixels, enabling efficient model training while preserving the visual features 
needed for classification. 

## PROBLEM STATEMENT: 

Satellite images contain valuable information about land use, but manually analyzing large 
amounts of data is time-consuming and inefficient. This project aims to automate land use 
classification using deep learning, making the process faster and more scalable. 

## METHODOLOGY

### A. Data Preprocessing

Before training, the raw satellite images were prepared to ensure consistency and improve the model performance:

- **Resizing:** Every satellite image was resized to 64x64 pixels. This ensures the model receives data in a consistent shape.  
- **Normalization:** Pixel values were normalized using a predefined mean and standard deviation. This helps stabilize training and prevents any single color channel from dominating the learning process.  

### B. Model Architecture (SimpleCNN)

Designed a Convolutional Neural Network (CNN), which is the standard for image recognition.

- **Convolutional Layers:** These layers extract important features such as edges, textures, and shapes. Example: roads, crops, buildings.  
- **Pooling Layers:** These layers reduce the spatial size of the feature maps, keeping only the most important features and making the model more efficient.  
- **Fully Connected Layers:** These layers combine the extracted features and produce the final classification output across the 10 land use categories.  

### C. Explainability with Grad-CAM

To improve interpretability, Grad-CAM (Gradient-weighted Class Activation Mapping) was used.

Grad-CAM analyzes the final convolutional layer and highlights the regions of the image that contributed most to the model’s prediction.

It generates a heatmap, where:

- Red regions indicate high importance  
- Blue regions indicate low importance  

This helps verify that the model is focusing on meaningful land features rather than irrelevant background areas.

### D. AI-Assisted Interpretation

To make the model outputs more understandable, the Gemini API was integrated.

The model generates a predicted class (e.g., forests) along with a confidence score (e.g., 95%). The AI system then converts this information into a natural language explanation.

This allows users, including non-technical audiences, to easily understand the model’s decision-making process.
