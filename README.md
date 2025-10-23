# Road Segmentation in Aerial Images

## Overview
This project focuses on the **automatic segmentation of roads** in high-resolution aerial imagery using a subset of the **Massachusetts Roads Dataset**.  
The objective is to develop a computational method capable of identifying road pixels and separating them from their surroundings, even under challenging conditions such as shadows, vegetation, and variable lighting.

---

## Problem Statement
Road detection in aerial or satellite imagery is a fundamental task in computer vision, with applications in **urban planning**, **geographic information systems (GIS)**, and **autonomous navigation**.  
However, it poses several challenges:

- Roads occupy a small fraction of the total image area (**class imbalance**).  
- Their appearance changes with lighting, material, and shadow conditions.  
- Non-road elements like rooftops or rivers can have **similar colors or textures**.

The goal is to automatically segment **road networks** by combining color-based and texture-based features with **machine learning models**.

---

## Methodology

### 1. Data Preparation
- Images and ground-truth masks are loaded from the *Massachusetts Roads Dataset*.  
- Each image is resized and normalized for consistency.  
- Training, validation, and test splits are defined to ensure proper evaluation.

### 2. Feature Extraction
Several features are derived from multiple **color spaces**:

| Color Space | Channels Used | Purpose |
|--------------|----------------|----------|
| RGB | R, G, B | Basic intensity and color composition |
| HSV | H, S | Color and brightness invariance |
| Lab | b | Lightness and chromatic separation |

Additional features include:
- **Binary and adaptive thresholds** for intensity variations  
- **Gradient magnitude on the H channel** to detect road edges and boundaries

### 3. Model Training
Two supervised models were trained and compared:

| Model | Description | Advantage |
|--------|--------------|------------|
| Neural Network | Learns complex non-linear relationships between features | Captures subtle texture differences |
| Random Forest | Ensemble of decision trees | Robust, interpretable, and efficient |

To address **class imbalance**, road and background pixels were sampled in balanced proportions during training.

### 4. Evaluation
The dataset was split into **train**, **validation**, and **test** subsets to avoid overlap and ensure unbiased evaluation.  
Performance was measured using multiple metrics:

| Metric | Purpose |
|--------:|----------|
| **F1-score** | Main evaluation metric for class balance |
| **Accuracy** | Overall performance |
| **Precision / Recall** | Trade-off between false positives and false negatives |

---

## Results
The trained models successfully segmented roads and achieved a balanced trade-off between precision and recall.  
- The **Random Forest** model provided stable and interpretable results.  
- The **Neural Network** captured more complex spatial patterns but required higher computational cost.

| Model | F1-score | Accuracy | Remarks |
|--------|-----------|-----------|----------|
| Random Forest | High | High | Reliable and efficient |
| Neural Network | Slightly higher | Similar | Better on complex edges |

Visualization examples confirm the detection of both main roads and small connecting paths.

---

## Technologies Used
- **Language:** Python  
- **Frameworks/Libraries:** NumPy, OpenCV, scikit-learn, Matplotlib, Seaborn  
- **Dataset:** Massachusetts Roads Dataset

---

## Folder Structure
```
├── data/
│   ├── images/                  # Input aerial images
│   ├── masks/                   # Ground-truth road masks
│   └── processed/               # Preprocessed/normalized data
├── notebooks/
│   └── parte1_Enrique_Pardo_Garcia.ipynb
├── src/
│   ├── feature_extraction.py    # RGB, HSV, Lab feature generation
│   ├── model_training.py        # Random Forest and NN classifiers
│   └── evaluation.py            # Metric calculation (F1, accuracy, etc.)
├── results/
│   ├── visualizations/          # Predicted mask samples and performance plots
│   └── metrics.csv              # Summary of evaluation results
└── README.md
```

---

## Execution Guide
1. Clone the repository:
   ```bash
   git clone https://github.com/EnriquePardoGarcia/computer-vision-projects.git
   cd computer-vision-projects/road-segmentation
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Run the notebook:
   ```bash
   jupyter notebook parte1_Enrique_Pardo_Garcia.ipynb
   ```

4. Inside the notebook:
   - Load and preprocess the dataset  
   - Extract RGB, HSV, and Lab features  
   - Train and evaluate Random Forest / Neural Network models  
   - Visualize segmentation masks and metrics

---

## Results Visualization
Example visualizations included in the notebook:

| Example | Description |
|----------|--------------|
| Input Image | Original aerial image |
| Ground Truth | Manually labeled road mask |
| Predicted Mask | Model output after segmentation |
| Overlay | Prediction overlaid on the input image |

---

## Conclusion
This project demonstrates an **effective feature-engineered approach** to segmenting roads in aerial imagery using traditional **machine learning** techniques.  
It shows that combining **multi-space color features** with robust models (like Random Forests) yields reliable segmentation even under variable conditions.  
The approach can be extended to **urban analysis**, **infrastructure mapping**, or **autonomous vehicle perception** systems.

---

## Author
Developed by **Enrique Pardo García**  
*Data Science and Engineering student – University of A Coruña*
