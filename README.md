# PCA-Based MNIST Digit Recognition

This project implements a **PCA (Principal Component Analysis)–based digit recognizer** on the MNIST dataset using a **reconstruction error–based classification** approach.

## Overview
Each digit class (0–9) is modeled using its own PCA subspace. A test image is classified by projecting it onto each class subspace, reconstructing it, and assigning the label with the **minimum reconstruction error**.

## Dataset
- **MNIST** (70,000 grayscale images)
- Image size: **28 × 28** (784 features)
- Classes: **10 digits (0–9)**

## Methodology
1. **Load Data**
   - Fetch MNIST using `fetch_openml`
   - Convert labels to integers

2. **Train-Test Split**
   - 70% training, 30% testing
   - Stratified to maintain class balance

3. **PCA Subspace Construction**
   - For each digit class:
     - Compute mean image
     - Center data
     - Apply PCA with `k` components

4. **Hyperparameter Tuning**
   - Tested `k = {10, 20, 50, 100, 150}`
   - Best performance achieved at **k = 20**

5. **Classification**
   - Project test image into each class PCA subspace
   - Reconstruct image
   - Compute L2 reconstruction error
   - Predict class with minimum error

6. **Evaluation**
   - Accuracy
   - Confusion Matrix
   - Precision, Recall, F1-score

## Results
- **Best Accuracy:** **95.44%**
- **Optimal PCA Components:** `k = 20`
- Strong and balanced performance across all digit classes

## Libraries Used
- `numpy`, `pandas`
- `scikit-learn`
- `matplotlib`, `seaborn`

## Key Insight
PCA-based reconstruction error is an effective and interpretable approach for digit recognition, achieving high accuracy without using complex classifiers.

## Output
- Accuracy vs. PCA components plot
- Confusion matrix
- Detailed classification report
