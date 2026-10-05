
## Setup

```bash
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

## Limits of the data

- Population from SITUAS is at 31/12/2024 and is used for all years: rates for earlier years are approximate.
- 682 municipality codes in the accidents table (1.85% of accidents) have no match in SITUAS 2024 because those municipalities were merged or abolished. They are kept in the dataset but excluded from the rates.
- The accident table only includes accidents with personal injuries, not property-damage-only accidents.
- 2024 lists only municipalities with at least 1 accident, so the 2024 mean rate is slightly overestimated.
- For Friuli-Venezia Giulia in 2024, local police data are partially estimated by ISTAT.
- Rates do not account for vehicle ownership or traffic volumes, which are not available at municipality level.

## Requirements

See `requirements.txt`. Main libraries: `pandas`, `requests`, `beautifulsoup4`, `selenium`, `matplotlib`, `seaborn`, `scikit-learn`, `scipy`, `statsmodels`.
