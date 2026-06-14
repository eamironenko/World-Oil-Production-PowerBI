# World-Oil-Production-PowerBI
Analysis of world oil production from 1900 to 2024 based on Energy Institute - Statistical Review of World Energy (2025) dataset.

## Table of Content
[Problem Statement](#problem-statement)
[Data Source](#data-source)
[Tools](#tools)
[Data Cleaning](#data-cleaning)
[Questions for Data Analysis](#questions-for-data-analysis)
[Dashboard](#dashboard)
[DAX](#dax)
[Recomendations](#Conclusion)

### Problem Statement
Oil remains one of the most important energy resources and a key driver of the global economy. Understanding long-term trends in oil production helps identify shifts in energy markets, changes in geopolitical influence, and the emergence of new leading producers. The objective is to explore how oil production has evolved over time, identify the largest producing countries, evaluate production concentration among major producers. 
The dashboard should help identify:
- How has global oil production changed over the last century?
- Which countries have been the leading oil producers over time?
- How concentrated is global oil production among the top producing countries?
- How have production rankings changed throughout different historical periods?
- What percentage of global production is contributed by the top 10 producing countries?

### Data Source
This dataset was obtained from the Our World in Data platform and downloaded in CSV format. The original data sources are the Energy Institute's Statistical Review of World Energy (2025) and The Shift Data Portal (2019). The data available through Our World in Data has been collected, harmonized, and maintained by the Our World in Data team.

The dataset contains historical oil production data from 1900 to 2024. Key fields used in this analysis include:
- Entity – country or region name.
- Code – ISO country code or regional identifier.
- Year – reporting year.
- Oil – annual oil production measured in terawatt-hours (TWh).

The oil production metric includes:
- Crude oil
- Shale oil
- Oil sands
- Condensates (lease condensate and gas condensates requiring further refining)
- Natural Gas Liquids (NGLs), including ethane, LPG, and naphtha separated during natural gas production

The metric excludes:
- Biofuels
- Synthetic fuels derived from coal or natural gas
- Refinery processing gains and other liquid fuel adjustment factors

Oil production values are converted from million tonnes into energy units using a standard oil-equivalent conversion factor of 41.868 petajoules per million tonnes.
Find Original Data Source Here: [Oil Production dataset](https://github.com/eamironenko/World-Oil-Production-PowerBI/blob/main/oil-production-by-country.csv)

### Tools
- Power Query – I used Power Query for Data Cleaning
- Excel – I used Excel for Data Analysis
  - Pivot Table – for creating the Dashboard and Visualizations

### Data Cleaning
- Data loading and inspection
- Handling errors, missing values
- Data cleaning and formatting.
- For the purpose of this analysis, aggregated regions and economic groups (e.g., World, OECD, OPEC, EU28, CIS, and other regional totals) were excluded to focus exclusively on country-level production trends and comparisonsю
- The excel file after the data cleaning & preparation process can be downloaded here [Clean Dataset Here](https://github.com/eamironenko/World-Oil-Production-PowerBI/blob/main/Oil_production_countries.xlsx)

### Questions for Data Analysis
- How concentrated is global oil production among the top producing countries?
- How have production rankings changed throughout different historical periods?
- What percentage of global production is contributed by the top 10 producing countries?

### Dashboard
<img width="1276" height="715" alt="Dashboard PowerBi" src="https://github.com/user-attachments/assets/9057b0db-75d5-49dd-82c3-e284fc9bb9ea" />
[Project file in pbix format Here](https://github.com/eamironenko/World-Oil-Production-PowerBI/blob/main/Dashboard%20Oil%20Production%20by%20countries.pbix)

### DAX
Total Production: Total Production = SUM('oil-production-by-country1'[Oil])*1000;

Country counts: Country counts = CALCULATE(DISTINCTCOUNT('oil-production-by-country1'[Country]), FILTER('oil-production-by-country1', 'oil-production-by-country1'[Oil]>0));

Average Production: Avg Production = DIVIDE('oil-production-by-country1'[Total Production],'oil-production-by-country1'[Country counts]);

Top 10 Producers: Top10 Production = CALCULATE([Total Production], TOPN(10, VALUES('oil-production-by-country1'[Country]), [Total Production],DESC))

Rest World PRoduction: Rest Production = 'oil-production-by-country1'[Total Production]-[Top10 Production]

### Conclusion
1. Long-Term Growth in Oil Production: The analysis reveals a strong long-term upward trend in global oil production between 1900 and 2024. Despite periods of economic downturns, geopolitical conflicts, and market volatility, global production has increased substantially over the last century, reflecting growing energy demand driven by industrialization, population growth, and economic development.

2. Leading Oil-Producing Countries: The largest contributors to global oil production are concentrated among a relatively small number of countries. The top producers identified in the dataset include:
  - United States
  - Saudi Arabia
  - Russia and CIS countries (aggregated regional group)
  - Iran
  - China

  These countries have consistently played a significant role in shaping global oil supply and energy markets.

3. Production Concentration: Oil production remains highly concentrated among the world's leading producers. The analysis shows that the top 10 producing countries account for approximately 30% of total global oil production, highlighting the strategic importance of a relatively small group of countries in meeting global energy demand.

4. Geographic Distribution of Production: The highest levels of production are concentrated in:
 - North America
 - The Middle East
 - Eurasia

 These regions contain many of the world's largest conventional oil reserves and continue to dominate global production.

5. Strategic Implications: The concentration of oil production among a limited number of countries suggests that global energy markets remain sensitive to geopolitical developments, production policies, and economic conditions within major producing regions. Changes in production levels among these key producers can have a significant impact on global supply, prices, and energy security.

Conclusion

Overall, the analysis demonstrates sustained growth in global oil production over the past century, supported by increasing energy demand and technological advancements. While production is geographically diversified, a relatively small group of countries continues to dominate global output, reinforcing their strategic importance in the global energy sector.








