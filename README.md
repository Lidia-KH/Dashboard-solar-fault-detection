# AI-Driven Photovoltaic Power Forecasting and Fault Detection

> This repository accompanies a research project on deep learning-based photovoltaic (PV) forecasting and anomaly detection. (A manuscript based on this work is currently under review)
<img width="10" alt="PowerSight-logo" src="https://github.com/user-attachments/assets/a7ca0c66-935f-4737-b02f-d13f4d5ca3fd" />

---

## Abstract

The increasing integration of photovoltaic (PV) systems into modern power grids introduces challenges related to variability, reliability, and fault management. This project presents a deep learning-based framework for PV power forecasting and residual-based fault detection using advanced time-series models.

Using long-term meteorological data from the NASA POWER dataset, multiple architectures—including LSTM, Bidirectional LSTM (BiLSTM), Transformer, and Temporal Fusion Transformer (TFT)—are developed and evaluated. Results demonstrate that Transformer-based models significantly improve forecasting accuracy and enable effective anomaly detection through residual analysis.

---

## 1. Introduction

Solar energy systems are inherently dependent on environmental conditions such as solar irradiance, temperature, and cloud cover. These variations, combined with potential system faults, make reliable forecasting and monitoring essential.

Traditional approaches based on static thresholds and manual inspection are insufficient for large-scale PV systems. This work investigates the use of deep learning techniques to enhance predictive accuracy and enable data-driven fault detection.

---

## 2. Problem Statement

Photovoltaic systems face several challenges:

- High variability due to weather conditions  
- Performance degradation over time  
- Difficulty in detecting faults early  
- Lack of scalable monitoring solutions  

This project aims to address these challenges through a unified framework combining forecasting and anomaly detection.

---

## 3. Methodology

### 3.1 Data Source

- NASA POWER dataset  
- Long-term hourly meteorological data (2001–2025)

### 3.2 Data Processing

- Data cleaning and interpolation  
- Feature engineering (temporal encoding, derived features)  
- Normalization and scaling  

### 3.3 Models Implemented

- Long Short-Term Memory (LSTM)  
- Bidirectional LSTM (BiLSTM)  
- Transformer  
- Temporal Fusion Transformer (TFT)  

These models are designed to capture both short-term fluctuations and long-term temporal dependencies in PV-related data.

---

## 4. Results and Validation

Models were evaluated on a 2023 hold-out test set derived from meteorological data, capturing seasonal variability and extreme conditions such as dust events.

---

### 4.1 Forecasting Performance

| Model        | MAE   | RMSE  | R²   |
|--------------|------|------|------|
| LSTM         | 0.055 | 0.095 | 0.79 |
| BiLSTM       | 0.062 | 0.098 | 0.78 |
| Transformer  | **0.028** | **0.042** | **0.96** |
| TFT          | 0.064 | 0.100 | 0.77 |

#### Key Findings

- The Transformer achieves the best performance, reducing MAE by ~49% compared to LSTM.  
- High R² (0.96) indicates strong predictive capability across seasonal variations.  
- LSTM and BiLSTM provide stable but lower accuracy.  
- TFT offers comparable performance with a smaller computational footprint.  

A paired t-test confirms the statistical significance of the Transformer’s superiority (*p* < 0.01).

---

### 4.2 Model Complexity and Efficiency

| Model        | Parameters | Latency        | Remarks |
|--------------|-----------|---------------|---------|
| LSTM         | 95K       | <5 ms/sample  | Compact baseline |
| BiLSTM       | 120K      | <6 ms/sample  | Bidirectional context |
| Transformer  | ~150K     | 7–10 ms/sample| Higher accuracy |
| TFT          | 58K       | <6 ms/sample  | Lightweight + interpretable |

#### Observations

- Transformer provides the highest accuracy at moderate computational cost.  
- TFT is efficient and suitable for edge deployment.  
- LSTM-based models remain viable in low-resource environments.  

---

### 4.3 Residual-Based Fault Detection

Fault detection is performed using residual analysis, where anomalies are flagged when prediction errors exceed a defined threshold (2×RMSE).

| Model        | Detection Sensitivity | False Alarm Rate |
|--------------|---------------------|------------------|
| LSTM         | Moderate            | Moderate         |
| BiLSTM       | Moderate            | Moderate         |
| Transformer  | High                | Low              |
| TFT          | High                | Low              |

#### Key Findings

- Transformer-based models produce sharper residual distributions, enabling more precise anomaly detection.  
- Residual analysis demonstrates the feasibility of detecting abnormal system behavior from forecasting errors.  
- The approach is suitable for early-stage fault detection frameworks, though validation on real PV system data is required.  

---

### 4.4 Robustness Analysis

- Transformer models maintain stable performance under extreme variations (e.g., dust conditions).  
- LSTM-based models show higher sensitivity to abrupt changes.  
- TFT provides a balance between robustness and computational efficiency.  

---

## 5. Contributions

- Comparative analysis of four deep learning architectures for PV forecasting  
- Integration of forecasting and anomaly detection in a unified framework  
- Demonstration of residual-based fault detection without labeled fault data  
- Evaluation under long-term meteorological variability  

---

## 6. Limitations

- Reliance on meteorological data rather than real measured PV output  
- Fault detection based on inferred anomalies rather than labeled events  
- Limited validation in real-world deployment environments  

---

## 7. Future Work

- Integration with real PV system measurements and SCADA data  
- Extension to inverter-level diagnostics and monitoring  
- Incorporation of cybersecurity-aware anomaly detection  
- Hybrid and ensemble modeling approaches  
- Real-time deployment in smart grid environments  

---

## 9. Technologies

- Python  
- TensorFlow / PyTorch  
- Pandas, NumPy  
- Matplotlib / Seaborn

<img width="1744" height="897" alt="Capture d&#39;écran 2025-07-11 180128" src="https://github.com/user-attachments/assets/8f7be344-52f1-41fb-a627-7c4945c3a2ed" />
---

## Author

Khelif Ibtissem Lidia  
Master’s Thesis : Artificial Intelligence & Renewable Energy Systems
