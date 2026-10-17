# ISTAT road accidents analysis

Analysis of road accidents in Italian municipalities (ISTAT and SITUAS data, 2001–2024) to find where a road-risk company should invest.

## Contents

- `01_incidenti_istat.ipynb`: download of the ISTAT accident data
- `02_situas.ipynb`: scraping of population and area from SITUAS
- `03_integration.ipynb`: cleaning, join and creation of the rates
- `04_eda_analysis.ipynb`: exploratory analysis and charts
- `05_advanced_analysis.ipynb`: K-means clustering, regression, t-test and ANOVA
- `Report.pbix`: Power BI dashboard
- `deck.pdf`: 5-slide presentation
- `Data/`: raw and processed data

Start with 01, then 02, 03, 04, 05
```

## Note on the download

The ISTAT server is slow and limits the number of requests. The raw file is already saved in `Data/Raw`, so it is not necessary to download it again.

## Main steps

1. Download of the accidents from the ISTAT API and scraping of population and area from SITUAS (Selenium).
2. Cleaning: the sigla "NA" (Napoli) is read as a missing value by pandas, so it is read as text. ISTAT does not list municipalities with zero accidents in 2024, so the 1,557 missing ones were added with zero.
3. Join on the municipality code and creation of the rates per 1,000 inhabitants and per km².
4. Exploratory analysis, K-means clustering, regression and ANOVA.
5. Power BI dashboard.

## Requirements

See `requirements.txt`. Main libraries: `pandas`, `requests`, `beautifulsoup4`, `selenium`, `matplotlib`, `seaborn`, `scikit-learn`, `scipy`, `statsmodels`.
