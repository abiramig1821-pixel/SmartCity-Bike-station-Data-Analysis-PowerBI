# 🚲 Smart City Bike Sharing Data Analysis

## 📑 Table of Contents
* [Project Overview](#-project-overview)
* [Data Source](#-data-sources)
* [Data Modeling & DAX Measures](#-Data-Modeling-DAX-Measures)
* [Interactive Dashboard Ecosysytem](#-Interactive-Dashbaord-Ecosystem)
* [Key Insights](#-key-insights)
* [Strategic Recommendations](#-Strategic-Recommendations)
* [Project conclusion](#-Project-Conclusion)
* [Author](#-Author)

## 📌 Project Overview

An end-to-end data transformation, modeling, and visualization system built entirely within Power BI. This project analyzes live, large-scale public bike-sharing data spanning 2022 to 2025 across multiple international smart cities. The pipeline converts raw data into tactical urban mobility insights across four distinct analytic frameworks: descriptive, diagnostic, predictive, and prescriptive.

## 🗃️ Data Sources

  •	**Core Technology:** Power BI (Power Query, DAX Engine, Desktop Data Modeling)

  • **Domain:** Smart Transportation & Urban Mobility Ecosystems.

## 📊 Analytical Framework & Problem Statement
**1. Descriptive Analytics (Current State)**

•	Tracking total functional bikes and empty parking spots across all networks.

•	Isolating the exact count of stations allowing direct on-terminal credit card checkout (banking).

**2. Diagnostic Analytics (Root Cause Analysis)**

•	Investigating structural station imbalances and evaluating whether "free minutes" bonus flags help self-regulate station equilibrium.

•	Mapping specific localized city failures to determine if inventory drops stem from physical dock shortages or closed/broken infrastructure.

**3. Predictive Analytics (Future State Modeling)**

•	Forecasting daily peak risk hours where busy downtown corridors run completely out of equipment.

•	Pre-identifying critical neighborhood bottlenecks prone to maximum parking shortages next month due to urban expansion.

**4. Prescriptive Analytics (Operational Action Plan)**

•	Generating live, high-priority dispatch loops for delivery truck routing (Top 10 drop-off vs. Top 10 collection sites).

•	Mapping strategic zones for new bonus station placement to incentivize organic rider rebalancing and minimize logistics costs.

## 🛠️ Data Pre-processing (Power Query)

The entire ingestion pipeline was automated cleanly inside Power Query Editor, completely bypassing any need for external spreadsheet processing tools:

•	Split compound address blocks containing prefixed numeric labels using custom string delimiters.

•	Cleaned and split the complex geographical Position grouping into independent Longitude and Latitude floating-point fields.

• Checked duplicates and resolved structural null blanks within raw text fields by writing standard "Unknown" default values.

## 📐 Data Modeling & DAX Measures

A centralized data model was established inside Power BI. Key custom business intelligence measures include:

```dax
Total Capacity = SUM('Data Table'[Bike Stands])

Station Count = COUNT('Data Table'[Station Name])

Station Fill Rate = DIVIDE(SUM('Data Table'[Available Bike Stands]), SUM('Data Table'[Bike Stands]), 0)

Closed Station = CALCULATE(SUM('Data Table'[Bike Stands]), 'Data Table'[Station status] = "CLOSED")

Open empty station = CALCULATE(SUM('Data Table'[Available Bike Stands]), 'Data Table'[Station status] = "OPEN")

Parking shortage Risk = DIVIDE(SUM('Data Table'[Available Bike Stands]), SUM('Data Table'[Bike Stands]), 0)

Truck Delivery Risk = ABS(SUM('Data Table'[Available Bikes]) - SUM('Data Table'[Available Bike Stands]))
```

## 🖥️ Interactive Dashboard Ecosystem

### 🛑 Dashboard 1: Operational Core & Dynamics


•	**KPI Metrics Block:** Multi-card indicators displaying system-wide Total Capacity (57K), Available Bikes (20K), and Available Bike Stands (32K) alongside automated payment terminal tracking (69 Credit Card Stations).

•	**Chronological Timeline:** A structured 24-hour line chart highlighting chronological available stands.

•	**Contract Health Breakdown:** Stacked horizontal bar chart tracking real-time asset distributions by contract city names.

•	**Incentive Scatter Evaluation:** A detailed distribution matrix graphing Available Bikes against Available Bike Stands, split completely by Bonus status to assess network equilibrium.


### ⚠️ Dashboard 2: Shortage Risk Projections


•	**Risk Ranking:** Ranked clustered bar chart pinpointing urban sectors exceeding boundaries with maximum 1.00 Parking Shortage Risk Scores.


### 🚚 Dashboard 3: Logistical Dispatch Toolkit


•	**Refill Tracking Grid:** Bottom-10 filtered checklist isolating empty hubs showing exactly 0 Available Bikes.

•	**Clearance Grid:** Top-10 target checklist isolating completely full docks at 1.00 Shortage Risk.

•	**Truck Delivery Matrix:** An operational table calculating absolute volumetric deviation (Truck Delivery Risk) by unique station names to schedule fleet drop-offs.


## 💡 Key Insights

•	**The Incentive Fallacy:** The current "Free Minutes" bonus system fails to balance the network. Scatter plotting maps both Bonus = True and Bonus = False stations sitting trapped at extreme boundaries (completely full or completely empty).

•	**Dual Shortage Dynamics:** Shortage root causes are split structurally by region. Toulouse, Valence, Seville, and Toyama run out of bikes because of high passenger demand and distribution gaps (~70% open empty docks). In contrast, Vilnius presents an infrastructure breakdown, failing entirely because 99.84% of its network sits deactivated in a closed station status.

•	**Predictive Rush Hour Timelines:** Stations follow a rigid daily risk sequence, facing massive bike depletion during late-night (1:00 AM) and late-evening (9:00 PM) social cycles, resetting supply during the morning commute (7:00 AM).

## 🚀 Strategic Recommendations

1.**Re-engineer the Bonus Incentive:** Restructure bonus rewards into dynamic, high-value visual alerts exclusively when a station touches the critical 0-bike or 0-dock boundary line.

2.**Infrastructure Overhaul (Vilnius):** Reallocate budget resources in Vilnius away from rebalancing trucks and entirely into technician field operations to repair the 99.84% closed hardware logjam.

3.**Smart Logistics Routing:** Deploy a high-priority loop routing drivers directly to the 10 completely empty stations (0 bikes) for drop-offs and the 10 overflowing hubs (1.00 risk) for inventory collection.

4.**Self-Healing Automation:** Target automated app promotions at maximum-risk hubs where the mathematical gap between available bikes and open docks (Truck Delivery Risk) is widest to replace expensive truck routes with organic rider actions.

## 🏁 Project Conclusion

The end-to-end data analysis was executed entirely within Power BI, proving its robust native power from raw data ingestion to advanced visual reporting. By building robust Power Query staging pipelines, modeling localized calculated dimensions, and deploying advanced DAX measures, this centralized ecosystem successfully cracked severe smart city micro-mobility imbalances without relying on any external spreadsheet transformation layers.

## Author
 ### Abirami Ganessan

