Milestone 2: Feature Extraction and Modeling

Project: FitPulse Health Anomaly Detection from Fitness Devices  



1]. Objective

The goal of Milestone 2 is to **derive meaningful insights from fitness datasets** (heart rate, steps, and sleep) by performing:

1. **Feature Extraction** – generate statistical and time-series features to capture the behavior of each metric.  
2. **Trend Modeling** – use Prophet to identify seasonal trends and temporal patterns.  
3. **Behavioral Pattern Clustering** – group similar behavior patterns to distinguish normal and atypical behavior.  

This milestone lays the **foundation for anomaly detection**, which will be addressed in Milestone 3.


 2]. Datasets Used

1. **Heart Rate (`/content/drive/MyDrive/heart_rate.csv')**
   - Columns: `timestamp`, `heart_rate`  
   - Frequency: every minute/second (depending on device)  

2. **Steps (`/content/drive/MyDrive/steps.csv`)**  
   - Columns: `timestamp`, `steps`  
   - Captures daily or minute-level activity counts  

3. **Sleep Duration (`/content/drive/MyDrive/sleep.csv`)**  
   - Columns: `date`, `sleep_hours`  
   - Daily total sleep duration  

**Preprocessing:**  
- Timestamps standardized and converted to datetime objects  
- Missing or inconsistent values handled (forward fill or interpolation where necessary)  
- Daily aggregation applied to steps and sleep datasets  

---

 3]. Methodology

 3.1 Feature Extraction
- **TSFresh** was used to automatically extract
**time-series features** from each dataset, including:
  - Mean, standard deviation, skewness, kurtosis  
  - Frequency-based characteristics (e.g., Fourier coefficients)  
  - Trend and autocorrelation metrics  
- Features were generated for
- **daily windows** to ensure multiple samples for analysis.  
- **Variance thresholding** was applied to remove low-variance or irrelevant features.  
- Resulting features from all datasets were
-  **concatenated** into a single feature matrix for modeling.

**Reasoning:**  
TSFresh allows automated extraction of features that can capture subtle temporal patterns without manual feature engineering. Daily windows ensure each row corresponds to a meaningful observation for clustering.

---

### 3.2 Trend Modeling using Prophet
- **Prophet** was applied separately to heart rate, steps, and sleep datasets.  
- Forecasts (`yhat`) were generated based on daily or weekly seasonality.  
- **Residuals** (`residual = observed - forecast`) were computed to highlight deviations from expected behavior.  

**Observations:**
- Heart rate residuals identified days with unusually high or low heart rates.  
- Steps residuals highlighted periods of unusual activity (very high or low steps).  
- Sleep residuals captured nights of insufficient or excessive sleep.  



### 3.3 Dimensionality Reduction using PCA
- **Combined TSFresh features** from all datasets were
-  **high-dimensional (1254 features)**.  
- **PCA** reduced the dimensionality to
- **2 components** for visualization and clustering.  
- **Missing values** introduced during concatenation were handled using
-  **mean imputation**.

**Reasoning:**  
PCA reduces noise and highlights the most significant patterns in data, allowing effective clustering of behavioral patterns.

---

### 3.4 Behavioral Pattern Clustering
- **KMeans** clustering (k=2) was applied to the PCA-reduced features.  
- Clusters represented:
  - **Cluster 0:** Normal behavioral patterns  
  - **Cluster 1:** Atypical patterns or potential anomalies  

**Observation:**  
- One cluster contained the majority of daily samples, indicating typical behavior.  
- The smaller cluster captured atypical or anomalous behavior, setting the stage for anomaly detection in Milestone 3.


## 4. Tools and Libraries Used
- **Python 3.x**  
- `pandas`, `numpy` → Data handling  
- `matplotlib` → Visualization  
- `scikit-learn` → PCA, KMeans, SimpleImputer  
- `tsfresh` → Automated time-series feature extraction  
- `prophet` → Trend modeling and forecasting  



## 5. Key Observations
- Residuals are effective indicators of unusual behavior.  
- PCA allowed visualization and dimensionality reduction of complex features.  
- Clustering successfully identified normal vs atypical patterns.  

