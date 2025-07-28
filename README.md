# Informal Short-term Rentals in NYC: A Post-LL18 Analysis

This project explores the informal short-term rental market in New York City in the wake of Local Law 18 (LL18), which limited listings on platforms like Airbnb. Using web-scraped Craigslist listings and spatial census data, the analysis maps and interprets patterns of rent burden, demographic change, and neighborhood pressure.

## 🧰 Tools & Languages

- **Python** (web scraping)
- **R** (data cleaning, transformation, spatial analysis, mapping)
- **Datawrapper** (visualization)
- **Census Data** (ACS 5-Year Estimates)
- **Zillow ZORI** (Rent index)

## 📁 File Structure

```
project-directory/
├── README.md
├── craigslist scraping.ipynb                          # Python script to scrape and geocode listings from Craigslist
├── Data wrangling for listings.rmd                    # R script to group listings by ZIP code
├── Data wrangling for change in black population.rmd  # R script to group demographic change by ZIP code
├── Rent burden.rmd                                    # R script to compute and map rent burden
├── census_gentrification.rmd                          # R script to calculate demographic and income change

├── data/
│   ├── apartments.csv                                 #initial web-scraped listings
│   ├── apartments_with_location.csv                   #listings with reverse geocoded coordinates
│   ├── address_sheet3.csv                             #Python script writes to a Google Sheet file 
│   ├── listings_per_ZIP.csv                           #Craigslist listings by ZIP code
│   ├── zip_income_change_inflation_adjusted.csv       #inflation-adjusted rent burden by ZIP code
│   ├── rent_burdenNEW1.csv                            #2023 rent burden
│   ├── rent_burden_2025.csv                           #2025 inflation-adjusted rent burden (using 2023 income data)
│   ├── TRACT_ZIP_032025.csv                           #crosswalk obtained from HUD (converting tract to ZIP codes)
│   ├── race_percent_change.csv                        #percent change in all populations
│   ├── percent_change_black_with_zip.csv              #percent change in black population by ZIP code
│   ├── ZORI.csv                                       #rental data obtained from Zillow
  
 
 └── outputs/
    ├── data/
    
```

## Instructions

### 1. Scrape Craigslist Listings and reverse geocode (Python)
```bash
python craigslist scraping.ipynb
```

```r
source("Data wrangling for listings.rmd")
```
- Outputs: 
`data/apartments.csv`
`data/apartments._with_location.csv`
`data/apartments._with_location.csv`
`data/listings_per_ZIP.csv`

### 2. Calculate rent burden and percent change in Black population from 2013 to 2023
```r
source("census_gentrification.rmd")
```
These calculate:
  - Rent burden using Zillow ZORI and ACS income
  - Change in Black population (2013–2023)
  - Change in inflation-adjusted income (2013–2023)
  
- Outputs: 
`data/race_percent_change.csv`
`data/zip_income_change_inflation_adjusted.csv`

### 3. Clean up data and group by ZIP code
```r
source("Data wrangling for listings.rmd")
source("Data wrangling for change in black population.rmd")
```
- Outputs: 
`data/listings_per_ZIP.csv`
`data/percent_change_black_with_zip.csv`

### 4. Mapping & Visualization
- All mapping is performed in R and exported to CSV for visualization in **Datawrapper**.
- Includes both **dot maps** (listings) and **choropleth maps** (rent burden, population change, etc.)

## 📊 Research Focus

This analysis explores:
- The spatial distribution of informal short-term rental listings
- The spatial correlation with rent burden and gentrification
- Post-LL18 mapping of listing behavior

## ⚠️ Limitations

- Craigslist was the only platform scraped. More data might be available on informal short-term rentals from other platforms like Facebook Marketplace or Reddit.
- Some rental and income data had incomplete ZIP code coverage.
- Gentrification measured using change in Black population and income is only a proxy.

## License

MIT License. Free to use with attribution. Contact for collaborative reuse.

## Contact

Author: Marie Anne Lise Tan
Email: mt5655@nyu.edu
Project affiliated with: New York University (NYU) Wagner School of Public Service
