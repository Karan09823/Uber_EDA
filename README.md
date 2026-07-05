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
![Trip Status Distribution](images/trip_status_distribution.png)
![Trip Status Bifurcation](images/trip_status_bifurcation.png)

Roughly **75.5%** of ride requests resulted in a completed trip, while **15.2%** were cancelled and **9.3%** failed due to no cars being available.

### 2. Trip Cost & Duration
![Trip Cost Distribution](images/trip_cost_distribution.png)
![Trip Duration Distribution](images/trip_duration_distribution.png)

Most trips are low-cost (under ₹100), with a long tail of higher-fare trips. Trip duration is fairly evenly spread between 10–100 minutes, peaking around the 60–90 minute range.

### 3. Demand Patterns — Day & Hour
![Request Count vs Day](images/request_count_vs_day.png)
![Request Count vs Hour](images/request_count_vs_hour.png)

Requests spike sharply on **Tuesdays**, and demand shows two clear daily peaks — early morning (5–9 AM) and evening (5–9 PM) — consistent with commute patterns.

### 4. Cancellation Analysis
![Trip Cancellation Trend](images/trip_cancellation_trend.png)
![Incomplete Rides Bifurcation](images/incomplete_rides_bifurcation.png)
![Incomplete Rides by Day and Reason](images/incomplete_rides_by_day.png)
![Incomplete Rides by Hour and Reason](images/incomplete_rides_by_hour.png)

Around **85.6%** of cancellations are driver-initiated versus **14.4%** by passengers. Cancellations cluster heavily around morning and evening peak hours, and are concentrated on Tuesdays — mirroring overall demand.

### 5. Weather Impact
![Cancellations by Weather and Reason](images/cancellations_by_weather.png)
![Trip Completion vs Weather](images/trip_completion_vs_weather.png)

Weather has only a marginal effect on completion rates — cancellation proportions stay broadly similar across Clear, Cloudy, and Rainy conditions, with a slightly higher share of passenger-driven cancellations during rain.

### 6. Location Insights
![Top Pickup Locations](images/top_pickup_locations.png)
![Top Drop Locations](images/top_drop_locations.png)
![Top Pickup and Drop Combined](images/top_pickup_drop_combined.png)

High-traffic zones include **Bangalore City Railway Station, Majestic Bus Station, Manyata Tech Park, MG Road**, and **Whitefield** — a mix of transit hubs, tech parks, and commercial centers.

### 7. Driver Performance
![Top Drivers](images/top_drivers.png)

Top-performing drivers combine high trip volume with strong tip earnings — the leading driver logged **115 trips** and over **₹35,000** in trip revenue.

### 8. Trends Over Time
![Average Trip Duration Over Time](images/avg_trip_duration_over_time.png)
![Total Cost Trend by Ride Type](images/total_cost_trend_by_ride_type.png)

Average trip duration stayed relatively stable across the observed period before ticking upward toward December. Average cost varies noticeably by ride type and day, with **UberGo** showing the most volatile pricing trend.

### 9. Correlation Analysis
![Ride Delay Correlation Heatmap](images/ride_delay_correlation_heatmap.png)

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

## 🚀 How to Run

```bash
# Clone the repository
git clone https://github.com/Karan09823/Uber_EDA.git
cd Uber_EDA

# Install dependencies
pip install pandas numpy matplotlib seaborn jupyter openpyxl

# Launch the notebook
jupyter notebook Uber_EDA.ipynb
```

---

## 📬 Feedback

If you spot an issue in the analysis or have suggestions for additional angles to explore (e.g., surge pricing, driver retention, geo-clustering of demand), feel free to open an issue or a pull request.
