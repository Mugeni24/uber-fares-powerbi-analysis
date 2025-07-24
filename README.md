# 🌟 Uber Fares Dataset Analysis with Power BI

**Course:** Introduction to Big Data Analytics – INSY 8413  
**Instructor:** Eric Maniraguha ([📧 eric.maniraguha@auca.ac.rw](mailto:eric.maniraguha@auca.ac.rw))  
**Group:** B  
**Tool:** Power BI Desktop  
**Dataset Source:** [Uber Fares Dataset](https://www.kaggle.com/datasets/yasserh/uber-fares-dataset) (Kaggle)  
**Student Name:** MUGENI Cynthia  
**Student ID:** 26600  
**GitHub Repository:** [Explore the Code](https://github.com/your-username/uber-fares-analysis)

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

![Data Cleaning](https://github.com/user-attachments/assets/82c4370d-fac7-46c7-adf6-78286f2669bf)

---

### 3. 🧠 Feature Engineering
- **New Features**: Extracted `pickup_hour`, `pickup_day`, `pickup_month`, and `pickup_dayofweek` for temporal analysis.  
- **Distance Calculation**: Computed `trip_distance_km` using the haversine formula for precise geospatial insights.  
- **Output**: Exported the enriched dataset as `uber_enhanced.csv`.  

![Feature Engineering](screenshots/feature_engineering.png)

---

### 4. 📊 Power BI Visualizations
A suite of compelling visuals brings the data to life, offering intuitive insights into Uber’s operational patterns.

#### 🌅 Visual 1: Rides by Hour of Day
- **Type**: Clustered Column Chart  
- **Axis**: `pickup_hour`  
- **Values**: Count of `fare_amount`  
- **Insight**: Reveals peak ride times, guiding demand-based resource allocation.  

![Rides by Hour](https://github.com/user-attachments/assets/f6075861-3664-483f-8b66-d2275344cdbc)

---

#### 💸 Visual 2: Average Fare by Hour
- **Type**: Clustered Column Chart  
- **Axis**: `pickup_hour`  
- **Values**: Average of `fare_amount`  
- **Insight**: Highlights fare fluctuations, informing dynamic pricing strategies.  

![Average Fare by Hour](https://github.com/user-attachments/assets/9bcd40f4-3cc5-4cb6-acc6-9472b11bfbbb)

---

#### 📅 Visual 3: Fare Distribution by Day of Week
- **Type**: Clustered Bar Chart  
- **Axis**: `pickup_dayofweek`  
- **Values**: `fare_amount`  
- **Insight**: Uncovers weekly fare trends, aiding operational planning.  

![Fare by Day](https://github.com/user-attachments/assets/7d6e032b-ef46-4305-a925-19c1e8ea5667)

---

#### 📍 Visual 4: Fare vs. Trip Distance
- **Type**: Scatter Plot  
- **X-Axis**: `trip_distance_km`  
- **Y-Axis**: `fare_amount`  
- **Details**: Optional `passenger_count` for deeper segmentation.  
- **Insight**: Visualizes the relationship between distance and fare, exposing pricing patterns.  

![Fare vs Distance](https://github.com/user-attachments/assets/6ae1c44a-bbe4-4f29-91b5-b0e90b800ea7)

---

#### 🗺️ Visual 5: Pickup Locations (Alternative)
- **Type**: Line and Stacked Column Chart (due to map unavailability)  
- **Insight**: Approximates geospatial distribution of rides for strategic market analysis.  

![Pickup Locations](https://github.com/user-attachments/assets/bb393e92-d274-4671-bfbc-90b0de70e302)

---

### 5. 🎨 Interactive Dashboard
- **Design**: Unified all visuals into a cohesive, interactive Power BI dashboard.  
- **Features**:  
  - Slicers for dynamic filtering by hour, day, and month.  
  - Polished chart titles, vibrant colors, and intuitive tooltips.  
- **Purpose**: Empowers stakeholders to explore data effortlessly and derive insights in real-time.  

![Dashboard](https://github.com/user-attachments/assets/2c28a603-b583-45d1-87a0-8872be647ffc)

---

## 📝 Final Report Structure
The comprehensive report encapsulates the project’s journey and findings:  
- **Introduction**: Contextualizes the project’s purpose and dataset.  
- **Methodology**: Details Python-based data cleaning and Power BI-driven analysis.  
- **Analysis**: Breaks down insights from each visual.  
- **Results**: Highlights key trends in fare behavior and ride patterns.  
- **Conclusion**: Summarizes findings and their implications.  
- **Recommendations**: Offers strategic suggestions, such as peak-hour optimizations and pricing adjustments.  

📄 [View Report](Report.pdf) | [View Presentation](Report.pptx)

---

## 📬 Submission Checklist
- [x] **Power BI File**: `.pbix` file with interactive dashboard.  
- [x] **Datasets**: Cleaned and enhanced `uber_enhanced.csv`.  
- [x] **Jupyter Notebook**: Python code for data processing.  
- [x] **Screenshots**: Visuals stored in `visuals/` or `screenshots/` folder.  
- [x] **README**: This beautifully crafted document.  
- [x] **Final Report**: Submitted as PDF or PowerPoint.  
- [x] **GitHub**: Public repository with link shared with the instructor.  

---

## ✅ Academic Integrity
This project is an original work, crafted through meticulous analysis and visualization of the Uber Fares Dataset. All insights stem from authentic exploration using Python and Power BI, ensuring academic rigor and integrity.

---

## 🌐 Explore the Project
Dive into the code, visuals, and insights:  
👉 **GitHub Repository**: [Uber Fares Analysis](https://github.com/your-username/uber-fares-analysis)  
👉 **Dataset**: [Kaggle Uber Fares Dataset](https://www.kaggle.com/datasets/yasserh/uber-fares-dataset)  

---

## ✨ Why This Project Shines
This project transforms raw data into a compelling narrative, blending technical precision with visual elegance. The interactive Power BI dashboard not only informs but inspires, offering stakeholders a clear lens into Uber’s operational dynamics. From cleaned data to actionable insights, every step reflects a commitment to excellence and innovation.

---

*Crafted with 💡 by MUGENI Cynthia*  
*Let’s drive data to new destinations!* 🚗💨
