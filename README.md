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

# Trip Cost Distribution
<img width="719" height="560" alt="image" src="https://github.com/user-attachments/assets/bda4ceef-90eb-4f92-b205-628a174ac9d4" />

# Trip Duration Distribution
<img width="719" height="575" alt="image" src="https://github.com/user-attachments/assets/5f4b984d-d80e-4db7-ba23-a884c80b31b6" />

# Request Count Vs Day Distribution
<img width="720" height="568" alt="image" src="https://github.com/user-attachments/assets/2c162426-7b7d-452b-a325-432c9aaffacc" />

# Request Count Vs Hour Distribution
<img width="722" height="340" alt="image" src="https://github.com/user-attachments/assets/b29ffc85-b9de-4e71-ad54-0ac7262d347e" />

# Trip Status Bifurcation
<img width="652" height="517" alt="image" src="https://github.com/user-attachments/assets/721c09b1-97a4-451a-b9e3-03b40d119e7a" />

# Trip Cancellation Trend
<img width="534" height="512" alt="image" src="https://github.com/user-attachments/assets/fb4a06c3-8f51-4e25-a0b8-f7469141ce97" />

# Incomplete Rides Bifurcation
<img width="684" height="522" alt="image" src="https://github.com/user-attachments/assets/0ff5640b-c118-4f79-840e-1997acb9f159" />

# Incomplete Rides by Day and Reason Distribution
<img width="724" height="573" alt="image" src="https://github.com/user-attachments/assets/0f841204-7803-41f1-a9ea-4b9c8b3fcb68" />

# Incomplete Rides by Hour and Reason Distribution
<img width="718" height="469" alt="image" src="https://github.com/user-attachments/assets/e841ee17-5b60-43b8-9e2c-e65416bddfd3" />

# Cancellations by Weather and Reason per Ride Type Distribution
<img width="723" height="578" alt="image" src="https://github.com/user-attachments/assets/25118eba-a37b-4043-95bc-2625bc525d44" />

# Trip Completion Vs weather condition Distribution
<img width="689" height="616" alt="image" src="https://github.com/user-attachments/assets/69f4747a-99b1-4f75-84d2-a3222b035c11" />

# Top Pickup Locations
<img width="722" height="439" alt="image" src="https://github.com/user-attachments/assets/24be2736-33e4-4e78-ae39-f481429af3d6" />

# Top Droping Locations
<img width="721" height="396" alt="image" src="https://github.com/user-attachments/assets/a0a3a227-5b5e-4786-98c3-7f4601c6d0d1" />

# Top Pickup and Drop Location combined
<img width="720" height="400" alt="image" src="https://github.com/user-attachments/assets/3925e590-07ab-477c-96ae-d3c796e99d79" />

# Top Drivers
<img width="439" height="474" alt="image" src="https://github.com/user-attachments/assets/a994c432-c2cd-4931-88fe-58da17d0cbfe" />

# Average Trip Duration Over Time
<img width="722" height="401" alt="image" src="https://github.com/user-attachments/assets/1d14940c-4789-46fb-9448-f828a442d52f" />

# Total Cost Trend by Ride Type
<img width="727" height="403" alt="image" src="https://github.com/user-attachments/assets/746aa6d0-6bf8-4eed-a22f-35c2d9b23299" />

# Ride Delay Correlation Heatmap
<img width="656" height="576" alt="image" src="https://github.com/user-attachments/assets/292c66da-b4fc-4ef9-a508-5100ebf07f53" />

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
