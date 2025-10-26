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

---





