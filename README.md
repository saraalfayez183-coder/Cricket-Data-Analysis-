# Cricket Performance Analysis Dashboard (ESPNcricinfo Statsguru)



## 📋 Project Overview
This Power BI project provides a comprehensive 360-degree analysis of cricket player performances across **Batting**, **Bowling**, and **Fielding**. By transforming raw data into statistical insights, this dashboard helps teams and analysts identify top performers and evaluate consistency through advanced deviation metrics and rankings.

## 🌐 Data Source
The data for this project was meticulously sourced from **[Statsguru | Searchable Cricket Statistics database | ESPNcricinfo.com](https://stats.espncricinfo.com/ci/engine/stats/index.html)**. The dataset includes player career stats, strike rates, and detailed fielding performances.

## 🎯 Problem Statement
Evaluating cricket players across different eras and formats is complex without statistical context. This project solves this by:
- Measuring how much a player's scoring varies from the global average using **Deviation** metrics.
- Categorizing players by **Strike Rate** using a lookup logic.
- Ranking players based on their impact and efficiency (Power Rankings).

## 🛠️ Tools & Technologies Used
- **Power BI Desktop**: Dashboard creation and UI design.
- **Power Query**: Data cleaning, handling null values, and ETL.
- **DAX (Data Analysis Expressions)**: Advanced statistical modeling and ranking.
- **Theme**: CY25SU11 professional layout.

## 📊 DAX Calculations (Batting Analysis)
The following specialized DAX expressions were used to calculate player impact and performance consistency:

### 1. Performance Deviation
Calculates how much a player's runs vary from the overall population average.


[Image of a Bell Curve distribution chart showing Standard Deviation in statistics]

`Deviation = Batting[Runs] - AVERAGE(Batting[Runs])`

### 2. Absolute Deviation
Used to measure the magnitude of performance difference, regardless of being above or below average.
`Absolute Deviation = ABS(Batting[Deviation])`

### 3. Squared Deviation
Used to calculate variance and identify performance volatility (Standard Deviation building blocks).
`Squared Deviation = POWER(Batting[Deviation], 2)`

### 4. Strike Rate Categorization
Dynamically classifies players by linking the Batting table to a reference 'Strike Rate Table' without a physical relationship.
`Category = LOOKUPVALUE('Strike Rate Table'[Category], 'Strike Rate Table'[Strike Rate], Batting[SR])`

### 5. Power Ranking
A dense ranking system that assigns a position to players based on their Strike Rate (SR).
`Rank = RANKX(ALL(Batting), Batting[SR], , DESC, Dense)`

### 6. Bowling Economy
Standard measure to evaluate bowling efficiency.
`Bowling Economy = DIVIDE(SUM(Bowling[Runs_Conceded]), SUM(Bowling[Overs]))`

## 🚀 Steps Followed 

### Phase 1: Data Preparation
* **Data Extraction**: Scraped/Extracted data from ESPNcricinfo Statsguru.
* **Data Cleaning**: Used **Column Quality** and **Column Profile** to identify and fix errors. Cleaned specialized columns like `BBI` and `Span`.
* **Modeling**: Created a logic to categorize players using the `LOOKUPVALUE` function.

### Phase 2: Design & Interactivity
* **Slicers**: Added filters for **Player**, **Career Span**, and **Matches Played**.
* **Visuals**: Card visuals for KPIs, Bar charts for rankings, and custom icons for UI/UX.

## 💡 Key Insights

* **Batting Performance**: The `Deviation` analysis reveals players significantly outperforming the global mean.
* **Reliability**: A lower `Absolute Deviation` indicates a consistent run-scorer.
* **Bowling Efficiency**: Highlights bowlers with the best Wicket-to-Economy ratios.

---
**Project created by [Sara Alfayez ]**
