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

## Power BI Dashboard

The report (`CTA_Forecast_Dashboard.pbix`) is a **6-page dashboard**: Overview, Live Forecast, Stations, History, Analytics, and Reports. Every page shares a common slicer set (Station, Day Category, Year) so filtering carries across the story.

### Page 1 — Overview
**KPI Cards**
- **Total Stations** — Count of stations included in the forecast (`CountNonNull(forecast_report.Station ID)`)
- **Total Estimated Passengers** — Sum of estimated passengers for the selected date (`Sum(forecast_report.Estimated Passengers)`)
- **Total Forecasted Crowd** — Sum of model-predicted ridership (`Sum(final_forecast_results.Forecasted Crowd)`)
- **Total Actual Passengers** — Sum of historical actual ridership (`Sum(final_forecast_results.Actual Passengers)`)
- **Day Category** — Day type of the predicted date (Weekday / Saturday / Sunday-Holiday)

**Charts and Visuals**
- **Area Chart — "Historical Ridership vs Model Prediction Accuracy"**: Actual Passengers vs Forecasted Crowd over time (2001–2019)
- **Map — "Geographic Station Distribution"**: All stations plotted, bubble size = Estimated Passengers, tooltip shows station count
- **Bar Chart — "Top 10 Stations by All-Time Ridership"**: Top 10 stations by total historical rides *(this is a clustered bar chart, not a table)*
- **Gauge — "System Load"**: Total Estimated Passengers vs the historical average ride target
- **Scatter Chart — "Actual vs Predicted"**: Actual Passengers (X) vs Forecasted Crowd (Y) per station, colored by Day Name
- **Donut Chart — "Ridership by Day Category"**: Average rides split across Weekday / Saturday / Sunday-Holiday

**Table**
- **"Detailed Forecast by Station"** — Station Name and Estimated Passengers for the predicted date

**Slicer**
- **Station Navigator** — filters all visuals by station

### Page 2 — Live Forecast
- **KPI Cards**: Total Forecasted, Busiest Station, Quietest Station, Stations Covered
- **Table — "Estimated Passengers per Station — Full Ranking"**: Station Name, Station ID, Estimated Passengers, and an in-cell Ridership Bar (data bar visual)

### Page 3 — Stations
- **KPI Cards**: Actual Passengers, Dynamic Peak Year, Forecasted Crowd, vs Network Average
- **Column Chart — "Ridership by Day of Week"**: Average rides per day, Monday–Sunday
- **Area Chart — "Year-over-Year Trend"**: Actual Passengers by year, with a peak-year marker
- **100% Stacked Bar — "Station vs Network Average Comparison"**: Selected station's rides vs the network average

### Page 4 — History
- **Area Chart — "Full Historical Ridership vs Forecast Accuracy — 2001 to 2019"**: Forecasted Crowd vs Actual Passengers across the full history
- **Pivot Table — "Monthly Ridership Heatmap"**: Years × months, values = Actual Passengers
- **Column Chart — "Year-over-Year Comparison"**: Forecasted Crowd by year
- **Area Chart — "Seasonal Pattern"**: Average rides per day by month

### Page 5 — Analytics
- **Scatter Chart — "Actual vs Predicted Accuracy - All Stations"**: same X/Y/color scheme as the Overview scatter, dedicated full-page view
- **Donut Chart — "Ridership by Day Category"**
- **Gauge — "System Load"**: Estimated Passengers vs Actual Passengers target
- **Table — "Station-Level Analytics — Accuracy & Performance Metrics"**: Actual vs Forecasted, Difference, and Accuracy % per station

### Page 6 — Reports
- **Table — "Complete Output Files Summary"**: File Name, Type, Row Count, Source, Status for each exported dataset
- **KPI Cards**: Final Forecast Results (rows exported), Forecast Report (stations · selected date), Top 10 Stations (busiest all-time), Avg Rides by Day Type (categories analyzed), Model Performance (overall accuracy), Database Summary

## How to Run
1. Open VS Code in the project folder
2. Ensure PostgreSQL is running
3. Run all cells in `Crowding_Forecast_Model.ipynb`
4. Enter prediction date when prompted
5. Open Power BI → click Refresh

## Author
**Mohamed Sathik Z** 
© 2026
