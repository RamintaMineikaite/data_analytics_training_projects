# Road Accident Analysis – Power BI Project
This project is part of my Data Analytics portfolio, focusing on building a comprehensive Road Accident Dashboard using Power BI. The dashboard presents actionable insights from accident data across 2021 and 2022, helping stakeholders understand trends, patterns, and key metrics for improved decision-making.

## Problem Statement
This dashboard helps government agencies, city planners, and public safety officials better understand the patterns and causes of road accidents. It provides insights into the total number of accidents and casualties, enabling stakeholders to identify high-risk areas, dangerous road types, and critical time periods when accidents are most likely to occur.

By breaking down casualties by accident severity, vehicle type, location, and time of day, this dashboard highlights key areas for intervention and safety improvements. 

With data from 2021 and 2022, the dashboard also tracks YoY trends, helping assess the effectiveness of past safety initiatives and guiding future policy decisions.

Project Objectives
The goal was to meet client requirements for a dashboard that highlights key performance indicators (KPIs) and breakdowns of accident data by year, severity, location, and time.

### Requirements for Dashboard

Clients wants to create a Road Accident Dashboard for year 2021 and 2022 so that they can have insight  ont the below requirements:
- Primary KPI – Total Casualties and Total Accident values for Current Year and YoY growth
- Primary KPI’s – Total Casualties by Accident Severity for Current Year and YoY growth
- Secondary KPI’s – Total Casualties with respect to vehicle type for Current Year
- Monthly trend showing comparison of casualties for Current Year and Previous Year
- Casualties by Road Type for Current Year
- Current Year Casualties by Area/Location & by Day/Night
- Total Casualties and Total Accidents by Location

### Steps followed 
- Step 1: Loaded the dataset (Excel file) into Power BI Desktop.
- Step 2: Opened Power Query Editor and enabled "Column distribution", "Column quality", and "Column profile" under the View tab to assess data quality.
- Step 3: Changed the profiling setting to analyze the entire dataset, not just the top 1000 rows.
- Step 4: Reviewed the data for nulls, errors, and inconsistencies. Corrected the typo mistake ("Fetal" > "Fatal") in "Accident_Severity" column.
- Step 5: Time Intelligence was activated for current file.
- Step 6: New data table was created for date storage called "Calendar". "Date" column stores date from primary data source. Additional columns were created for Year, Month & Month number storage.
- Step 7: New measure ("CY Casualties") was created to find total number of casualties in 2022.

Following DAX expression was written:
        
        CY Casualties = TOTALYTD(SUM(Data[Number_of_Casualties]), 'Calendar'[Date])
        
- Step 8: New measure ("PY Casualties") was created to find total number of casualties in 2021.

Following DAX expression was written:
        
        PY Casualties = CALCULATE(SUM(Data[Number_of_Casualties]), SAMEPERIODLASTYEAR('Calendar'[Date]))

- Step 9: New measure ("YoY Casualties") was created to find the growth of casualties compared to 2021.

Following DAX expression was written:
        
        YoY Casualties = ([CY Casualties] - [PY Casualties])/[PY Casualties] 
        - Step 10: A card visual was used to represent number of CY Casualties and YoY Casualties.

- Step 11: New measure ("CY Accident Count") was created to find total accident count in 2022.

Following DAX expression was written:
        
        CY Accident Count = TOTALYTD(COUNT(Data[Accident_Index]),'Calendar'[Date]) 

- Step 12: New measure ("PY Accident Count") was created to find total accident count in 2021.

Following DAX expression was written:
        
        PY Accident Count = CALCULATE(COUNT(Data[Accident_Index]), SAMEPERIODLASTYEAR('Calendar'[Date]))

- Step 13: New measure ("YoY Accidents") was created to find the growth of accidents compared to 2021.

Following DAX expression was written:

         YoY Accidents = ([CY Accident Count]-[PY Accident Count])/[PY Accident Count]

- Step 14: A card visual was used to represent number of CY Accidents and YoY Accidents and CY Casualties and YoY Casualties.

![Accidents image](/assets/CY-Accidents.png)
![Casualties image](/assets/CY-Casualties.png)
- Step 15: A card visuals depicting CY Fatal Casualties, CY Serious Casualties and CY Slight Casualties as described for CY Casualties with adding filter for respected Accident_Severity.

![Casualties-different image](/assets/Casualties_different.png)
- Step 16: Vehicle types grouped into 6 categories: Van, Car, Bus, Bike, Agricultural and Other.

- Step 17: A multi-row card visual was used to represent Casualties by Vehicle type.

![Casualties-vehicle image](/assets/Casualties-Vehicle-type.png)
- Step 18: An area chart visual was used to represent CY vs PY casualties by month number.

![Casualties-month image](/assets/casualties-by-month.png)
- Step 19: A donut chart visual was used to represent CY casualties by Urban or Rural area.

![Casualties-urban image](/assets/Casualties-Rural-urban.png)
- Step 20: Light conditions were group into two groups - Day and Night.

- Step 21: A donut chart visual was used to represent CY casualties by Day and Night time.

![Casualties-daylight image](/assets/Casualties-Day-night.png)

- Step 22: A bar chart was also added to the report design area representing the number of casualties by road type.

![Casualties-roadtype image](/assets/Casualties-roadtype.png)

- Step 23: A map was used to visualize casualties by location.

![Casualties-location image](/assets/casualties-location.png)

- Step 24: Visual filters (Slicers) were added for two fields named "Weather Continions" & "Road Surface".

![Slicer image](/assets/Slicer.png)

 # Report Snapshot (Power BI DESKTOP)

![Dashboard_upload](/assets/Dashboard.png)
