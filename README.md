# 🌟 Uber Fares Dataset Analysis with Power BI

**Course:** Introduction to Big Data Analytics – INSY 8413  
**Instructor:** Eric Maniraguha ([📧 eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw))  
**Group:** B  
**Tool:** Power BI Desktop  
**Dataset Source:** [Uber Fares Dataset](https://www.kaggle.com/datasets/yasserh/uber-fares-dataset) (Kaggle)  
**Student Name:** MUGENI Cynthia  
**Student ID:** 26600  
**GitHub Repository:** [Explore the Code](https://github.com/Mugeni24/uber-fares-powerbi-analysis)

---

## 🚀 Project Mission

Embark on a data-driven journey to unravel the intricacies of Uber’s fare dynamics! This project harnesses the power of the Uber Fares Dataset to illuminate patterns in ride fares, trip durations, and operational efficiencies. By blending Python’s analytical prowess with Power BI’s visualization magic, we deliver actionable insights through an interactive dashboard that captivates and informs.

### 🎯 Objectives
- **Explore**: Conduct in-depth Exploratory Data Analysis (EDA) to understand dataset nuances.  
- **Clean**: Refine the dataset by addressing inconsistencies and outliers.  
- **Enhance**: Engineer new features to enrich analysis.  
- **Visualize**: Craft a dynamic Power BI dashboard showcasing fare trends across time and geography.  
- **Inform**: Provide stakeholders with clear, actionable insights to optimize operations.

---

## 🛠️ Implementation Blueprint

### 1. 📥 Data Acquisition & Exploration
- **Source**: Sourced the Uber Fares Dataset from Kaggle.  
- **Tool**: Loaded into Jupyter Notebook using Pandas for initial exploration.  
- **Actions**: Inspected dataset structure, data types, null values, and duplicates to ensure a robust foundation.  

<img width="1067" height="332" alt="df head" src="https://github.com/user-attachments/assets/fddab80d-f80e-4330-98fe-09b5b410bbd1" />

---

### 2. 🧹 Data Refinement
- **Cleaning**: Eliminated missing values and extreme outliers in fare and distance fields.  
- **Transformation**: Converted timestamps to proper datetime formats for seamless analysis.  

```python
import numpy as np

# Drop rows with missing values
uber_df_clean = uber_df.dropna()

# Remove fares less than or equal to zero
uber_df_clean = uber_df_clean[uber_df_clean['fare_amount'] > 0]

# Remove unrealistic passenger counts (keep 1 to 6)
uber_df_clean = uber_df_clean[(uber_df_clean['passenger_count'] >= 1) & (uber_df_clean['passenger_count'] <= 6)]

# Define plausible NYC longitude and latitude ranges
# NYC approx longitude: -74.05 to -73.75
# NYC approx latitude: 40.63 to 40.85

lon_min, lon_max = -74.05, -73.75
lat_min, lat_max = 40.63, 40.85

# Filter pickup coordinates
uber_df_clean = uber_df_clean[
    (uber_df_clean['pickup_longitude'].between(lon_min, lon_max)) &
    (uber_df_clean['pickup_latitude'].between(lat_min, lat_max))
]

# Filter dropoff coordinates
uber_df_clean = uber_df_clean[
    (uber_df_clean['dropoff_longitude'].between(lon_min, lon_max)) &
    (uber_df_clean['dropoff_latitude'].between(lat_min, lat_max))
]

# Convert pickup_datetime from string to datetime type
uber_df_clean['pickup_datetime'] = pd.to_datetime(uber_df_clean['pickup_datetime'], errors='coerce')

# Drop any rows where datetime conversion failed (NaT)
uber_df_clean = uber_df_clean.dropna(subset=['pickup_datetime'])

# Drop unnecessary columns, like 'Unnamed: 0' and 'key' if not needed
uber_df_clean = uber_df_clean.drop(columns=['Unnamed: 0', 'key'])

# Check the cleaned dataset
print("Cleaned dataset shape:", uber_df_clean.shape)
uber_df_clean.head()
```

You will see that the  output will be looking like this:
<img width="836" height="239" alt="second 1" src="https://github.com/user-attachments/assets/f041c7cf-73be-4243-912a-5fb87de5c264" />



### 3. 🧠 Features Engineering
The analysis of the Uber dataset reveals that fare amounts are strongly correlated with trip distance. Most rides are short, with fares typically under $20, and the highest concentration of pickups is in Manhattan. Time of day also influences fare variability, with more fluctuation in prices during evening hours. 
- **Output**: Exported the enriched dataset as `uber_fares_enhanced.csv`.  

#### 1. Distribution of Uber Fare Amounts and Trip Distances
- **🔍 Observation**:
Most Uber fares are under $20, and most trips are short. However, there are notable outliers with unusually high fares and long distances.

- **💡 Insight**:
Uber’s business is largely made up of short-to-medium trips. High-fare outliers may result from long-distance rides, surge pricing, or rare events. These should be flagged for deeper operational review or error checking.



<img width="1005" height="444" alt="feature1" src="https://github.com/user-attachments/assets/1086d0d6-96c1-4515-8de6-857810a9eac2" />

---
#### 2. Distribution of Uber Fare Amounts (from $0 to $$0 to $100)
- **🔍 Observation**:
Most rides fall within the $5–$10 range, with the frequency of trips dropping as the fare increases.

- **💡 Insight**:
The service is primarily used for affordable, short trips. This can guide pricing models, promotions, or package offers focused on budget-conscious customers.



<img width="856" height="418" alt="feature2" src="https://github.com/user-attachments/assets/39324b1f-a798-4fe6-8a21-f6dac9aa2251" />

---
#### 3.Relationship between Trip Distance and Fare Amount & Impact of the Hour of the Day on Fare Amount
##### Scatter Plot: Distance vs Fare Amount
- **🔍 Observation**:
There’s a clear positive linear relationship — the longer the trip, the higher the fare.

- **💡 Insight**:
Fare is strongly driven by distance, which is expected. This validates pricing models and supports predictive fare estimation tools for riders and planners.

##### Boxplot: Hour of Day vs Fare Amount
- **🔍 Observation**:
Fare variation increases in the evening hours, with wider ranges and higher outliers — even though median fares stay stable.

- **💡 Insight**:
There is greater fare variability at night, likely due to surge pricing or longer rides. This insight can help Uber adjust availability, pricing, or driver incentives during peak hours.

<img width="1170" height="453" alt="feature3" src="https://github.com/user-attachments/assets/fe5f24b5-2ec6-42ae-9a89-18fd2c0d402d" />



---


### 4. 📊 Power BI Visualizations
A suite of compelling visuals brings the data to life, offering intuitive insights into Uber’s operational patterns.

#### 📏 Visual 1: Fare vs. Distance
- **Type**: Scatter Plot
- **Axis**: `distance`  
- **Values**: Count of `fare_amount`  
- **Insight**:Relationship between trip length and fare. Outliers could show flat-rate rides or errors.

<img width="435" height="238" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/1fbd797e-4d5d-4227-913e-9e702f1e5e8d" />

---

#### 💸 Visual 2: Average Fare by Hour
- **Type**: Line Chart  
- **Axis**: `pickup_hour`  
- **Values**: Average of `fare_amount`  
- **Insight**: Highlights fare fluctuations, informing dynamic pricing strategies.  

<img width="240" height="241" alt="average by hour" src="https://github.com/user-attachments/assets/56d69a7b-d9bc-4cb5-b309-bb79b18660a0" />

---

#### 📅 Visual 3: Fare Distribution by Day of Week
- **Type**: Clustered Column Chart  
- **Axis**: `pickup_dayofweek`  
- **Values**: `fare_amount`  
- **Insight**: Uncovers weekly fare trends, aiding operational planning.  

<img width="268" height="226" alt="amountby day" src="https://github.com/user-attachments/assets/e0999d18-4eae-4961-b5f3-dcfb5116a78b" />


---

#### 🗺️ Visual 4: Pickup Locations (Alternative)
- **Type**: Line and Stacked Column Chart (due to map unavailability)  
- **Insight**: Approximates geospatial distribution of rides for strategic market analysis.  

<img width="349" height="288" alt="map" src="https://github.com/user-attachments/assets/6201ffdc-ce42-48b5-b636-cd324aa8a153" />


---
#### 📆 Monthly Trend Line
- **Type**: Area Chart  
- **Axis**: `month`  
- **Values**: `fare_amount`  
- **Insight**: Uncovers monthly fare trends, aiding operational planning.  

<img width="293" height="275" alt="fareamountmont" src="https://github.com/user-attachments/assets/e75b2e1b-b559-4d23-9c9a-a7a07e89dfce" />



---

### 5. 🎨 Interactive Dashboard
- **Design**: Unified all visuals into a cohesive, interactive Power BI dashboard.  
- **Features**:  
  - Slicers for dynamic filtering by hour, day, and month.  
  - Polished chart titles, vibrant colors, and intuitive tooltips.  
- **Purpose**: Empowers stakeholders to explore data effortlessly and derive insights in real-time.  


<img width="842" height="465" alt="updated" src="https://github.com/user-attachments/assets/d3115c7f-2d5c-4313-a941-33b57983d2c4" />

---

## 📝 Final Report Structure
The comprehensive report encapsulates the project’s journey and findings:  
- **Introduction**: Contextualizes the project’s purpose and dataset.  
- **Methodology**: Details Python-based data cleaning and Power BI-driven analysis.  
- **Analysis**: Breaks down insights from each visual.  
- **Results**: Highlights key trends in fare behavior and ride patterns.  
- **Conclusion**: Summarizes findings and their implications.  
- **Recommendations**: Offers strategic suggestions, such as peak-hour optimizations and pricing adjustments.  



---

## 📬 Submission Checklist
- [x] **Power BI File**: `.pbix` file with interactive dashboard.  
- [x] **Datasets**: Cleaned and enhanced `uber_fares_enhanced.csv`.  
- [x] **Jupyter Notebook**: Python code for data processing.   
- [x] **README**: This beautifully crafted document.  
- [x] **Final Report**: Submitted as PDF or PowerPoint.  
- [x] **GitHub**: Public repository with link shared with the instructor.  

---

## ✅ Academic Integrity
This project is an original work, crafted through meticulous analysis and visualization of the Uber Fares Dataset. All insights stem from authentic exploration using Python and Power BI, ensuring academic rigor and integrity.

---


## ✨ Why This Project Shines
This project transforms raw data into a compelling narrative, blending technical precision with visual elegance. The interactive Power BI dashboard not only informs but inspires, offering stakeholders a clear lens into Uber’s operational dynamics. From cleaned data to actionable insights, every step reflects a commitment to excellence and innovation.

---

*Crafted with 💡 by MUGENI Cynthia*  
*Let’s drive data to new destinations!* 🚗💨
