# Hate Crime Trends in New York City (2019–2024)

An analysis of 3,450 NYPD-confirmed hate crime complaints from 2019 to 2024. It looks at how incidents changed over time, which boroughs and groups are most affected, and how reliable the underlying data is.

## Key findings
- Hate crimes fell to **284** in 2020, then rose to a peak of **758** in 2023 and dipped to 709 in 2024.
- **Anti-Jewish** incidents are **45.9%** of all cases (1,585) and rose every year from 2020 to 2024, including 2024, when the overall total fell.
- **Anti-Asian** incidents went from 1 in 2019 to **150** in 2021, then declined each year.
- **Per resident, Manhattan's rate is about 5.5× the Bronx's** (12.7 vs. 2.3 incidents per 100,000 residents per year). Staten Island, lowest in raw counts, has about the same rate as Queens.
- Among incidents with a known location, **homes** and **places of worship** are the most common settings.

## Data quality findings
- **55%** of NYPD hate crimes reported to the FBI list the offender's race as "Unknown," and **66%** list the location as "Other/Unknown."
- Federal (DOJ) and state/city totals for New York disagree: they're close in 2022 (953 vs. 958) but **130 incidents apart in 2023** (1,048 vs. 1,178), which points to different definitions and reporting systems.

## Data sources
| Source | Used for |
|---|---|
| [NYPD Hate Crimes, NYC Open Data](https://data.cityofnewyork.us/Public-Safety/NYPD-Hate-Crimes/bqiq-cu78) | Main dataset: year, borough, county, bias motivation |
| [NY DCJS Hate Crimes by County](https://data.ny.gov/Public-Safety/Hate-Crimes-by-County-and-Bias-Type-Beginning-201/6xda-q7ev) and 2023 regional update | NYC vs. rest of state, 2010–2023 |
| [FBI Crime Data Explorer, NIBRS hate crime file](https://cde.ucr.cjis.gov/) | Offender race and location type (filtered to the NYPD) |
| [U.S. DOJ hate crime statistics, New York](https://www.justice.gov/hatecrimes/state-data/new-york) | Federal totals for comparison |
| 2020 U.S. Census | Borough populations for per-resident rates |

## Method
- Cleaned and filtered the NYPD data to complete years (2019–2024) with pandas
- Grouped incidents by year, patrol borough, county, and bias motivation, and calculated year-over-year change
- Calculated per-resident rates by dividing borough counts by 2020 Census populations
- Compared NYC with the rest of the state and compared federal totals with state and city totals
- Analyzed offender race and location type from the FBI's NIBRS file

## Repository contents
```
hatecrime_analysis.ipynb                     analysis notebook, with outputs and charts
data/hatecrime_opennyc.csv                   NYPD hate crimes (NYC Open Data)
data/hatecrime_by_county.csv                 NY DCJS county data, 2010-2022
data/hate_crime_bias_type_2023.xlsx          NY DCJS 2023 regional update
data/nibrs_nyc_hate_crime_2019_2023.csv      FBI NIBRS hate crime file, filtered to the NYPD
```

## Limitations
- The data covers only reported, confirmed hate crimes, so underreporting is likely.
- Timing alone can't establish causes. Shifts in bias categories coincide with events like COVID-19 and conflict in the Middle East, but that link isn't tested statistically.
- Per-resident rates are based on where people live, not where they work or visit, which inflates Manhattan's rate.
- The FBI NIBRS file covers 2019–2023 only.

## How to run
Open `hatecrime_analysis.ipynb` in Jupyter or Google Colab, with the `data` folder in the same directory, and run all cells. If the NYPD file is missing, the notebook downloads it from NYC Open Data.

**Tools:** Python, pandas, matplotlib
