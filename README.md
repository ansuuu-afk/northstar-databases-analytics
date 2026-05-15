# NorthStar Urban Mobility and Logistics
## Databases and Analytics Assignment

**Student:** Mohammed | **Student ID:** 3214  
**Module:** Databases and Analytics | **University of West London**  
**Module Leader:** Shidrokh Goudarzi  

---

## Overview

This repository contains the full analytical solution for the NorthStar Urban Mobility and Logistics case study, completed as part of the Databases and Analytics module at the University of West London.

NorthStar is a large regional transport and logistics organisation that has grown rapidly through mergers across multiple UK cities. Despite rising demand, the company is experiencing declining efficiency — deliveries are failing, complaints are rising, and management cannot explain why because the data needed to answer that question is scattered across disconnected systems.

This project connects those fragmented datasets for the first time using four technologies: SQL in R, R analytics and visualisation, Python data processing, and MongoDB Atlas NoSQL database design.

---

## Repository Structure
northstar-databases-analytics/
│
├── Colab Notebooks/
│   ├── Notebook1_SQL_in_R.ipynb           # SQL queries using sqldf in R
│   ├── Notebook2_R_Analytics.ipynb        # Statistical analysis and visualisation in R
│   ├── Notebook3_Python_Processing.ipynb  # Data cleaning, feature engineering, anomaly detection
│   ├── Notebook4_MongoDB_Design.ipynb     # MongoDB Atlas database design and CRUD operations
│   └── Notebook5_Query_Optimisation.ipynb # Compound indexes and explain() plan analysis
│
├── northstar_dataset/
│   ├── customers.csv
│   ├── drivers.csv
│   ├── deliveries.csv
│   ├── incidents.csv
│   ├── complaints.csv
│   ├── hubs.csv
│   ├── orders.csv
│   ├── vehicles.csv
│   └── app_events.csv
│
└── README.md

---

## Dataset

The NorthStar dataset contains 9 CSV files representing different parts of the business:

| File | Records | Description |
|------|---------|-------------|
| customers.csv | 650 | Customer profiles, zones, loyalty scores |
| orders.csv | 1,250 | Service orders, revenue, priority levels |
| deliveries.csv | 950 | Delivery attempts, status, driver and vehicle assignments |
| drivers.csv | 170 | Driver profiles, training scores, ratings |
| vehicles.csv | 120 | Fleet data, battery health, maintenance status |
| incidents.csv | 280 | Incidents during deliveries, severity levels |
| complaints.csv | 320 | Customer complaints, resolution times, compensation |
| hubs.csv | 8 | Operational hub details and zones |
| app_events.csv | 640 | Mobile platform events, API latency, success rates |

---

## Notebooks

### Notebook 1 — SQL in R
- Runs SQL queries directly over R data frames using the `sqldf` package
- Cleans inconsistent zone names before all queries
- 7 queries covering: hub failure rates, repeat failure customers, driver override analysis, service type financials, incident-to-failure links, zone complaint rates, vehicle risk
- **Runtime:** R kernel

### Notebook 2 — R Analytics and Visualisation
- Statistical analysis and visualisation using `ggplot2`, `dplyr`, `corrplot`
- 8 charts: zone outcomes stacked bar, loyalty vs complaints scatter, driver training scatter, incident heatmap, battery health boxplot, complaint resolution boxplot, monthly time series, Pearson correlation matrix
- **Runtime:** R kernel

### Notebook 3 — Python Data Processing
- Full data pipeline using `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`
- Zone normalisation, missing value analysis, median imputation
- Feature engineering: delivery duration, temporal anomaly detection, cost per km, vehicle risk scores
- Identifies 64 delivery records with impossible timestamps (completed before dispatch)
- Multi-factor failure analysis, complaint dashboard, integrated hub risk bubble chart
- **Runtime:** Python 3

### Notebook 4 — MongoDB Atlas Design
- Designs and builds `northstar_db` on MongoDB Atlas using `PyMongo`
- 4 collections: `customers` (embedded complaint history), `deliveries` (embedded incident events), `driver_profiles` (embedded performance stats), `app_events` (session-grouped events)
- Full CRUD operations with realistic operational scenarios
- 3 aggregation pipelines: zone complaint summary, hub failure by service type, high-risk driver identification
- **Runtime:** Python 3

### Notebook 5 — Query Optimisation
- Creates 4 compound indexes using the ESR rule (Equality → Sort → Range)
- Before/after `explain('executionStats')` showing COLLSCAN → IXSCAN transition
- Performance benchmarking with `benchmark_query()` helper function
- **Runtime:** Python 3 | **Requires:** Notebook 4 to be run first

---

## How to Run

### Prerequisites
- Google account (for Google Colab)
- Free MongoDB Atlas account at [mongodb.com/atlas](https://mongodb.com/atlas)

### Running R Notebooks (1 and 2)
1. Open [Google Colab](https://colab.research.google.com)
2. File → Upload notebook → select the notebook file
3. Runtime → Change runtime type → select **R**
4. Run all cells: Runtime → Run all (Ctrl + F9)

> Data loads automatically from this GitHub repository — no file uploads needed.

### Running Python Notebooks (3, 4, 5)
1. Open [Google Colab](https://colab.research.google.com)
2. File → Upload notebook → select the notebook file
3. Keep default **Python 3** runtime
4. Run all cells: Runtime → Run all (Ctrl + F9)

> Data loads automatically from this GitHub repository — no file uploads needed.

### MongoDB Setup (Notebooks 4 and 5)
1. Create a free account at [mongodb.com/atlas](https://mongodb.com/atlas)
2. Create a free **M0** cluster
3. Security → Database Access → Add a user with a password
4. Security → Network Access → Add IP → Allow Access from Anywhere (`0.0.0.0/0`)
5. Connect → Drivers → Python → Copy connection string
6. In Notebooks 4 and 5, replace:
```python
MONGO_URI = "YOUR_CONNECTION_STRING_HERE"
```
with your actual connection string.

---

## Key Findings

After connecting all nine datasets for the first time, five core operational problems were identified:

1. **Central zone hubs fail at twice the rate of East/South hubs** — Midtown Relay and Central Core both sit at ~20% failure rate vs ~9% at East Dock
2. **64 delivery records have impossible timestamps** — completion recorded before dispatch, directly causing the cross-system mismatch described by management
3. **Business service contracts have the highest failure rate (~20%)** despite being premium tier — SLA penalties are likely eroding margins
4. **58% of deliveries involve route overrides** — override rate positively correlates with failure rate
5. **Active vehicles operating below 60% battery threshold** are not being flagged for maintenance before deployment

---

## Technologies Used

| Technology | Purpose | Notebook |
|-----------|---------|----------|
| R + sqldf | SQL queries over structured data | Notebook 1 |
| R + ggplot2 + dplyr | Statistical analysis and charts | Notebook 2 |
| Python + Pandas + Seaborn | Data cleaning, anomaly detection, visualisation | Notebook 3 |
| MongoDB Atlas + PyMongo | NoSQL document database design and CRUD | Notebook 4 |
| MongoDB compound indexes | Query optimisation and explain() analysis | Notebook 5 |

---

## Module Information

- **Module:** Databases and Analytics
- **Module Codes:** CP60056E, CP6CS56E, CP6HA50E
- **Institution:** University of West London — School of Computing and Engineering
- **Module Leader:** Shidrokh Goudarzi
- **Submission:** 12 May 2026
