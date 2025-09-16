# Alzheimer’s Disease Progression Prediction

## Overview
This project aims to predict the progression of Alzheimer’s disease using MRI and clinical data from the **National Alzheimer’s Coordinating Center (NACC)**. The dataset includes MRI scan quality, brain morphometry, and patient demographic and clinical information. The goal is to develop a predictive model that can assist in early diagnosis and support personalized treatment strategies.

## Data Preprocessing
Each table underwent thorough preprocessing:
- **MRIQC table**: filtered for quality scans, standardized date/time, and merged with morphometry data.
- **MRISBM table**: removed irrelevant columns, standardized dates, and merged with patient data.
- **Patient table**: selected relevant demographic and clinical features, removed duplicates, and handled missing values.

Additional preprocessing steps included:
- One-Hot encoding of categorical variables.
- Standardization of numerical features.
- PCA applied to reduce dimensionality and extract principal components.
- Visualization of missing values, correlations, and distributions using plots and heatmaps.
- Imputation of missing values with median, mode, or zeros where appropriate.
- Removal of uninformative columns (single unique value or redundant data).

## Modeling
- A **PyTorch LSTM model** was trained on patient time series data to predict `NACCALZD`.
- Data was split into **train and test sets by patients** to ensure independence.
- Model performance was tracked per epoch using **Loss** and **Accuracy** on both train and test sets.
- The best epoch was identified around **epoch 5–6**, where test loss was lowest and test accuracy highest.

## Feature Importance
- **PCA components** and original features were analyzed using **SHAP**.
- For predicting Alzheimer’s (`target = 1`), the **first PCA component** was the most important.
- Key contributing features included specific brain volumetric measures, highlighting the most relevant biomarkers associated with Alzheimer’s progression.

## Results
- The LSTM model successfully captured temporal patterns in patient data.
- F1 scores and confusion matrices confirmed strong performance for high-risk patients.
- Visualizations of loss, accuracy, and feature contributions support model interpretability and provide insights into early detection.

## Conclusion
The combination of PCA-processed features from MRI and clinical data with a temporal LSTM model allows effective prediction of Alzheimer’s progression. This approach highlights critical brain regions and clinical indicators, supporting early intervention and personalized care strategies.

