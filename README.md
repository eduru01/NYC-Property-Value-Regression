NYC Property Value Analysis
Data 200 Final Project Fall 2025

**Overview**
This project investigates which neighborhood features most strongly influence residential property values
across New York City, using multiple linear regression and borough-specific models. 
The goal is to understand how amenities and socioeconomic characteristics drive variation in
housing prices and how these relationships differ between the Bronx, Brooklyn, Manhattan, Queens, and Staten Island.

This analysis was completed as part of Data 200: Applied Statistical Methods at Tufts University.

**Research Questions**
How do number of new businesses, schools (public, private, and independent), subway stations, grocery stores, 
population, crime rate, unemployment rate, education rate, and median household income affect property value by zip code 
in New York City’s 5 boroughs? 


**Data Sources**
New York City Department of Consumer and Worker Protection. Issued Licenses. 
NYC Open Data. https://data.cityofnewyork.us/Business/Issued-Licenses/w7w3-xahh 

New York City Department of Health and Mental Hygiene. Modified Zip Code Tabulation Areas (MODZCTA) map. 
NYC Open Data. https://data.cityofnewyork.us/Health/Modified-Zip-Code-Tabulation-Areas-MODZCTA-Map/5fzm-kpwv 

New York City Police Department. NYPD Complaint Data - Current Year to Date. 
NYC Open Data. https://data.cityofnewyork.us/Public-Safety/NYPD-Complaint-Data-Current-Year-To-Date-/5uac-w243 

NewYork-Demographics.com. ZIP Codes by Population. 
https://www.newyork-demographics.com/zip_codes_by_population 

New York State Department of Agriculture & Markets. Retail Food Stores. data.ny.gov. 
https://data.ny.gov/Economic-Development/Retail-Food-Stores/9a8c-vfzj

New York State Education Department. K–12 Schools (GIS) dataset. 
New York State GIS. https://data.gis.ny.gov/datasets/sharegisny::schools-k-12  

New York State. New York State ZIP Codes ‒ County FIPS Cross-Reference. 
data.ny.gov. https://data.ny.gov/Government-Finance/New-York-State-ZIP-Codes-County-FIPS-Cross-Referen/juva-r6g2 

Social Explorer. American Community Survey 5-Year Estimates. 
U.S. Census Bureau, accessed 2024. https://www.socialexplorer.com/.

United States General Services Administration. MTA Subway Stations. 
Data.gov. https://catalog.data.gov/dataset/mta-subway-stations 

Zillow. (2025). ZHVI All Homes, Time Series, Seasonally Adjusted, Smoothed ($) for ZIP Code. 
Zillow Research. https://www.zillow.com/research/data/ 


**Methods**
We built a ZIP-code–level dataset combining point-based amenities (subway stations, grocery stores, crimes, schools, new businesses) with demographic and socioeconomic attributes (income, education, unemployment, population).
Point data were spatially joined to ZIP Code Tabulation Areas using sf in R, aggregated by ZIP code, and merged into one master dataset.
We ran:
Model 1: Full multiple linear regression across all NYC ZIP codes
Models 2–6: Separate regressions for each borough

**Model Performance**
R² = 0.58, Adjusted R² = 0.55
Residual Standard Error ≈ $285K
F-statistic p < 0.001 → model is highly statistically significant

**Borough-Level Results**
Predictors vary widely by borough:
Manhattan: Most significant predictors (subway stations ↑, income ↑, new businesses ↓)
Brooklyn: Grocery stores ↑, new businesses ↓
Queens: Population ↑ → property value ↓
Bronx & Staten Island: No significant predictors (small sample sizes)

**Limitations**
ZIP-level aggregation hides within-neighborhood variation
Predictors show multicollinearity
Data from multiple sources may introduce inconsistencies
Small borough samples reduce statistical power

**Future Work**
Add spatial models (GWR/GIS)
Incorporate time-series trends
Include zoning, school quality, and environmental amenities
Explore causal methods

**Key Findings**
- Income is consistently one of the strongest positive predictors of property values.
- Grocery stores behave as amenities, aligning with literature showing improved consumer access raises home prices.
- Crime typically lowers property values, but the full-NYC model identified an unexpected positive coefficient, possibly due to:
  - multicollinearity with population density
  - borough-specific clustering
  - measurement issues in reported crime data
- Predictor importance changes dramatically by borough, showing the NYC housing market is not uniform.


