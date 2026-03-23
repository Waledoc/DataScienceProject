# Weather, Holidays, and Electricity Dynamics in Germany

This project analyzes how weather conditions, public holidays, and regional structures influence electricity consumption, electricity generation, and electricity prices in Germany between 2022 and 2025.

## Main Research Question

**To what extent do weather conditions and public holidays influence electricity consumption and electricity generation in Germany?**

## Sub-Research Questions

### 1. Public Holidays & Electricity Consumption (Germany-wide)
Do public holidays and school holidays in Germany show a measurable difference in daily electricity consumption compared to regular working days when analyzing Germany as a whole?

### 2. Seasonal Patterns in Electricity Consumption
How does electricity consumption vary across seasons in Germany, and how does this relate to seasonal weather conditions?

### 3. Weather Influence on Renewable Generation
How strongly do weather conditions (especially wind speed and sunshine / solar radiation) explain daily electricity generation from wind and photovoltaic (PV) in Germany?

### 4. Generation Mix during High Renewable Output
How does Germany’s electricity generation mix change on days with high renewable output (wind and PV), and which conventional sources (lignite, hard coal, gas) decrease the most?

### 5. Regional Differences in Electricity Consumption
How does electricity consumption differ between Germany’s TSO control areas (50Hertz, Amprion, TenneT, TransnetBW), and which factors may explain these regional differences?

### 6. Correlation between Electricity Consumption and Generation in TSO Regions
To what extent is electricity consumption correlated with electricity generation within Germany’s TSO control areas, and are there observable relationships between regional demand and regional electricity production?

### 7. Renewable Generation and Electricity Prices
How are electricity prices related to renewable electricity generation levels, and do high renewable generation periods correspond to lower electricity prices in Germany?

## Project Overview

This project combines energy market data, weather data, and holiday information to examine Germany-wide and regional electricity patterns. The analysis is based on public electricity and market data, historical weather data, and holiday calendars.

The regional analysis focuses on the four German TSO control areas:

- 50Hertz
- Amprion
- TenneT
- TransnetBW

This is important because electricity data in Germany is structured by transmission system zones rather than by political regions such as federal states or cities.

## Data Sources

The project uses the following data sources:

- **SMARD API** for electricity generation, electricity consumption, and electricity price data
- **Open-Meteo API** for historical weather data
- **Public holiday and school holiday data** for calendar-based analysis

### Main Variables

Examples of variables used in this project include:

- electricity consumption / net load
- electricity generation by source type
- renewable generation from wind onshore, wind offshore, and photovoltaics
- electricity prices
- wind speed
- sunshine duration / solar-related weather indicators
- temperature
- precipitation
- public holidays and school holidays
- date and TSO region

### Time Period

The project covers the period **2022 to 2025**.

## Data Pipeline

The project follows a structured workflow from raw data collection to final website presentation.

### 1. Data Collection
Data was fetched from public APIs and additional holiday sources, then stored locally for further processing.

### 2. Data Cleaning and Preprocessing
The raw data was cleaned and standardized before analysis. This included:
- converting timestamps into a consistent datetime format,
- normalizing time zones,
- selecting relevant categories and variables,
- and handling missing or inconsistent values where necessary.

### 3. Temporal Harmonization
Because the original datasets came in different time resolutions such as quarter-hourly, hourly, and daily values, all relevant datasets were converted to a **common daily level** so they could be compared consistently.

### 4. Data Merging
The processed datasets were merged by **date** and, where needed, by **TSO zone**, resulting in analysis-ready datasets for the individual research questions.

### 5. Variable Selection
Since electricity generation consists of multiple source types, relevant generation categories first had to be identified from the available API filters. Depending on the research question, the appropriate source types were selected.

For the renewable generation analysis, the project focused especially on:
- Wind Onshore
- Wind Offshore
- Photovoltaics (PV)

These were matched with suitable weather variables:
- wind speed for wind generation,
- sunshine duration for PV generation.

### 6. Analysis and Visualization
The project uses descriptive statistics, correlation analysis, and visualizations such as scatterplots, line charts, bar charts, and boxplots.

The visualizations were created in Python and exported as **HTML files**. These exported HTML visualizations were then integrated into the website.

## Repository Structure

Example structure of the repository:

```text
project-root/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── scripts/
│   ├── Frage1.py
│   ├── Frage2.py
│   ├── Frage3.py
│   ├── Frage4.py
│   ├── Frage5.py
│   ├── Frage6.py
│   └── Frage7.py
│
├── website/
│   ├── index.html
│   ├── style.css
│   ├── script.js
│   └── assets/
│
├── output/
│   ├── charts/
│   └── figures/
│
├── requirements.txt
└── README.md
