# 🚑 AI Emergency Service Assistant  

A machine learning–based project that predicts **KTAS (Korean Triage and Acuity Scale)** levels to assist in emergency triage. By using patient vitals and chief complaints, this tool aims to reduce **mistriage** and support **understaffed ER/trauma centers** with a fast, consistent triage assistant.

![Four Models](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/models.png?raw=true)


## Table of Contents  
- [Background & Motivation](#background--motivation)  
- [What is KTAS?](#what-is-ktas)  
- [Dataset](#dataset)  
  - [General Information](#general-information)  
  - [Data Visualization](#data-visualization)  
- [Methods](#methods)  
  - [Data Cleaning](#data-cleaning)  
  - [Preprocessing](#preprocessing)  
  - [Models Tested](#models-tested)  
- [Results](#results)  
  - [Model Accuracy Comparison](#model-accuracy-comparison)  
  - [Testing with sample data](#testing-with-sample-data)  
  - [Confusion Matrix](#confusion-matrix)  
  - [Summary](#summary)  
- [Conclusion & Future Work](#conclusion--future-work)  


## Background & Motivation
Emergency rooms in South Korea face **understaffing and overcrowding**, leading to delayed or inaccurate triage. Similar (but less severe) problems exist in the US.  
This project introduces an **AI triage assistant** that:
- Uses **machine learning** to predict KTAS scores.  
- Acts as a **cross-checker** for human triage decisions.  
- Improves **speed, accuracy, and consistency** in ER patient care. 


## What is KTAS?
- **KTAS (Korean Triage and Acuity Scale)**: Ranks patients on a **1–5 scale**  
  - 1 = Highest Priority (Critical Emergency)  
  - 5 = Lowest Priority (Non-emergency)  

- Our model simplifies the output:  
    - **Emergency** → KTAS 1–2  
    - **Non-Emergency** → KTAS 3–5  


## Dataset

### General Information
- **Source**: [Emergency Service Triage Application (Kaggle)](https://www.kaggle.com/datasets/ilkeryildiz/emergency-service-triage-application/data)  
- **Size**: 1,267 patient records (2016–2017, Korea ER study)  
- **Variables**: 24 (chief complaints, vitals, clinical outcomes)  
- **Ground Truth**: KTAS scores assigned by 3 expert triage specialists  
- **Reference**: Moon SH, Shim JL, Park KS, Park CS (2019). *Triage accuracy and causes of mistriage using the Korean Triage and Acuity Scale*. PLOS ONE 14(9): e0216972.  

![Dataset](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/dataset.png?raw=true)

### Data Visualization
![Data Visualization 1](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/visualization-1.png?raw=true)\
![Data Visualization 2](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/visualization-2.png?raw=true)

## Methods

### Data Cleaning
- Removed duplicates, outliers, and missing core vitals (BP, HR, RR, Temp).  
- Imputed missing O₂ saturation with average.  

### Preprocessing
- **Standard Scaler** → Normalize numerical values.  
- **One-Hot Encoder** → Encode categorical values, handle missing entries.  
- Included **NRS pain** & **chief complaint** for improved accuracy.  

### Models Tested
1. Logistic Regression  
2. K-Nearest Neighbors  
3. Decision Tree  
4. Random Forest  


## Results

### Model Accuracy Comparison
![Four Models](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/models.png?raw=true) 

### Testing with sample data
![Sample Data Testing](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/output.png?raw=true)

### Confusion Matrix
![Confusion Matrix 1](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/cm-1.png?raw=true)\
![Confusion Matrix 2](https://github.com/yerin16/ai-diagnosis-assistant/blob/main/images/cm-2.png?raw=true)

### Summary
- **Best Model**: Logistic Regression → **68.3% accuracy**  
- **Key Insights**:  
  - KTAS 2 ↔ 3 and KTAS 4 ↔ 3 misclassifications were frequent.  
  - KTAS 5 often confused with 3/4.  
  - More training data for KTAS 1 and 5 is needed.  
- **Output**
    - Predicts **KTAS Level (1–5)**  
    - Labels **Emergency (1–2)** or **Non-Emergency (3–5)**  


## Conclusion & Future Work
- Logistic Regression is promising but limited by **imbalanced data**.  
- Future improvements:  
  - Expand dataset, especially for rare KTAS 1 & 5 cases.  
  - Improve **natural language processing** of chief complaints.  
  - Collaborate with **medical experts** for better feature selection.  
