# FitPulse Health Anomaly Detection – Report Summary

## Project Overview
The FitPulse Health Anomaly Detection project aims to analyze wearable fitness data to identify unusual or abnormal health patterns. The system processes heart rate, sleep duration, and step count data to detect anomalies that may indicate potential health risks. An interactive dashboard is developed to visualize insights and support decision-making.

---

## Objectives
- To preprocess and merge multiple fitness datasets into a unified format  
- To apply unsupervised machine learning (K-Means clustering) for anomaly detection  
- To visualize health trends and detected anomalies using an interactive dashboard  
- To generate downloadable anomaly reports for further analysis  

---

## Datasets Used
The project uses three datasets collected from fitness devices:

1. **Heart Rate Dataset**
   - Columns: `timestamp`, `heart_rate`
2. **Sleep Dataset**
   - Columns: `date`, `sleep_hours`
3. **Steps Dataset**
   - Columns: `timestamp`, `steps`

All datasets are cleaned, normalized, and aligned using date-based merging.

---

## Data Preprocessing
- Column names were standardized (lowercase and stripped of spaces)
- `timestamp` columns were converted to `date` format
- Missing or inconsistent entries were handled
- All datasets were merged on the `date` column

---

## Methodology
- **Algorithm Used:** K-Means Clustering (Unsupervised Learning)
- **Number of Clusters:** 2 (Normal vs Anomalous behavior)
- The cluster with higher deviation in selected metrics was labeled as the anomaly cluster

---

## Dashboard Features
- File upload support for all three datasets
- Metric selection (Heart Rate, Sleep Hours, Steps)
- Interactive line charts highlighting anomalies
- Tabular display of detected anomalous records
- Option to download anomaly report as CSV

---

## Results and Insights
- The system successfully identifies abnormal spikes or drops in health metrics
- Visual indicators help in quick identification of health risks
- The dashboard provides an intuitive and user-friendly experience

---

## Tools and Technologies Used
- **Programming Language:** Python
- **Libraries:** Pandas, Scikit-learn, Plotly, Streamlit
- **Deployment:** Streamlit with Ngrok tunneling
- **Platform:** Google Colaboratory

---

## Challenges Faced
- Column mismatches across datasets
- Streamlit caching issues during development
- Date-time format inconsistencies

These challenges were resolved through column normalization, process restarts, and robust validation logic.

---

## Conclusion
The FitPulse Health Anomaly Detection system effectively demonstrates how wearable data combined with machine learning can assist in early detection of potential health anomalies. The interactive dashboard enhances usability and real-time analysis, making the solution practical for health monitoring applications.

---

## Future Enhancements
- Integration of additional health metrics (calories, oxygen level)
- Use of advanced anomaly detection algorithms (Isolation Forest, DBSCAN)
- Real-time data streaming support
- User authentication and personalized dashboards
