# 🚕 Robotaxi Service Gap Analysis – New York State

> **Identifying transit deserts and optimizing autonomous vehicle deployment across all NYC census tracts**

---

## 📌 Project Overview

This project addresses a critical urban mobility challenge: millions of residents in New York State — particularly those with ambulatory difficulties — live in neighborhoods severely underserved by existing public transit. As robotaxi services emerge as a viable transportation alternative, the question becomes: **where should they be deployed first to maximize both business ROI and social impact?**

Our team is building a six-phase end-to-end data science pipeline that leverages NYC census data, TLC trip records, MTA transit station locations, and weather data to identify service gaps, forecast ride demand, and compute Social Return on Investment (SROI) for robotaxi deployment.

---

## 🎯 Objectives

- Segment NYC neighborhoods into distinct market personas based on demographic and transit access profiles
- Classify census tracts as **Service Deserts** or **Well Served** using machine learning
- Pinpoint optimal depot and charging station locations through geospatial analysis
- Forecast ride demand volumes using XGBoost regression
- Quantify the financial ROI and social impact of robotaxi deployment in high-need areas
- Conduct sensitivity analysis to assess pricing strategies across different income segments

---

## 🗂️ Project Phases

| Phase | Title | Goal |
|-------|-------|------|
| **Phase 1** | Data Collection & Preparation | Aggregate and clean NYC Master dataset (census tracts, demographics, transit) |
| **Phase 2** | Market Segmentation | K-Means clustering to group neighborhoods into 4–5 market personas |
| **Phase 3** | Target Classification | Random Forest / Logistic Regression to label Service Deserts vs. Well Served |
| **Phase 4** | Geospatial Strategy | Heatmaps to identify optimal depot/charging station locations |
| **Phase 5** | Predictive Forecasting | XGBoost regression to forecast ride volumes and demand spikes |
| **Phase 6** | Strategy & Social ROI | ROI calculation, sensitivity analysis, and social impact quantification |

---

## 🛠️ Tech Stack

| Category | Tools |
|----------|-------|
| **Language** | Python |
| **Machine Learning** | Scikit-learn (K-Means, Random Forest, Logistic Regression), XGBoost |
| **Geospatial** | GeoPandas, Folium, Shapely |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn, Folium (heatmaps) |
| **Data Sources** | NYC TLC Trip Records, NYC Master Census Dataset, MTA Transit Station Locations, NOAA Weather Data |

---

## 📊 Data Sources

- **NYC Master Census Dataset** – Demographics, vehicle ownership %, service occupations %, total disability %, transit use %
- **NYC TLC Trip Records** – Total pickups per census tract per hour (Yellow & Green cab data)
- **MTA Subway/Bus Station Locations** – Lat/Long coordinates for every subway and bus station
- **Weather Data** – Temperature, precipitation, weather conditions for demand spike modeling
- **Median Income Data** – For sensitivity/pricing analysis

---

## 🔬 Methodology

### Phase 2 – Market Segmentation (K-Means Clustering)
- Applied K-Means clustering to group all NYC census tracts into 4–5 distinct market types
- Features used: vehicle ownership %, service occupation %, total disability %, transit usage %
- Output: Each census tract labeled with a "Persona" (e.g., Cluster A = late-night demand, Cluster B = wheelchair-accessible vehicle need)

### Phase 3 – Target Classification (Random Forest / Logistic Regression)
- Created binary target variable: `Is_Service_Desert` = 1 if (Need_Score is High AND Distance_to_Subway > 0.5 miles), else 0
- Trained Random Forest and Logistic Regression classifiers to predict service desert status
- Key features: demographic indicators, proximity to transit, vehicle ownership

### Phase 4 – Geospatial Strategy
- Merged census tract boundary geometries with demand scores
- Generated Folium heatmaps identifying neighborhoods where demand is high but subway access is low
- Output: Map of ideal first-deployment Depots and Charging Stations

### Phase 5 – Predictive Forecasting (XGBoost)
- Built XGBoost regression model using NYC TLC trip data (1-month sample)
- Time features engineered: `Hour_of_Day`, `Day_of_Week`, `Is_Holiday`
- Formula: `Daily Revenue = Expected Daily Trips × Avg Trip Length × Price per Mile`

### Phase 6 – ROI & Sensitivity Analysis
- **Revenue**: Estimated 5% of public transit users in High-Need tracts switching to robotaxi
- **Pricing Benchmark**: Current Uber/Lyft cost per mile
- **Variable Costs**: Electricity, insurance, fleet management
- **Fixed Costs**: Vehicle price (~$30K per unit)
- **ROI Formula**: `ROI% = (Revenue per Mile - Cost per Mile) / Cost per Mile`
- **Social ROI**: `No. of Disabled Residents in High-Need Tracts × Estimated Yearly Trips Provided`
- **Sensitivity Analysis**: Median income from NY Master data to assess willingness to pay across income tiers

---

## 📈 Key Results *(In Progress)*

- Identified **X transit desert zones** across NYC with high demand and low subway access
- Projected daily ride volume of **X rides/day** in top-priority deployment zones
- Estimated ROI of **X%** for initial fleet deployment in high-need tracts
- Social ROI: Potential to serve **X+ ambulatory-difficulty residents** with improved mobility access

---

## 📁 Repository Structure

```
robotaxi-service-gap-nyc/
│
├── data/
│   ├── raw/                    # Raw NYC TLC, Census, MTA data
│   └── processed/              # Cleaned and merged datasets
│
├── notebooks/
│   ├── 01_data_preparation.ipynb
│   ├── 02_market_segmentation.ipynb
│   ├── 03_target_classification.ipynb
│   ├── 04_geospatial_strategy.ipynb
│   ├── 05_predictive_forecasting.ipynb
│   └── 06_roi_sensitivity_analysis.ipynb
│
├── src/
│   ├── clustering.py
│   ├── classification.py
│   ├── geospatial.py
│   ├── forecasting.py
│   └── roi_calculator.py
│
├── outputs/
│   ├── maps/                   # Folium heatmaps
│   └── figures/                # Charts and visualizations
│
├── requirements.txt
└── README.md
```

---

## 👥 Team

- **Prateeksha Mehta** – Data Pipeline, Clustering, ROI Modeling, Sensitivity Analysis
- Team collaboration across all 6 phases

---

## 📬 Contact

**Prateeksha Mehta** | pratu2930@gmail.com | [LinkedIn](https://linkedin.com/in/prateeksha29)
