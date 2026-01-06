# Milestone 3: Anomaly Detection and Visualization

## Objective
The objective of Milestone 3 is to detect abnormal health patterns from fitness device data and visualize them effectively. This milestone focuses on identifying anomalies in heart rate and sleep behavior using time-series modeling, domain-specific threshold rules, and clustering results obtained in Milestone 2.

---

## Steps Followed

### 1. Residual Analysis (Time-Series Modeling)
A Prophet time-series model was trained on heart rate data to learn normal physiological patterns. Residuals were calculated as the difference between actual and predicted values. Data points with unusually large residuals were identified as potential anomalies.

### 2. Threshold-Based Anomaly Detection
Domain-specific thresholds were applied to detect abnormal values:
- Heart rate values below 40 bpm or above 120 bpm were considered abnormal.
- Sleep durations below 4 hours or above 10 hours were marked as anomalies.
These thresholds help capture medically significant deviations.

### 3. Cluster-Based Anomaly Detection
Behavioral cluster labels generated in Milestone 2 were reused. Data points belonging to outlier or minority clusters were considered anomalous, providing behavioral context to physiological abnormalities.

### 4. Visualization of Anomalies
Interactive time-series visualizations were created for heart rate and sleep data. Anomalous points were highlighted using markers, making abnormal patterns easy to identify and interpret.


## Tools Used
- Python  
- Google Colaboratory  
- Prophet (Time-Series Forecasting)  
- Pandas, NumPy (Data Processing)  
- Plotly, Matplotlib (Visualization)


## Key Insights and Visualizations
- Sudden spikes and drops in heart rate were successfully detected using residual and threshold-based methods.
- Irregular sleep durations highlighted potential sleep-related health issues.
- Cluster-based anomaly detection helped identify users with unusual behavioral patterns.
- Visualizations provided a clear and intuitive understanding of when and where anomalies occurred.

The results demonstrate that combining time-series analysis, rule-based thresholds, and clustering techniques is effective for detecting and explaining health anomalies from fitness device data.

