# ISTAT road accidents analysis

Analysis of road accidents in 7,896 Italian municipalities (ISTAT and SITUAS data, 2001–2024) to find where a road-risk company should invest.

## Contents

- `01_incidenti_istat.ipynb`: download of the ISTAT accident data
- `02_situas.ipynb`: scraping of population and area from SITUAS
- `03_integration.ipynb`: cleaning, join and creation of the rates
- `04_eda_analysis.ipynb`: exploratory analysis and charts
- `05_advanced_analysis.ipynb`: K-means clustering, regression, t-test and ANOVA
- `Report.pbix`: Power BI dashboard
- `deck.pdf`: 5-slide presentation
- `Data/`: raw and processed data

## Setup

```
# 1. Clone the repository
git clone https://github.com/martinafurian/istat-traffic-analysis.git
cd istat-traffic-analysis

# 2. Create and activate a virtual environment
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # Mac/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Run the notebooks in order
# Open each notebook in VS Code or Jupyter and run all cells
# Start with 01, then 02, 03, 04, 05
```

## Note on the download

The ISTAT server is slow and limits the number of requests. The raw file is already saved in `Data/Raw`, so it is not necessary to download it again.

## Main steps

1. Download of the accidents from the ISTAT API and scraping of population and area from SITUAS (Selenium).
2. Cleaning: the sigla "NA" (Napoli) is read as a missing value by pandas, so it is read as text. ISTAT does not list municipalities with zero accidents in 2024, so the 1,557 missing ones were added with zero.
3. Join on the municipality code and creation of the rates per 1,000 inhabitants and per km².
4. Exploratory analysis, K-means clustering, regression and ANOVA.
5. Power BI dashboard.

## Limits of the data

- Population from SITUAS is at 31/12/2024 and is used for all years, so rates for earlier years are approximate.
- 682 municipality codes in the accidents table (1.85% of accidents) have no match in SITUAS 2024 because those municipalities were merged or abolished. They are kept in the dataset but excluded from the rates.
- The accident table only includes accidents with personal injuries, not accidents with property damage only.
- In 2024 ISTAT lists only municipalities with at least one accident. The 1,557 missing municipalities were added with zero accidents, deaths and injured. The 2024 totals (173,364 accidents, 3,030 deaths, 233,853 injured).
- Rates do not account for vehicle ownership or traffic volumes, which are not available at municipality level.
- No forecast is included: only one year of population is available for each municipality.

## Requirements

See `requirements.txt`. Main libraries: `pandas`, `requests`, `beautifulsoup4`, `selenium`, `matplotlib`, `seaborn`, `scikit-learn`, `scipy`, `statsmodels`.
