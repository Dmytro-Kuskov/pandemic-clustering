# Global Resilience Clustering: Socioeconomic and Mobility Patterns Before and After the Pandemic

---

## Project Overview

This project explores how structural characteristics of countries, such as healthcare access, mobility, urbanization, and demographics relate to their resilience during global pandemics.  

The study integrates data from multiple global sources (World Bank, Our World in Data) and examines how these clusters align with pandemic outcomes, such as excess mortality and vaccination coverage.

---

## Research Goals

1. Identify country clusters based on development, mobility, and demographic structure.  
2. Understand pandemic impact differences across clusters.  
3. Propose actionable policy insights for global health resilience and future crisis preparedness.  

---

## Datasets Used 

| Dataset | Purpose |
|----------|----------|
| **Urban Population (% of total)** | To adjust population density by urbanization rate, approximating effective human contact potential. |
| **Population Density (people/km²)** | Proxy for spatial distribution of human interaction. |
| **Population aged 65+ (% of total)** | Identifies vulnerable demographic share. |
| **Human Development Index (HDI)** |  Captures overall development level. |
| **Coverage of Essential Health Services** |  Measures accessibility of healthcare. |
| **% Without Improved Water Source** | Proxy for basic infrastructure and hygiene. |
| **Air Transport (passengers carried)** | Indicates international mobility and globalization level. |
| **Population Total** | Used to normalize air transport data (per capita). |
| **Excess Mortality and Vaccination** | Used to validate cluster outcomes post-pandemic. |

Data were preprocessed to:
- Remove small island territories and duplicates.
- Focus on years with maximal completeness: 2000, 2005, 2010, 2015, 2017, 2019, 2021.
- Use 2019 as the baseline for clustering.
- Fill missing values using previous years or regional medians.

---

## Methods and Analysis

- **EDA (Exploratory Data Analysis)**:
  - Correlation matrix, scatterplots, temporal trends, and distribution plots.
  - Identified strong multicollinearity among development indicators (HDI, healthcare, water access).  
  - Justified PCA-based dimensionality reduction into a single `PCA_Development` component.

- **Feature Engineering**:
  - `Adj_PopDensity = Population_Density × Urban_Population_%`
  - `Air_Transport_Per_Capita = Air_Transport / Total_Population`
  - Final clustering features:
    - `PCA_Development`
    - `Adj_PopDensity`
    - `AirTransportPerCapita`
    - `Population_65_Plus_Pct`

- **Clustering Algorithms Tested**:
  - K-Means (k optimized by silhouette score)
  - Agglomerative Clustering
  - DBSCAN (for outlier sensitivity)
  - PCA and t-SNE visualizations of cluster separation

---

## Key Insights

1. **High-HDI, high-mobility clusters** suffered the most from pandemic excess mortality, likely due to population aging, travel exposure, and early outbreak timing.  
2. **Low-mobility, younger clusters** had lower recorded mortality but face persistent risks from weak vaccination and health infrastructure.  
3. Pandemic impact was **not primarily economic**, but **structural and demographic**.

---

## Repository Structure
```
├── data/ 
│ ├── raw/
│ ├── interim/
│ └── processed/
├── notebook/
│ └── pandemic-clustering.ipynb
├── figures/ 
├── Reflective Narrative.pdf
├── Actionable impact brief.pdf
├── README.md
└── requirements.txt
```

---

## Data sources

- [United Nations Population Division, via World Bank (2025)](https://data.worldbank.org/indicator/SP.URB.TOTL.IN.ZS) – processed by Our World in Data
- World Population Prospects, United Nations ( UN ), publisher: UN Population Division [https://data.worldbank.org/indicator/SP.POP.65UP.TO.ZS](https://data.worldbank.org/indicator/SP.POP.65UP.TO.ZS)
- [Global Health Observatory, World Health Organization, via World Bank (2025)](https://data.worldbank.org/indicator/SH.UHC.SRVS.CV.XD) – processed by Our World in Data
- FAO population estimates, Food and Agriculture Organization of the United Nations ( FAO ), publisher: Food and Agriculture Organization of the United Nations ( FAO ); World Bank population estimates, World Bank ( WB ), publisher: World Bank ( WB ) [https://data.worldbank.org/indicator/EN.POP.DNST](https://data.worldbank.org/indicator/EN.POP.DNST)
- [UNDP, Human Development Report (2025);](https://hdr.undp.org/) Our World in Data – with minor processing by Our World in Data
- Civil Aviation Statistics of the World, International Civil Aviation Organization ( ICAO ), uri: [data.icao.int/newdataplus/#:~:text=ICAO%20data%20is%20comprised%20of,information%20about%20commercial%20air%20carriers](data.icao.int/newdataplus/#:~:text=ICAO%20data%20is%20comprised%20of,information%20about%20commercial%20air%20carriers); ICAO Staff estimates, International Civil Aviation Organization ( ICAO ), uri: [data.icao.int/newdataplus/#:~:text=ICAO%20data%20is%20comprised%20of,information%20about%20commercial%20air%20carriers](data.icao.int/newdataplus/#:~:text=ICAO%20data%20is%20comprised%20of,information%20about%20commercial%20air%20carriers)
- World Population Prospects, United Nations ( UN ), uri: population.un.org/wpp, publisher: UN Population Division; Statistical databases and publications from national statistical offices, National Statistical Offices, uri: unstats.un.org/home/nso_sites, publisher: National Statistical Offices; Eurostat: Demographic Statistics, Eurostat ( ESTAT ), uri: ec.europa.eu/eurostat/data/database?node_code=earn_ses_monthly, publisher: Eurostat; Population and Vital Statistics Report ( various years ), United Nations ( UN ), uri: unstats.un.org, publisher: UN Statistics Division
- [WHO/UNICEF Joint Monitoring Programme for Water Supply, Sanitation and Hygiene (JMP) (2024)](https://washdata.org/data/household#!/) – with major processing by Our World in Data
- [The Economist (2024)](https://github.com/TheEconomist/covid-19-the-economist-global-excess-deaths-model/tree/main) [World Health Organization (2025)](https://data.who.int/dashboards/covid19/cases?n=c) [Population based on various sources (2024)](https://ourworldindata.org/population-sources) – with major processing by Our World in Data
- [Official data collated by Our World in Data (2024)](https://github.com/owid/covid-19-data/) [World Health Organisation (2025)](https://data.who.int/dashboards/covid19/cases?n=c) [Population based on various sources (2024)](https://ourworldindata.org/population-sources) – with major processing by Our World in Data

---





