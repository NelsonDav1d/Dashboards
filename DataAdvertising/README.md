# Advertising Data Generation

## Introduction

This repository contains resources for creating a dashboard for a synthetic advertising scenario.

The script in Python folder generates synthetic advertising data and stores it in a CSV file. The data simulates a marketing campaign scenario with randomly generated data.

Feel free to utilize it for practice purposes.

## Usage

1. Open the Jupyter Notebook or Python script containing the code.
2. Execute the code to generate synthetic advertising data.
3. The generated data will be stored in a CSV file located at the specified file path.

## Data Generation

The script generates advertising data with the following attributes:
- Date
- Campaign Name
- Total Unique Users
- Total Visitors Completed
- Impressions
- Number of Clicks
- Number of Conversions
- Advertising Channel
- Device Type
- OS (Operating System)
- Browser
- Geographic Location
- Start Time of Session
- End Time of Session
- Platform
- Total Cost

## Measures and Table in Power BI

For this exercise, the following measures have been added in the Power BI model:
- **Average Time of Session**: Calculates the average duration of sessions.
- **Click Through Rate (CTR)**: Calculates the ratio of clicks to impressions.
- **Cost per Click (CPC)**: Calculates the cost per click.
- **Total Cost Campaign**: Calculates the total cost per campaign.

Additionally, a new table has been added to the Power BI model:
- **Location**: Contains the country, geographic location, and province.
- The country column has the value "Canada" for all rows, the geographic location is a distinct field from 'DataTest', and the province column is manually added based on city names.

## Power BI Measures and Columns

### Measures:
```DAX
Average Time of Session = 
    AVERAGEX(
        'DataTest',
        'DataTest'[End Time of Session] - 'DataTest'[Start Time of Session]
    )
```

```DAX
Click Through Rate = 
    DIVIDE(SUM('DataTest'[Number of Clicks]), SUM('DataTest'[Impressions]), 0)
```
```DAX
Cost per Click = 
    DIVIDE(SUM(DataTest[Total Cost]), SUM(DataTest[Number of Clicks]), 0)
```
```DAX
Total Cost Campaign = 
    SUM(DataTest[Total Cost])
```
Columns:
Country: Add a new column named country with the value "Canada".
Province: Manually add a new column named province based on city names.
```DAX
Location Table:
Location = 
    SUMMARIZE(
        'DataTest',
        'DataTest'[Country],
        'DataTest'[Geographic Location]
    )
```
Add another column for location named Province.
```DAX
Province = 
    SWITCH(
        'Location'[Geographic Location],
        "Ottawa", "Ontario",
        "Vancouver", "British Columbia",
        "Quebec City", "Quebec",
        "London", "Ontario",
        "Montreal", "Quebec",
        "Calgary", "Alberta",
        "Toronto", "Ontario",
        "Edmonton", "Alberta",
        "Hamilton", "Ontario",
        "Winnipeg", "Manitoba",
        BLANK()
    )
```
Feel free to adjust the script or measures to better fit your needs.

Nelson Aguilera.
email: nelson.aguilera.guevara@gmail.com
