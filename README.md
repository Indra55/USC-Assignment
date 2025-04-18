# Environmental Exposure Analysis for LA Schools

## Project Overview
This project analyzes air pollution and weather data to estimate environmental exposure for students in Los Angeles public schools from 2020 to 2024. By collecting and processing extensive datasets, we provide insights into how environmental factors may impact student health and well-being during school hours.

## Project Structure
The project is organized into four main components:

```
.
├── Part 1 Collect School Information/
│   ├── school_scrapping.ipynb     # Scripts for collecting LA school data
│   └── Data/                      # Outputs from school data collection
├── Part 2 Gather Pollution Data/
│   ├── usc.ipynb                  # Scripts for gathering air pollution data
│   ├── FilteredData1/             # Processed pollution data by date
│   └── Combined_Daily_Data.csv    # Consolidated pollution measurements
├── Part 3 Gather Weather Data/
│   ├── scrapper.ipynb             # Scripts for gathering weather data
│   └── data/                      # Processed weather data outputs
└── Analysis (Part 4&5)/
    ├── analysis.ipynb             # Analysis of school-day conditions and exposure
    ├── weather_data_hourly.csv    # Hourly weather data for analysis
    └── air_quality_data.csv       # Processed air quality data for analysis
```

## Project Components

### Part 1: School Information Collection
- Implemented in `school_scrapping.ipynb`
- Scrapes data for LA senior high schools, middle schools, and elementary schools from the California Department of Education directory
- Collects school names, addresses, zip codes, and geographical coordinates
- Filters schools within the Los Angeles area using a defined geographical polygon
- Outputs a CSV file with comprehensive school data

### Part 2: Pollution Data Collection
- Implemented in `usc.ipynb`
- Gathers historical pollution data from AirNow archives (2020-2024)
- Downloads hourly data files and extracts PM2.5 and PM10 measurements for LA area
- Filters data by relevant monitoring stations
- Processes and combines data into daily files
- Outputs both individual date files and a consolidated dataset

### Part 3: Weather Data Collection
- Implemented in `scrapper.ipynb`
- Collects weather information from NOLA/Weather Underground (2020-2024)
- Records daily weather type, temperature, and precipitation
- Processes data by date and organizes it for analysis
- Generates structured weather datasets for all relevant zip codes

### Part 4 & 5: Analysis and Exposure Estimation
- Implemented in `analysis.ipynb`
- Combines pollution and weather data with school information
- Calculates average pollution levels during school hours for different school types:
  - Elementary schools (typically 8:00 AM - 2:00 PM)
  - High schools (typically 8:00 AM - 3:00 PM)
- Classifies pollution levels according to EPA standards
- Analyzes time spent in each pollution category
- Determines cumulative exposure across the 5-year period
- Generates visualizations and summary statistics

## Air Quality Thresholds
The analysis uses EPA air quality thresholds to classify exposure:

### PM2.5 (µg/m³)
- Good: 0.0 – 12.0
- Moderate: 12.1 – 35.4
- Unhealthy for Sensitive Groups: 35.5 – 55.4
- Unhealthy: 55.5 – 150.4
- Very Unhealthy: 150.5 – 250.4
- Hazardous: 250.5+

### PM10 (µg/m³)
- Good: 0 – 54
- Moderate: 55 – 154
- Unhealthy for Sensitive Groups: 155 – 254
- Unhealthy: 255 – 354
- Very Unhealthy: 355 – 424
- Hazardous: 425+

## Data Sources
- School information: California Department of Education School Directory
- Pollution data: AirNow historical archives (https://files.airnowtech.org/)
- Weather data: NOLA and Weather Underground historical records

## Key Findings
- Analysis demonstrates the variation in pollution exposure across different school locations
- Data reveals seasonal patterns in pollution levels affecting school environments
- Results highlight potential health implications of environmental exposure during school hours
- The project establishes a methodology for ongoing monitoring of environmental conditions at schools

## Setup and Running the Project
1. Clone this repository
2. Install required dependencies:
   ```
   pip install -r requirements.txt
   ```
   or create a virtual environment:
   ```
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```
3. Run the notebooks in sequential order:
   - First run `Part 1 Collect School Information/school_scrapping.ipynb`
   - Then run `Part 2 Gather Pollution Data/usc.ipynb`
   - Then run `Part 3 Gather Weather Data/scrapper.ipynb`
   - Finally run `Analysis (Part 4&5)/analysis.ipynb`

## Required Libraries
- beautifulsoup4
- requests
- pandas
- numpy
- matplotlib
- seaborn
- shapely
- jupyter

## Notes and Limitations
- The analysis uses data from the nearest monitoring stations, which may not perfectly represent conditions at each school
- Weather and pollution data timestamps are maintained separately
- Some data interpolation may be required for missing values
- The geographical boundaries for LA are approximated using a polygon 