FitPulse Health Anomaly Detection from Fitness Devices
Milestone 1: Data Collection and Preprocessing

Objective

The objective of Milestone 1 is to collect, preprocess, and normalize fitness data from wearable devices, including heart rate, steps, calories, and sleep logs. The goal is to create a clean, consolidated dataset with all metrics aligned to a 1-minute frequency, enabling accurate downstream analysis and anomaly detection.

Key goals:

Read multiple CSV/JSON fitness datasets.

Normalize timestamps to UTC for consistency.

Handle missing or null values using appropriate strategies.

Align metrics to a uniform 1-minute interval.

Merge datasets into a single cleaned dataset with additional derived features like activity status.

Dataset Source:

We used open datasets from Kaggle (Fitbit Fitness Tracker dataset).

Files used:

heartrate_seconds_merged.csv – Heart rate measured in seconds.

dailyActivity_merged.csv – Daily steps and calories burned.

sleepDay_merged.csv – Sleep logs with total minutes asleep.

Fitbit Fitness Tracker Dataset (Kaggle): [https://www.kaggle.com/datasets/arashnic/fitbit](https://www.kaggle.com/datasets/arashnic/fitbit)

Each dataset contains a common key, Id, and a timestamp column that allows merging.

Steps Performed:

Data Upload
Uploaded CSV datasets into Google Colaboratory.
Verified schema of each file and identified columns required for analysis.
Timestamp Normalization
Converted all timestamp columns to UTC using Pandas pd.to_datetime(..., utc=True).
Ensured that SleepDay, ActivityDate, ActivityMinute, and heart rate timestamps are consistent.
Missing Value Handling

For heart rate: missing values filled using forward-fill.

For steps and calories: daily values expanded to 1-minute resolution, missing minutes filled with 0.

For sleep: daily sleep duration expanded to 1-minute intervals, missing minutes filled with 0.

Resampling & Alignment:

Heart rate resampled to 1-minute mean values.
Steps and calories expanded from daily to 1-minute resolution.
Sleep duration aligned to 1-minute intervals.
All datasets merged using Id and Time as keys.
Derived Feature: Activity
Added a new column Activity based on steps:

Steps > 0 → 'Active'  
Steps = 0 → 'Inactive'


Final Dataset Creation:

Merged heart rate, steps, calories, sleep, and activity into final_df.
Sorted by Id and Time.
Ensured all columns are properly formatted and free from missing values.

Tools & Libraries Used:

Python 3.x
Google Colab for cloud-based execution
Pandas – for data manipulation and merging
NumPy – for numerical operations
Matplotlib & Seaborn – for data visualization

Final Dataset Features:

Column	Description
Id	Unique user ID
Time	Timestamp (UTC)
HeartRate	Heart rate per minute
Steps	Step count per minute
Calories	Calories burned per minute
TotalMinutesAsleep	Sleep duration per minute
Activity	Derived activity status (‘Active’/’Inactive’)

Sample Output:

Id	Time	HeartRate	Steps	Calories	TotalMinutesAsleep	Activity
1503960366	2023-01-01 00:00:00+00:00	72	0	0	0	Inactive
1503960366	2023-01-01 00:01:00+00:00	71	0	0	0	Inactive
1503960366	2023-01-01 00:02:00+00:00	70	0	0	0	Inactive

Visualizations:

We generated graphs to understand temporal patterns:
Heart Rate vs Time
Shows heart rate fluctuations over the day.
Steps vs Time
Illustrates periods of activity and inactivity.
Calories vs Time
Indicates energy expenditure patterns.
Sleep Pattern
Shows total sleep minutes aligned to time.

Activity Distribution:

Bar chart for Active vs Inactive periods.

