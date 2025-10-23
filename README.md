# Road-Segmentation
Project Overview

This project focuses on the automatic segmentation of roads in high-resolution aerial imagery using a subset of the Massachusetts Roads Dataset.
The objective is to develop a computational method capable of identifying road pixels and separating them from the surrounding environment, even under difficult conditions such as shadows, vegetation, or variable lighting.

Problem Statement

Detecting roads in aerial or satellite images is an essential problem in computer vision with applications in urban planning, geographic information systems, and autonomous navigation.
The task is challenging because:

Roads cover a small fraction of the total image area, creating class imbalance.

Their appearance changes due to lighting, surface material, and shadows.

Non-road elements (such as rooftops or rivers) may have similar color or texture.

The goal of this project is to automatically segment road networks by combining image features and machine learning models.

Methodology

Data Preparation
Images and corresponding ground truth masks are loaded from the Massachusetts Roads Dataset. Each image is resized and normalized to ensure consistent input.

Feature Extraction
Multiple features are derived from color spaces (RGB, HSV, and Lab).

Channels R, G, B, H, S, and b from Lab are included.

Binary and adaptive thresholds are applied to capture variations in tone and intensity.

Gradient magnitude on the H channel is used to detect road boundaries.

Model Training
Different machine learning models were tested, including:

A Neural Network, capable of learning non-linear patterns.

A Random Forest, providing robust performance and interpretability.
Class imbalance was addressed by balancing the number of samples for each class during training.

Evaluation
Data were divided into training, validation, and test sets to avoid overlap and ensure fair evaluation.
The main performance metric was the F1-score, complemented by accuracy and precision.

Results

The implemented models successfully identify roads and achieve a good balance between precision and recall.
The Random Forest model provided the most stable performance, while the neural network captured more complex relationships at the cost of higher computational requirements.

Conclusion

This project demonstrates an effective approach to road segmentation in aerial images through feature engineering and supervised learning.
The methodology can be extended to other image segmentation tasks or integrated into larger geographic information systems.
