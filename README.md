# NYC Rideshare Seasonal Demand Patterns

### An Exploratory Data Analysis of Uber and Lyft in New York City (2023–2025)

**Boston University | MS in Business Analytics | BA780**
---

## 1. Project Overview

How do seasonal changes, pickup locations, and weather conditions influence ride-hailing activity and passenger wait times in New York City?

This project analyzes **7,155,498 sampled rideshare trips from 2023 to 2025** to identify patterns that can support Uber's operational planning and competitive positioning relative to Lyft.

By examining trip volumes, passenger waiting times, pickup locations, weather conditions, and driver compensation, we aim to understand when and where ride-hailing activity is concentrated and identify potential opportunities to improve driver availability and passenger experience.

## 2. Business Problem

Matching driver availability with passenger demand is an important operational challenge for ride-hailing platforms. Demand varies across locations, hours, seasons, and weather conditions, making it difficult to anticipate when additional drivers may be needed.

Our analysis focuses on three business objectives:

1. **Demand forecasting:** Identify recurring seasonal, daily, and hourly patterns in ride-hailing activity.
2. **Operational efficiency:** Examine passenger waiting times and geographic demand concentrations to identify potential service improvements.
3. **Competitive benchmarking:** Compare Uber and Lyft across similar conditions to identify differences in passenger waiting times and recorded trip characteristics.

The findings are intended to support data-driven decisions about driver allocation, airport pickup operations, and service planning.

## 3. Data Sources

We combined three publicly available datasets:

| Dataset | Source | Description |
|---|---|---|
| High Volume For-Hire Vehicle Trip Records | NYC Taxi & Limousine Commission | Uber and Lyft trip records, 2023–2025 |
| Taxi Zone Lookup Table | NYC TLC | Pickup zone names and borough information |
| Local Climatological Data | NOAA | Daily weather observations from LaGuardia Airport |

**Sampling:** We used a 1% random sample from each of the 36 monthly HVFHV files between January 2023 and December 2025.

**Final dataset:** 7,155,498 trip records after removing one exact duplicate.

Data sources:

- [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
- [NYC Taxi Zone Lookup Table](https://d37ci6vzurychx.cloudfront.net/misc/taxi_zone_lookup.csv)
- [NOAA Local Climatological Data](https://www.ncei.noaa.gov/products/land-based-station/local-climatological-data)

## 4. Tools and Technologies

- **Python:** Data preparation and exploratory analysis
- **pandas:** Data cleaning, manipulation, and aggregation
- **NumPy:** Numerical operations
- **Matplotlib and Seaborn:** Statistical visualizations
- **Google Colab / Jupyter Notebook:** Analysis and documentation
- **Parquet:** Storage of sampled trip records

## 5. Data Preparation and Methodology

Our analysis followed a structured data preparation and exploratory analysis process.

### Data Cleaning

We first combined the 36 monthly samples into a single dataset containing 7,155,499 records.

The cleaning process included:

- Identifying and removing one exact duplicate.
- Inspecting missing values and column data types.
- Standardizing categorical variables, including shared-ride and wheelchair-accessibility flags.
- Validating pickup and drop-off timestamps.
- Identifying invalid trip measurements and negative passenger waiting times.
- Creating derived variables for pickup hour, weekday, season, and passenger wait time.
- Joining pickup location information from the TLC Taxi Zone Lookup Table.
- Integrating daily weather observations from NOAA.

Invalid measurements were excluded from relevant calculations rather than automatically removing entire trips from all analyses.

### Exploratory Data Analysis

We investigated 15 exploratory questions covering temporal demand, seasonal patterns, geographic concentrations, platform differences, weather conditions, fares, and driver compensation.

We used grouped summaries, median comparisons, and visualizations to examine patterns and evaluate our hypotheses.

## 6. Key Findings

### Finding 1: Weekend evenings show high ride-hailing activity

Friday and Saturday evenings were among the busiest pickup periods.

The highest recorded weekday-hour combination was **Saturday between 11 PM and midnight**, with 71,923 sampled trips accumulated across 2023–2025.

The preceding Saturday hour, 10–11 PM, followed closely with 71,722 sampled trips.

**Business implication:** Uber could prioritize weekend evenings when reviewing driver availability and operational capacity.

### Finding 2: Airports are major pickup hotspots

LaGuardia Airport and JFK Airport were the two busiest pickup zones in our sampled dataset.

| Pickup zone | Sampled trips |
|---|---:|
| LaGuardia Airport | 140,733 |
| JFK Airport | 127,382 |

Uber recorded more sampled trips than Lyft in all ten of the busiest pickup zones.

**Business implication:** Airport pickup operations deserve particular attention because of their concentrated activity and potential passenger waiting-time challenges.

### Finding 3: Winter activity increased across consecutive years

Average daily sampled winter trip activity increased in both annual comparisons:

- **2024:** +4.35%
- **2025:** +4.08%

However, growth was not consistent across all seasons. Spring activity declined by 0.54% in 2025, while fall increased by 3.94%.

August was consistently the month with the lowest average daily sampled activity across all three years.

**Business implication:** Seasonal planning should account for different growth patterns rather than assuming uniform demand changes throughout the year.

### Finding 4: Early-morning passenger waits are relatively long

In 2025, both Uber and Lyft experienced their longest hourly median passenger waits around 4 AM, at approximately five minutes.

Uber's lowest hourly median wait was 3.48 minutes during 10–11 AM.

**Business implication:** Early-morning service may warrant closer investigation, even though overall trip activity is concentrated during other periods.

### Finding 5: Uber had longer waits than Lyft in a controlled LaGuardia comparison

We compared passenger waiting times at LaGuardia Airport during 7–8 PM in 2025, controlling for pickup location, hour, and trip-distance category.

For trips between 5 and 10 miles:

| Platform | Median passenger wait |
|---|---:|
| Uber | 6.47 minutes |
| Lyft | 4.43 minutes |

Uber's median wait was approximately two minutes longer in this specific comparison.

**Business implication:** Uber could investigate airport pickup coordination and driver availability during this period to understand the difference.

This finding applies to the selected location, hour, year, and distance category and should not be generalized to all trips.

### Finding 6: Daily precipitation has a limited overall association with passenger waits

Median passenger waiting times were:

- **Precipitation days:** 4.07 minutes
- **Dry days:** 4.00 minutes

Although passenger waits were slightly longer on precipitation days, the difference was only approximately four seconds.

Weather-related pickup activity also varied by location. For example, East Village recorded more average daily sampled pickups on precipitation days, while LaGuardia showed the opposite pattern.

**Business implication:** Daily precipitation alone may not be sufficient to guide driver allocation decisions. More detailed weather and location data could improve operational planning.

## 7. Business Recommendations

Based on our findings, we identified several opportunities for further investigation.

**1. Review weekend and early-morning driver availability**

Weekend evenings experience high pickup activity, while early-morning hours show relatively long passenger waits. Uber could examine driver availability during these periods to identify possible service gaps.

**2. Improve airport pickup coordination**

LaGuardia and JFK have the highest sampled pickup activity. The longer Uber waits observed in the controlled LaGuardia comparison suggest that airport operations deserve additional investigation.

**3. Incorporate seasonal patterns into operational planning**

Winter activity increased across both annual comparisons, while August remained consistently quieter. These recurring patterns could inform seasonal capacity planning.

**4. Use more detailed weather information**

Hourly and location-specific weather data could help identify demand changes that are not visible in daily precipitation summaries.

These recommendations are opportunities for testing rather than proven interventions.

## 8. Limitations

Several limitations should be considered when interpreting our results.

**Sampling:** Our analysis uses 1% monthly samples rather than the complete population of NYC ride-hailing trips.

**Weather granularity:** Daily weather summaries may overlook short-term weather events that influence trip activity and passenger waits.

**Geographic coverage:** Weather observations from LaGuardia Airport may not accurately represent conditions across every NYC borough.

**Weather classification:** Grouping days into dry and precipitation categories does not distinguish between light rain and severe weather.

**Unmet demand:** The dataset contains completed trips but does not capture canceled rides, unfulfilled requests, or customers who abandoned the booking process.

**Driver compensation:** Recorded driver pay per trip hour does not account for time between trips or operating expenses.

These limitations mean that observed patterns should not be interpreted as evidence of causality or definitive proof of driver shortages.

## 9. Future Research

Future extensions of this project could include:

- Integrating hourly weather observations to examine short-term changes in demand.
- Expanding comparisons to additional for-hire vehicle services.
- Investigating the relationship between passenger fares, driver compensation, and platform revenue.
- Examining canceled requests and unmet demand where data becomes available.
- Testing whether targeted operational changes can reduce passenger waiting times.

## 10. Project Files and Reproducibility

The repository contains the Jupyter Notebook documenting the project's data preparation, exploratory analysis, visualizations, and conclusions.

To reproduce the analysis:

1. Open the project notebook in Google Colab.
2. Access the sampled monthly HVFHV datasets.
3. Add the dataset folder to Google Drive.
4. Mount Google Drive in Colab.
5. Update the dataset folder path to match your environment.
6. Run the notebook cells in order.

## 11. Data Attribution

This project uses publicly available NYC TLC trip records, the TLC Taxi Zone Lookup Table, and NOAA weather observations.

The sampled records and calculated measures are modifications of the original data.

- [NYC.gov Terms of Use](https://www.nyc.gov/main/terms-of-use)
- [NYC TLC Trip Record Data](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page)
- [NOAA Local Climatological Data](https://www.ncei.noaa.gov/products/land-based-station/local-climatological-data)

---

*Developed as part of the BA780 Business Analytics coursework at Boston University.*
