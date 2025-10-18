
# Predicting Sepsis Through Proteomic Insights: Findings From a Prospective ICU Cohort

This repository contains the R scripts and analysis pipeline for identifying clinical variables that are highly predictable from proteomic profiles, and subsequently using these selected variables to accurately predict sepsis outcomes in both a Discovery and an independent Validation Cohort.


##  Methodology and Workflow

The analysis pipeline consists of three main stages, primarily utilizing **Random Forest (RF)** models.

### Stage 1: Proteomics-Driven Clinical Variable Prediction
*   **Goal:** To determine which clinical variables (both continuous and binary) can be reliably predicted from a core set of proteomic features.
*   **Model:** Random Forest Regression for continuous targets and Random Forest Classification for binary targets.
*   **Method:** Leave-One-Out Cross-Validation (LOOCV) repeated 10 times.

### Stage 2: Sepsis Prediction in Discovery Cohort
*   **Goal:** To test the ability of the best-performing clinical variables (along with key proteomic markers) to predict sepsis within the **Discovery Cohort** (`n=55`).
*   **Feature Set:** A combined set of clinical and proteomic markers is used as input.
*   **Method:** Repeated LOOCV (10 repeats) to estimate performance metrics (AUC, Accuracy, F1).

### Stage 3: Validation in Independent Cohort
*   **Goal:** To validate the final model's performance on an independent patient group (**Validation Cohort**, `n=60`).
*   **Model Training:** The final Random Forest model is trained on the entire Discovery Cohort.
*   **Validation:** The model is tested on the Validation Cohort, and the process (training and testing) is repeated **10 times** to assess the stability of the prediction metrics (AUC, Sensitivity, Specificity) and feature importance.
