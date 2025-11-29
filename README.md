# Stress-Aware Heart Health Modeling using Wearable Sensors (WESAD)

## Overview
This project presents a stress-aware cardiovascular modeling pipeline using multimodal physiological data collected from wearable sensors. Using the WESAD (Wearable Stress and Affect Detection) dataset, the study investigates how psychological stress influences cardiac dynamics by jointly modeling electrodermal activity (EDA) and blood volume pulse (BVP).

The primary goal is to extract biologically meaningful stress and heart-related features and use interpretable machine learning models to analyze stress–heart interactions.

---

## Key Contributions
- End-to-end preprocessing of physiological signals (EDA & BVP)
- Extraction of stress markers using Skin Conductance Responses (SCR)
- Heart rate (HR) and heart rate variability (HRV) feature extraction
- Window-based feature engineering for non-stationary signals
- Interpretable machine learning for stress-state classification
- Feature importance analysis with physiological interpretation
- Cross-subject evaluation to analyze real-world generalization

---

## Dataset
**WESAD – Wearable Stress and Affect Detection Dataset**

- Sensors: Empatica E4 (EDA, BVP, ACC, TEMP)
- Subjects: Multiple participants performing baseline, stress, and amusement tasks
- Sampling rates:
  - EDA: 4 Hz
  - BVP: 64 Hz

> **Note:** Raw WESAD data is not included in this repository due to dataset licensing restrictions.

---

## Methodology

### Signal Preprocessing
- **EDA:** Low-pass Butterworth filtering for noise removal
- **BVP:** Band-pass filtering to isolate cardiac frequency components
- Peak detection used for SCR and heartbeat identification
- Zero-phase filtering (`filtfilt`) to preserve temporal accuracy

### Feature Extraction
Signals are segmented into overlapping windows (60 seconds, 50% overlap).

Extracted features include:
- SCR count
- SCR amplitude
- Mean heart rate
- RMSSD (parasympathetic HRV metric)
- SDNN (overall HRV metric)

### Machine Learning
- Models: Random Forest, Support Vector Machine
- Task: Multiclass stress-state classification
  - Baseline
  - Stress
  - Amusement
- Evaluation:
  - Within-subject validation
  - Cross-subject (subject-independent) validation

---

## Results

### Within-Subject Performance
- Classification accuracy: **86.7%**
- High recall for stress class (important for healthcare applications)
- Feature importance aligned with known autonomic physiology

### Cross-Subject Evaluation
- Significant drop in performance observed due to inter-individual physiological variability
- Highlights the challenge of subject-independent modeling in wearable healthcare systems
- Reinforces the need for personalization or calibration strategies

---

## Key Insights
- Heart rate and SCR frequency are dominant indicators of stress
- HRV features provide complementary information about autonomic balance
- Wearable physiological signals are highly individual-specific
- Interpretability is crucial for healthcare-focused machine learning

---

## Project Structure

```text
stress-heart-ml-wesad/
│
├── notebooks/
│   ├── 01_eda_preprocessing.ipynb
│   ├── 02_bvp_hr_hrv_extraction.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_ml_within_subject.ipynb
│   └── 05_cross_subject_validation.ipynb
│
├── data/
│   └── processed/
│       └── stress_heart_ml_dataset.csv
│
├── results/
│   ├── figures/
│   └── tables/
│
├── README.md
└── requirements.txt

Reproducibility Note

This project was developed and experimented using Google Colab.
Notebooks are modularized to illustrate each stage of the pipeline clearly.
Due to data licensing constraints, raw WESAD files are not included, but all methodology and feature extraction steps are fully documented.

Future Work

Subject-wise normalization and calibration

Deep learning models (CNN–LSTM) for temporal modeling

Longitudinal cardiovascular risk analysis

Multi-subject domain adaptation techniques

Motivation

This project was developed as part of preparation for graduate studies in machine learning and healthcare, with a specific interest in wearable sensing, physiological signal processing, and stress-aware health systems.



## ✅ Final confirmation
With this README, your project is now:
- ✅ **GKS-ready**
- ✅ **Professor-readable**
- ✅ **Research-presentable**
- ✅ **No further edits required**

### 🔥 Next correct move:
Reply with **“Start Project 2”**  
and I’ll design your **second GKS project** just as strategically.

