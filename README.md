# Predictive Maintenance using Random Forest & Monte-Carlo Simulation

# Installation Instructions

## Prerequisites
- Ensure you have Python 3.x installed.
- Install required libraries: `pip install -r requirements.txt`

## Environment Setup
1. Clone the repository: `git clone https://github.com/mdevaraju99/Predictive_Maintenance`
2. Navigate into the cloned directory: `cd Predictive_Maintenance`
3. Set up a virtual environment (optional but recommended):  
   `python -m venv venv`  
   `source venv/bin/activate` (Linux/Mac)  
   `venv\Scripts\activate` (Windows)

## Project Structure
- `src/`: Source code of the project  
- `data/`: Data files used in the project  
- `notebooks/`: Jupyter notebooks for exploration and analysis  

## Running the Project
1. Open Jupyter Notebook: `jupyter notebook`
2. Open the desired notebook and run the cells step by step.

## Usage
- For predictions, call the `predict()` function from the `src` module after loading the required data.


## Project Overview
Modern industrial machines generate continuous IoT sensor data such as vibration, temperature, humidity, and pressure. Unexpected failures cause downtime, safety risks, and increased maintenance costs.

This project develops a Predictive Maintenance System that:
- Classifies machine health into Normal, Warning, and Failure.
- Forecasts the number of machines likely to fail in the next 10 days using Monte-Carlo Simulation.

---

## Objectives

### 1. Machine Health Classification
Predict the machine state using a Random Forest Classifier:
- Normal  
- Warning  
- Failure  

### 2. Failure Forecasting
Use Monte-Carlo Simulation to model sensor drift and future uncertainty to estimate:
- Expected machine failures for each of the next 10 days.

---

## Dataset Description

| Component | Details |
|----------|---------|
| Source | Internal Industrial Maintenance Dataset |
| Files Used | Temperature, Humidity, Pressure, Vibration, PLC Logs, Fault Annotations |
| Final Rows After Merge | 144 |
| Sampling Rate | Every 10 minutes |
| Sensors Used | Vibration, Temperature, Pressure, Humidity |

### Class Distribution Before Balancing

| Label | Count |
|-------|-------|
| Normal | 121 |
| Warning | 17 |
| Failure | 6 |

<img width="1750" height="522" alt="image" src="https://github.com/user-attachments/assets/f99cee4c-de76-4211-83f2-747c22ee38d9" />


A significant class imbalance was present and addressed using SMOTE oversampling.

---

## Methodology

| Stage | Method | Purpose |
|--------|--------|---------|
| Data Pre-processing | Timestamp merge, feature selection | Align and clean sensor data |
| Scaling | StandardScaler | Improves model stability and supports SMOTE |
| Imbalance Handling | SMOTE oversampling | Helps the model learn from limited failure samples |
| ML Model | Random Forest Classifier | Robust for small datasets and noisy signals |
| Forecasting | Monte-Carlo Simulation | Models uncertainty and future sensor degradation |

---

## Model Training Results

### Train-Test Split
Stratified 80% training and 20% testing split.

### Classification Report

| Class | Precision | Recall | F1-Score | Support |
|-------|----------|--------|----------|---------|
| Failure | 1.00 | 0.83 | 0.91 | 6 |
| Normal | 0.96 | 0.99 | 0.98 | 121 |
| Warning | 0.93 | 0.76 | 0.84 | 17 |

Overall Accuracy: **95.83%**

---

## Confusion Matrix


<img width="812" height="521" alt="image" src="https://github.com/user-attachments/assets/925d4718-823f-4909-b45a-5c07359ac5cf" />

---

### First Usecase where machines are getting repaired and working normally from next day
## Machine-Level 10-Day Failure Forecast

<img width="1888" height="849" alt="image" src="https://github.com/user-attachments/assets/ac2f171b-2a0a-4a1d-8a4d-72f29c1ed10e" />

Here we can see the machine failures and reason for failures,then how we can repair that on that day.

---
##  10-Day Failure Risk Summary

<img width="1785" height="714" alt="image" src="https://github.com/user-attachments/assets/d2ec3784-c877-4c46-98fb-78557afcc7c2" />


---

### Second Usecase where failed machines are not considering for next forecasting 
## Machine-Level 10-Day Failure Forecast

<img width="1833" height="830" alt="image" src="https://github.com/user-attachments/assets/a2e5f43c-5f9c-4a21-b0b3-ae0d3e4bf99a" />


