# Utah Air Quality vs. Vehicle Registrations

## Project Overview
This project investigates whether growing vehicle registrations in Utah correlate with worsening air quality. Using EPA Air Quality Index (AQI) data and Utah DMV registration records spanning 25 years, the analysis examines county-level trends to test the assumption that more cars on the road means worse air.

**Tools Used:** SQL Server, Tableau  
**Skills Demonstrated:** Data joining, filtering, aggregation, derived columns, exploratory analysis  
**Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/andrew.wilding/viz/AQIvsRegistrations/Dashboard1)

---

## Dataset
| Dataset | Source | Rows | Granularity |
|---|---|---|---|
| Utah Vehicle Registrations | [Utah Tax Commission](https://tax.utah.gov/econstats/mv/registrations) | 725 | County / Year |
| EPA Air Quality Index | [EPA AQS Data](https://aqs.epa.gov/aqsweb/airdata/download_files.html) | 332 | County / Year |

Registration data covers all Utah counties over 25 years. AQI data is less complete, with usable records for 17 counties. To ensure data quality, the analysis filters to county-years where AQI was reported on at least 350 days.

---

## Methodology
Cars are the leading source of CO and NO2 emissions according to the EPA. To isolate vehicle-related air quality impact, pollutant days were grouped into two categories:

- **Vehicle-related:** Days CO or NO2 was the primary pollutant
- **Other causes:** Days Ozone, PM2.5, or PM10 was the primary pollutant

The two datasets were joined on County and Year, then filtered to records with 350+ days of AQI reporting to exclude counties with incomplete monitoring data.

---

## Key Findings

1. **Registrations increased 4.4x** — From 615,904 in 1997 to 2,729,278 in 2021
2. **Vehicle-related pollution days fell to 1/7th** — Days where CO or NO2 was the main pollutant dropped from 774 to 110 over the same period
3. **Salt Lake County is an outlier** — Despite having more than twice as many registrations as the next county, it ranks only 4th in days where CO/NO2 is the primary pollutant
4. **Washington County** — Contains the 5th most registrations in the state yet has reported only 2 days in 16 years where CO or NO2 was the primary pollutant

### Conclusion
Based on this data, a direct correlation between vehicle registrations and AQI cannot be confirmed. Despite a dramatic increase in vehicles on the road, days dominated by vehicle-related pollutants have declined significantly.

---

## Further Questions
1. Have vehicle emissions improvements outpaced the growth in registered vehicles?
2. Are there other contributors to CO and NO2 (refineries, agriculture) that could be influencing results?
3. Would the same analysis in other states yield similar findings?
4. Does county land area relative to registration density affect AQI outcomes?

---

## Files
| File | Description |
|---|---|
| `AQIvsRegistrations.sql` | All queries including join logic, filtering, and derived columns |
| `AQI.xlsx` | EPA AQI source data |
| `Registrations.xlsx` | Utah DMV registration source data |
| `AQI_vs_Registrations.xlsx` | Joined dataset used for Tableau |
