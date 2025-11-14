# Traffic Flow Forecasting using Bayesian Network

The aim of this project is to **predict short-term traffic speed** at a target road sensor.  

We follow the method from the paper: **“A Bayesian Network Approach to Traffic Flow Forecasting” (Sun et al., 2006)**

Since the original dataset is not available, we use the publicly available **PEMS-BAY** dataset for implementation.

Link: `https://www.kaggle.com/datasets/scchuy/pemsbay`

The main goal is to build a simple **cause → effect** model using past traffic values and nearby sensors to forecast the future speed.

---

## Approach Used

### 1. Bayesian Network (Cause–Effect Modeling)
We model traffic forecasting as: Past target values + Neighbor sensor values → Future target value


### 2. PCA (Dimensionality Reduction)
The input has many variables, so we apply Principal Component Analysis (PCA) to reduce the dimensionality while keeping ~95% variance.

### 3. Gaussian Mixture Model (GMM)
We fit a Gaussian Mixture Model (GMM) to learn the joint probability distribution of the cause and effect variables.  
We use Bayesian Information Criterion (BIC) to automatically select the best number of components.

### 4. Competitive EM (CEM)
We also implement Competitive Expectation–Maximization (CEM), which:
- Splits large clusters  
- Removes small clusters  
- Automatically adjusts the number of Gaussian components  

This makes the model more flexible compared to standard EM.

### 5. MMSE Forecasting
We compute the Minimum Mean Square Error (MMSE) estimate from the mixture model to predict the future speed.

---


