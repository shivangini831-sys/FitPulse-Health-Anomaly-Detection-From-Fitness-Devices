FitPulse Health Anomaly Detection from Fitness Devices
Milestone 1: Data Collection and Preprocessing

1] Objective

The objective of Milestone 1 is to collect, preprocess, and normalize fitness data from wearable devices, including heart rate, steps, calories, and sleep logs. The goal is to create a clean, consolidated dataset with all metrics aligned to a 1-minute frequency, enabling accurate downstream analysis and anomaly detection.

2] Key goals:

1.Read multiple CSV/JSON fitness datasets.

2.Normalize timestamps to UTC for consistency.

3.Handle missing or null values using appropriate strategies.

4.Align metrics to a uniform 1-minute interval.

5.Merge datasets into a single cleaned dataset with additional derived features like activity status.

3] Dataset Source:

We used open datasets from Kaggle (Fitbit Fitness Tracker dataset).

4] Files used:

heartrate_seconds_merged.csv – Heart rate measured in seconds.

dailyActivity_merged.csv – Daily steps and calories burned.

sleepDay_merged.csv – Sleep logs with total minutes asleep.

Fitbit Fitness Tracker Dataset (Kaggle): [https://www.kaggle.com/datasets/arashnic/fitbit](https://www.kaggle.com/datasets/arashnic/fitbit)

Each dataset contains a common key, Id, and a timestamp column that allows merging.

5] Steps Performed:

1.Data Upload

2.Uploaded CSV datasets into Google Colaboratory.

3.Verified schema of each file and identified columns required for analysis.

4.Timestamp Normalization

5.Converted all timestamp columns to UTC using Pandas pd.to_datetime(..., utc=True).

6.Ensured that SleepDay, ActivityDate, ActivityMinute, and heart rate timestamps are consistent.

7.Missing Value Handling

8.For heart rate: missing values filled using forward-fill.

9.For steps and calories: daily values expanded to 1-minute resolution, missing minutes filled with 0.

10.For sleep: daily sleep duration expanded to 1-minute intervals, missing minutes filled with 0.

6] Resampling & Alignment:

1.Heart rate resampled to 1-minute mean values.

2.Steps and calories expanded from daily to 1-minute resolution.

3.Sleep duration aligned to 1-minute intervals.

4.All datasets merged using Id and Time as keys.

5.Derived Feature: Activity

6.Added a new column Activity based on steps:

Steps > 0 → 'Active'  
Steps = 0 → 'Inactive'


7] Final Dataset Creation:

1.Merged heart rate, steps, calories, sleep, and activity into final_df.

2.Sorted by Id and Time.

3.Ensured all columns are properly formatted and free from missing values.

8]Tools & Libraries Used:

1.Python 3.x

2.Google Colab for cloud-based execution

3.Pandas – for data manipulation and merging

4.NumPy – for numerical operations

5.Matplotlib & Seaborn – for data visualization

9] Final Dataset Features:

Column	Description
Id	Unique user ID
Time	Timestamp (UTC)
HeartRate	Heart rate per minute
Steps	Step count per minute
Calories	Calories burned per minute
TotalMinutesAsleep	Sleep duration per minute
Activity	Derived activity status (‘Active’/’Inactive’)

10] Visualizations:

We generated graphs to understand temporal patterns:
1. Heart Rate vs Time
Shows heart rate fluctuations over the day.
2. Steps vs Time
Illustrates periods of activity and inactivity.
3. Calories vs Time
Indicates energy expenditure patterns.
4. Sleep Pattern
Shows total sleep minutes aligned to time.

11] Activity Distribution:

Bar chart for Active vs Inactive periods.

