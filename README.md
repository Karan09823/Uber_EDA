# 🚖 Uber Rides — Exploratory Data Analysis (EDA)

An end-to-end exploratory data analysis of Uber ride-request data from Bangalore, uncovering patterns in trip completion, cancellations, demand, pricing, and driver performance.

---

## 📌 Project Overview

Ride-hailing platforms generate rich operational data at every stage of a trip — from request to pickup to drop-off. This project explores a Uber-style ride dataset to understand **what drives trip completion, cancellation, delay, and cost**, and to surface insights that could inform operational and business decisions.

The analysis covers the full data pipeline: cleaning and feature engineering, univariate and bivariate analysis, time-based trend analysis, and correlation analysis — supported by visualizations at every stage.

---

## 🎯 Objectives

- Explore the structure, quality, and completeness of the raw dataset
- Clean missing values, invalid timestamps, and inconsistent entries
- Engineer time-based features (date, day, hour) for temporal analysis
- Understand trip status distribution (completed vs. cancelled vs. no cars available)
- Analyze cancellation behavior by day, hour, weather, and ride type
- Identify demand hotspots (top pickup/drop locations) and peak demand windows
- Evaluate driver performance and cost/duration trends over time
- Examine correlations between cost, tip, delay, and duration

---

## 🗂️ Dataset Overview

The dataset contains simulated Uber ride-request records for Bangalore, with the following key fields:

| Column | Description |
|---|---|
| `request_id` | Unique identifier for each ride request |
| `pickup_point` | Pickup location/zone |
| `drop_point` | Destination location/zone |
| `request_timestamp` | Time the ride was requested |
| `start_timestamp` | Time the trip started |
| `drop_timestamp` | Time the trip ended |
| `trip_cost` | Fare charged for the trip |
| `extra_tip` | Additional tip paid by the customer |
| `driver_id` | Unique identifier for the driver |
| `trip_status` | Trip Completed / Trip Cancelled / No Cars Available |
| `ride_type` | UberGo / UberX / UberXL |
| `payment_method` | Cash, Card, UPI, etc. |
| `weather` | Weather condition during the trip (Clear/Cloudy/Rainy) |
| `trip_duration_minutes` | Duration of the trip in minutes |
| `total_cost` | Sum of fare and tip |
| `request_date`, `start_date`, `drop_date` | Derived calendar dates |
| `request_day`, `start_day`, `drop_day` | Derived day-of-week fields |
| `request_hour`, `start_hour`, `drop_hour` | Derived hour-of-day fields |
| `ride_delay` | Delay between request and actual trip start |
| `cancellation_reason` | Driver or Passenger (for incomplete trips) |

---

## 🧹 Data Preprocessing

Key steps taken before analysis:

- Converted all timestamp columns to proper `datetime` format
- Derived `trip_duration_minutes`, `ride_delay`, and `total_cost` as engineered features
- Extracted `date`, `day`, and `hour` components from timestamps for time-series and pattern analysis
- Identified and removed invalid records — e.g., completed trips missing a start or drop timestamp
- Standardized categorical fields (trip status, cancellation reason, weather, ride type) for consistent grouping

---

## 📊 Exploratory Analysis & Visualizations

### 1. Trip Status Overview
<img width="567" height="612" alt="image" src="https://github.com/user-attachments/assets/8a442209-4ddf-4a01-b5f3-4ee7524ad0d1" />


Roughly **75.5%** of ride requests resulted in a completed trip, while **15.2%** were cancelled and **9.3%** failed due to no cars being available.

### 2. Trip Cost & Duration
<img width="685" height="613" alt="image" src="https://github.com/user-attachments/assets/3aaf6135-e2da-43bc-a4a2-0cedda48632d" />
<img width="706" height="617" alt="image" src="https://github.com/user-attachments/assets/013bd383-e12d-4838-b1a5-bbcece1905a5" />


Most trips are low-cost (under ₹100), with a long tail of higher-fare trips. Trip duration is fairly evenly spread between 10–100 minutes, peaking around the 60–90 minute range.

### 3. Demand Patterns — Day & Hour
<img width="697" height="602" alt="image" src="https://github.com/user-attachments/assets/0062c297-2d4f-432c-a484-a5be7e53675c" />
<img width="750" height="426" alt="image" src="https://github.com/user-attachments/assets/7ee8e8c2-7710-436f-9cfb-93c594677ba4" />


Requests spike sharply on **Tuesdays**, and demand shows two clear daily peaks — early morning (5–9 AM) and evening (5–9 PM) — consistent with commute patterns.

### 4. Cancellation Analysis
<img width="575" height="578" alt="image" src="https://github.com/user-attachments/assets/f6860076-13a5-4d29-be81-55aadfba4f58" />
<img width="700" height="606" alt="image" src="https://github.com/user-attachments/assets/1a783b70-1cb2-42c6-a721-fb0c904f6b42" />
<img width="697" height="607" alt="image" src="https://github.com/user-attachments/assets/e83854f3-b5ea-4428-8223-2ec1958491a0" />
<img width="732" height="556" alt="image" src="https://github.com/user-attachments/assets/88c883bc-659d-4ce6-86c6-fa66df783bb5" />

Around **85.6%** of cancellations are driver-initiated versus **14.4%** by passengers. Cancellations cluster heavily around morning and evening peak hours, and are concentrated on Tuesdays — mirroring overall demand.

### 5. Weather Impact
<img width="666" height="607" alt="image" src="https://github.com/user-attachments/assets/20a15cf4-a83d-490d-afa7-8cc3513d0626" />
<img width="668" height="612" alt="image" src="https://github.com/user-attachments/assets/32baea28-276b-4153-b326-a588974ab72c" />


Weather has only a marginal effect on completion rates — cancellation proportions stay broadly similar across Clear, Cloudy, and Rainy conditions, with a slightly higher share of passenger-driven cancellations during rain.

### 6. Location Insights
<img width="757" height="512" alt="image" src="https://github.com/user-attachments/assets/c37701b3-9381-4c06-ab4e-222199024efe" />
<img width="741" height="482" alt="image" src="https://github.com/user-attachments/assets/925f3bbc-03d6-466d-a509-294d920b7816" />
<img width="742" height="487" alt="image" src="https://github.com/user-attachments/assets/9902fa8d-7b61-43ea-a8df-3f13a207a0e2" />


High-traffic zones include **Bangalore City Railway Station, Majestic Bus Station, Manyata Tech Park, MG Road**, and **Whitefield** — a mix of transit hubs, tech parks, and commercial centers.

### 7. Driver Performance
<img width="467" height="558" alt="image" src="https://github.com/user-attachments/assets/1ec140c7-17f9-4053-9c49-494a0bbf495e" />


Top-performing drivers combine high trip volume with strong tip earnings — the leading driver logged **115 trips** and over **₹35,000** in trip revenue.

### 8. Trends Over Time
<img width="748" height="483" alt="image" src="https://github.com/user-attachments/assets/12d8187c-ceae-4ab2-8173-19ee4c3b154f" />
<img width="740" height="483" alt="image" src="https://github.com/user-attachments/assets/135c0bc1-c3ee-4ca1-ad0f-20b32dccc4e7" />

Average trip duration stayed relatively stable across the observed period before ticking upward toward December. Average cost varies noticeably by ride type and day, with **UberGo** showing the most volatile pricing trend.

### 9. Correlation Analysis
<img width="647" height="620" alt="image" src="https://github.com/user-attachments/assets/aab84e6c-88d8-40ac-8249-c04845e8d444" />


`trip_cost` and `total_cost` are (expectedly) perfectly correlated, and both show a moderate positive correlation with `extra_tip` (**0.63–0.67**) — suggesting costlier trips tend to draw higher tips. Trip duration and ride delay are unrelated to cost, indicating fare is driven primarily by distance/ride type rather than how long the ride takes.

---

## 💡 Key Insights

- **Completion rate is strong overall (~75%)**, but cancellations are overwhelmingly driver-initiated rather than passenger-initiated.
- **Demand is highly peaked** around commute hours (morning & evening) and spikes on specific weekdays, pointing to opportunities for dynamic driver allocation.
- **Weather has limited impact** on trip completion, suggesting operational cancellations are more behavior-driven than condition-driven.
- **Tips scale with fare**, but not with trip duration or delay — riders tip based on cost, not time spent.
- **Demand is concentrated** around transit hubs, tech parks, and commercial centers, making these natural targets for driver positioning strategies.
- **A small group of drivers** account for disproportionately high trip volume and earnings, indicating potential for identifying and replicating high-performer behavior.

---

## 🛠️ Tools & Libraries Used

- **Python** — core analysis language
- **Pandas** — data manipulation and preprocessing
- **NumPy** — numerical operations
- **Matplotlib / Seaborn** — data visualization
- **Jupyter Notebook** — interactive analysis environment

---

## 📁 Repository Structure

```
Uber_EDA/
├── Uber_EDA.ipynb      # Main analysis notebook
├── uber_eda.py         # Script version of the analysis
├── Uber_data.xlsx      # Source dataset
├── images/             # Exported chart images used in this README
└── README.md
```

---
