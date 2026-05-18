# Public Transportation Crowding Forecast
End-to-end public transportation crowding forecast project using Python, PostgreSQL, and Power BI. 
Includes data preprocessing, Random Forest model training per station, SQL business 
queries, estimated passenger prediction for any date, and an interactive dashboard 
to visualize ridership trends across 147 CTA stations.

## Project Overview
This project forecasts estimated passenger counts for 147 CTA transit stations 
using historical ridership data from 2001 to 2019. A Random Forest model is trained 
per station to predict daily crowd levels based on date features.

## Tools Used
- **Python** — Data preprocessing, feature engineering, model training
- **PostgreSQL** — Data storage and SQL analysis queries
- **Power BI** — Interactive dashboard for visualization
- **VS Code** — Single integrated development environment

## Dataset
- Source: CTA Ridership — L Station Entries Daily Totals
- Dataset Link: [Sample Dataset for Model](https://drive.google.com/uc?export=download&id=1M3m2O91hrxGsrYR0eDvSMLSS9cxggpcT)
- Records: 962,546 rows
- Stations: 147
- Date Range: 2001-01-01 to 2019-06-30
- Features: station_id, stationname, date, daytype, rides

## Project Structure

<img width="451" height="241" alt="image" src="https://github.com/user-attachments/assets/ded91051-a9f5-4ceb-81b2-1d0db56682ef" />


## Pipeline Flow

<img width="453" height="180" alt="image" src="https://github.com/user-attachments/assets/c13884d3-ed0b-4693-813c-9f10780b67c9" />


## Key Features
- Predicts estimated passengers for **every station** on any entered date
- Trains individual Random Forest model per station
- Sparse stations handled using historical average fallback
- 4 output files auto-saved and connected to Power BI

## SQL Queries
- Top 10 busiest stations by total ridership
- Average rides by day type (Weekday / Saturday / Sunday)

## Model Details
- Algorithm: Random Forest Regressor
- Trees: 20 per station
- Features: year, month, day, day_of_week, day_type_num
- Stations with sparse data: historical average used

## Power BI Dashboard Visuals

### KPI Cards
- **Total Stations** — Count of stations included in the forecast report
- **Total Forecasted Riders** — Sum of estimated passengers across all stations
- **Day Category** — Day type of the predicted date (Weekday / Saturday / Sunday)
- **Total Estimated Passengers** — Overall passenger load for the selected date

### Charts and Visuals
- **Area Chart** — Historical Ridership vs Model Prediction Accuracy
  - Shows Actual Passengers vs Forecasted Crowd over time from 2001 to 2019
  - X-axis: Date | Y-axis: Passenger Count

- **Donut Chart** — Ridership by Day Category
  - Breakdown of average rides across Weekday, Saturday and Sunday/Holiday

- **Scatter Chart** — Correlation: Actual vs Predicted Ridership
  - Plots Actual Passengers against Forecasted Crowd per station
  - Color coded by Day Name to show day-of-week patterns

- **Gauge Chart** — System Load vs Historical Average
  - Compares total estimated passengers for the predicted date
    against the overall historical average

- **Map Visual** — Geographic Distribution
  - Plots all 147 stations on a map
  - Bubble size represents estimated passengers per station

### Tables
- **Detailed Forecast by Station** — Station Name and Estimated Passengers
  for the predicted date across all stations

- **Historical Records: All-Time Busiest Stations** — Top 10 stations
  ranked by total all-time ridership

### Slicer
- **Station Navigator** — Filter all visuals by selecting a specific station

## How to Run
1. Open VS Code in the project folder
2. Ensure PostgreSQL is running
3. Run all cells in `Crowding_Forecast_Model.ipynb`
4. Enter prediction date when prompted
5. Open Power BI → click Refresh

## Author
**Mohamed Sathik Z** 
© 2026
