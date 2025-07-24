# 🌌 Unveiling Uber's Fare Dynamics: A Power BI Odyssey

**Course:** Introduction to Big Data Analytics – INSY 8413  
**Instructor:** Eric Maniraguha ([📧 eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw))  
**Group:** B  
**Tool:** Power BI Desktop  
**Dataset Source:** [Uber Fares Dataset](https://www.kaggle.com/datasets/yasserh/uber-fares-dataset) (Kaggle)  
**Student Name:** MUGENI Cynthia  
**Student ID:** 26600  
**GitHub Repository:** [Discover the Code](https://github.com/Mugeni24/uber-fares-powerbi-analysis)

---

## 🌠 Project Vision

Embark on an analytical voyage to decode the pulse of Uber’s fare ecosystem! This project harnesses the Uber Fares Dataset to illuminate the intricate interplay of ride fares, trip distances, and temporal patterns. Through Python’s analytical precision and Power BI’s visual artistry, we craft an immersive dashboard that transforms raw data into a symphony of insights, empowering stakeholders to navigate Uber’s operational landscape with clarity and confidence.

### 🎯 Objectives
- **Discover**: Dive deep into Exploratory Data Analysis (EDA) to uncover dataset intricacies.  
- **Refine**: Purify the dataset by addressing inconsistencies and outliers.  
- **Innovate**: Engineer features to amplify analytical depth.  
- **Visualize**: Create a captivating Power BI dashboard to showcase trends across time and space.  
- **Empower**: Deliver actionable insights to optimize Uber’s operations and strategy.

---

## 🛠️ Analytical Architecture

### 1. 📡 Data Acquisition & Exploration
- **Source**: Extracted the Uber Fares Dataset from Kaggle, a treasure trove of ride data.  
- **Tool**: Leveraged Jupyter Notebook with Pandas for initial exploration.  
- **Actions**: Probed dataset structure, data types, and anomalies to lay a solid analytical foundation.

![Dataset Preview](https://github.com/user-attachments/assets/fddab80d-f80e-4330-98fe-09b5b410bbd1)

---

### 2. 🧬 Data Purification
- **Cleansing**: Removed null values and outliers in fare and distance fields to ensure data integrity.  
- **Transformation**: Standardized timestamps into datetime formats for seamless temporal analysis.

```python
import pandas as pd
import numpy as np

# Load dataset
uber_df = pd.read_csv('uber_fares.csv')

# Drop missing values
uber_df_clean = uber_df.dropna()

# Filter out invalid fares
uber_df_clean = uber_df_clean[uber_df_clean['fare_amount'] > 0]

# Restrict passenger counts to realistic range (1-6)
uber_df_clean = uber_df_clean[(uber_df_clean['passenger_count'] >= 1) & (uber_df_clean['passenger_count'] <= 6)]

# Define NYC geographic bounds
lon_min, lon_max = -74.05, -73.75
lat_min, lat_max = 40.63, 40.85

# Filter valid pickup and dropoff coordinates
uber_df_clean = uber_df_clean[
    (uber_df_clean['pickup_longitude'].between(lon_min, lon_max)) &
    (uber_df_clean['pickup_latitude'].between(lat_min, lat_max)) &
    (uber_df_clean['dropoff_longitude'].between(lon_min, lon_max)) &
    (uber_df_clean['dropoff_latitude'].between(lat_min, lat_max))
]

# Convert pickup_datetime to datetime
uber_df_clean['pickup_datetime'] = pd.to_datetime(uber_df_clean['pickup_datetime'], errors='coerce')
uber_df_clean = uber_df_clean.dropna(subset=['pickup_datetime'])

# Drop irrelevant columns
uber_df_clean = uber_df_clean.drop(columns=['Unnamed: 0', 'key'], errors='ignore')

# Output cleaned dataset
print("Cleaned dataset shape:", uber_df_clean.shape)
uber_df_clean.head()
```

![Cleaned Dataset](https://github.com/user-attachments/assets/f041c7cf-73be-4243-912a-5fb87de5c264)

---

### 3. 🌟 Feature Engineering
The analysis reveals a strong correlation between fare amounts and trip distances, with most rides concentrated in Manhattan and fares typically under $20. Evening hours exhibit greater fare variability, hinting at surge pricing dynamics.

- **Output**: Exported enriched dataset as `uber_fares_enhanced.csv`.

#### a. Fare and Distance Distribution
- **🔍 Insight**: Most rides are short, with fares under $20, but outliers suggest surge pricing or long-distance trips.  
- **💡 Impact**: Highlights Uber’s focus on short trips, guiding pricing strategies and anomaly detection.

![Fare and Distance](https://github.com/user-attachments/assets/1086d0d6-96c1-4515-8de6-857810a9eac2)

#### b. Fare Range Analysis ($0–$100)
- **🔍 Insight**: Fares predominantly fall in the $5–$10 range, with frequency decreasing as fares rise.  
- **💡 Impact**: Reinforces Uber’s appeal for affordable rides, informing promotional strategies.

![Fare Range](https://github.com/user-attachments/assets/39324b1f-a798-4fe6-8a21-f6dac9aa2251)

#### c. Distance vs. Fare & Hourly Fare Trends
- **🔍 Scatter Plot Insight**: A linear relationship confirms distance as a primary fare driver.  
- **🔍 Boxplot Insight**: Evening hours show wider fare variability, likely due to surge pricing.  
- **💡 Impact**: Validates pricing models and suggests dynamic driver allocation during peak hours.

![Distance vs Fare](https://github.com/user-attachments/assets/fe5f24b5-2ec6-42ae-9a89-18fd2c0d402d)

---

### 4. 🎨 Power BI Visualizations
A constellation of visuals transforms data into compelling narratives, offering intuitive insights into Uber’s operational dynamics.

#### 📈 Visual 1: Fare vs. Distance Scatter
- **Type**: Scatter Plot  
- **Axis**: `distance` vs. `fare_amount`  
- **Insight**: Visualizes the linear relationship between trip length and fare, flagging outliers for review.

![Fare vs Distance](https://github.com/user-attachments/assets/1fbd797e-4d5d-4227-913e-9e702f1e5e8d)

#### 📊 Visual 2: Average Fare by Hour
- **Type**: Line Chart  
- **Axis**: `pickup_hour`  
- **Values**: Average `fare_amount`  
- **Insight**: Reveals fare fluctuations, guiding dynamic pricing strategies.

![Average Fare by Hour](https://github.com/user-attachments/assets/56d69a7b-d9bc-4cb5-b309-bb79b18660a0)

#### 📅 Visual 3: Fare by Day of Week
- **Type**: Clustered Column Chart  
- **Axis**: `pickup_dayofweek`  
- **Values**: `fare_amount`  
- **Insight**: Identifies weekly trends for operational planning.

![Fare by Day](https://github.com/user-attachments/assets/e0999d18-4eae-4961-b5f3-dcfb5116a78b)

#### 🗺️ Visual 4: Pickup Distribution
- **Type**: Line and Stacked Column Chart (map alternative)  
- **Insight**: Approximates geospatial ride patterns for market analysis.

![Pickup Distribution](https://github.com/user-attachments/assets/6201ffdc-ce42-48b5-b636-cd324aa8a153)

#### 📆 Visual 5: Monthly Fare Trends
- **Type**: Area Chart  
- **Axis**: `month`  
- **Values**: `fare_amount`  
- **Insight**: Highlights seasonal trends for strategic planning.

![Monthly Trends](https://github.com/user-attachments/assets/e75b2e1b-b559-4d23-9c9a-a7a07e89dfce)

---

### 5. 🖼️ Interactive Dashboard
- **Design**: A unified Power BI dashboard weaving all visuals into a seamless experience.  
- **Features**:  
  - **Slicers**: Enable filtering by hour, day, and month for dynamic exploration.  
  - **Aesthetics**: Vibrant colors, clear titles, and intuitive tooltips.  
- **Purpose**: Empowers stakeholders to interact with data and uncover insights effortlessly.

![Dashboard](https://github.com/user-attachments/assets/d3115c7f-2d5c-4313-a941-33b57983d2c4)

---

## 📜 Report Structure
The final report is a comprehensive narrative of the analytical journey:  
- **Introduction**: Sets the stage with project goals and dataset context.  
- **Methodology**: Details Python cleaning and Power BI visualization processes.  
- **Analysis**: Interprets insights from each visual.  
- **Results**: Summarizes fare trends and operational patterns.  
- **Conclusion**: Reflects on findings and their implications.  
- **Recommendations**: Proposes strategies like peak-hour driver incentives and pricing adjustments.

---

## 📦 Deliverables
- [x] **Power BI File**: Interactive `.pbix` dashboard.  
- [x] **Datasets**: Cleaned `uber_fares_enhanced.csv`.  
- [x] **Jupyter Notebook**: Python code for data processing.  
- [x] **README**: This meticulously crafted document.  
- [x] **GitHub**: Public repository shared with the instructor.

---

## 🛡️ Academic Integrity
This project is an original creation, born from rigorous analysis and visualization of the Uber Fares Dataset. All insights are derived authentically using Python and Power BI, upholding the highest standards of academic excellence.

---

## 🌟 Why This Project Excels
This project transcends traditional analysis, weaving data into a vibrant tapestry of insights. The Power BI dashboard is not just a tool but a storytelling masterpiece, blending technical rigor with visual elegance. Every step—from data cleansing to interactive visualization—reflects a passion for discovery and a commitment to excellence.

---

*Crafted with Precision and Passion by MUGENI Cynthia*  
*Driving Data Toward a Brighter Future* 🚀

  
***Proverbs 12:24: "The hand of the diligent will rule, while the slothful will be put to forced labor."***
