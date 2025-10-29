# Uber Rides Exploratory Data Analysis (EDA)
# Project Overview
This project performs an Exploratory Data Analysis (EDA) on Uber ride data to understand key trends, patterns, and operational insights.
The analysis aims to uncover factors influencing trip duration, cost, delays, cancellations, and customer behavior across different conditions such as weather, ride type, and payment method.

# Objectives
-Explore the structure and quality of the dataset
- Handle missing values and outliers
- Derive meaningful time-based features
- Analyze trip patterns, driver performance, and customer preferences
- Visualize key insights to support business decisions

# Dataset Information

| Column Name                               | Description                                            |
| ----------------------------------------- | ------------------------------------------------------ |
| `request_id`                              | Unique ID for each ride request                        |
| `pickup_point`                            | Ride pickup location/zone                              |
| `drop_point`                              | Ride destination/zone                                  |
| `request_timestamp`                       | Time when user requested the ride                      |
| `start_timestamp`                         | Time when the trip actually started                    |
| `drop_timestamp`                          | Time when the trip ended                               |
| `trip_cost`                               | Fare charged for the trip                              |
| `extra_tip`                               | Additional tip paid by the customer                    |
| `driver_id`                               | Unique ID of the driver                                |
| `trip_status`                             | Status of the trip (Completed / Cancelled / No Driver) |
| `ride_type`                               | Type of ride (e.g., Mini, Prime, XL)                   |
| `payment_method`                          | Payment mode (Cash, Card, UPI, etc.)                   |
| `weather`                                 | Weather condition during the trip                      |
| `trip_duration_minutes`                   | Total duration of trip in minutes                      |
| `total_cost`                              | Sum of fare and tip                                    |
| `request_date`, `start_date`, `drop_date` | Extracted dates for temporal analysis                  |
| `request_day`, `start_day`, `drop_day`    | Day names for weekly patterns                          |
| `request_hour`, `start_hour`, `drop_hour` | Hour extracted for hourly analysis                     |
| `ride_delay`                              | Delay between request and actual trip start            |
| `cancellation_reason`                     | Reason if the ride was cancelled                       |
| `hour`, `day`                             | Additional time-based features for aggregation         |

# Data Preprocessing
- Key preprocessing steps performed:
- Converted timestamps to datetime format
- Derived duration, delay, and date/time components
- Handled missing and inconsistent data entries
- Removed invalid timestamp rows (e.g., missing start/drop times for completed trips)
- Created derived features like trip_duration_minutes, total_cost, and ride_delay

# Trip Status Distribution
<img width="640" height="644" alt="image" src="https://github.com/user-attachments/assets/0dbbad36-0206-4cc0-9e55-a5421f46aaed" />
# Trip Duration Analysis
<img width="661" height="528" alt="image" src="https://github.com/user-attachments/assets/4a007152-5df2-4384-ab9e-2b60dc642622" />
# Pickup and Drop Hotspots
<img width="390" height="207" alt="image" src="https://github.com/user-attachments/assets/3d146c89-3b67-4644-844c-ebb051b9de75" />
# Payment Method Analysis
<img width="652" height="530" alt="image" src="https://github.com/user-attachments/assets/f4434e5b-ddd2-469d-bd59-055effaff846" />
# 
<img width="670" height="525" alt="image" src="https://github.com/user-attachments/assets/ddcc2420-9469-4f9a-a8e7-d2fbf2a2a152" />
<img width="1141" height="539" alt="image" src="https://github.com/user-attachments/assets/703a68e0-ad40-48a2-bda6-a343b922735a" />
<img width="596" height="476" alt="image" src="https://github.com/user-attachments/assets/3c4eed91-cd4a-4a1f-9b07-9f2550c9dd7b" />
<img width="484" height="465" alt="image" src="https://github.com/user-attachments/assets/2f844a01-6800-4ff3-8c53-7cc981c032d2" />
<img width="614" height="461" alt="image" src="https://github.com/user-attachments/assets/ea1eaa32-19a3-468a-96ca-0245a7024611" />
<img width="644" height="514" alt="image" src="https://github.com/user-attachments/assets/441732f1-2c2b-4351-b910-b3a5fb248f2c" />
<img width="957" height="622" alt="image" src="https://github.com/user-attachments/assets/67d4c81b-0bf8-4900-bc3d-5d4e225379c3" />
<img width="649" height="522" alt="image" src="https://github.com/user-attachments/assets/21099c2e-939e-47a2-b041-daec2374562d" />

# Key Insights
- Digital payments (Card/UPI) are used for longer and costlier rides.
- Cash trips dominate in volume but have lower average fare.
- Delays increase during bad weather and rush hours.
- Weekends show higher demand and slightly higher costs.
- Certain pickup/drop zones are consistently high in demand.
- Driver earnings vary significantly based on location and timing.
- Cancellations are mostly rider-driven or due to no available drivers in peak times
- 
# Tools & Libraries Used
- Python – Data analysis and visualization
- Pandas – Data manipulation and preprocessing
- NumPy – Numerical operations
- Matplotlib / Seaborn – Data visualization
- Jupyter Notebook / Google Colab – Interactive environment
