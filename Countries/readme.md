# Countries Dataset

A dataset of 194 countries with 64 columns covering geography, economy, energy, emissions, health, demographics, governance, and democracy. It is intended for exploratory analysis and comparison across countries.

## Contents

- `Countries.csv`: the dataset (194 rows, 64 columns)

## Requirements

- Python 3.x
- pandas

Load it with:

```python
import pandas as pd

df = pd.read_csv("Countries.csv")
```

## Dataset overview

- **Rows:** 194, one per country
- **Columns:** 64 (48 float, 6 integer, 10 text)
- **Index:** default integer index from 0 to 193

## Columns

### Identity and location

| Column | Description |
|--------|-------------|
| `country` | Short country name |
| `country_long` | Official country name |
| `capital_city` | Capital city |
| `region` | Geographic region |
| `continent` | Continent |
| `demonym` | Name for a person from the country |
| `latitude`, `longitude` | Geographic coordinates |
| `currency` | Official currency |

### Land use

| Column | Description |
|--------|-------------|
| `land_area` | Total land area |
| `agricultural_land` | Agricultural land area |
| `forest_area` | Forest area |
| `rural_land`, `urban_land` | Rural and urban land area |

### Economy

| Column | Description |
|--------|-------------|
| `gdp` | Gross domestic product |
| `inflation` | Inflation rate |
| `central_government_debt_pct_gdp` | Central government debt as % of GDP |
| `expense_pct_gdp` | Government expense as % of GDP |
| `tax_revenue_pct_gdp` | Tax revenue as % of GDP |
| `unemployment_pct` | Unemployment rate |
| `self_employed_pct` | Share of self-employed workers |
| `vulnerable_employment_pct` | Share of vulnerable employment |

### Energy

| Column | Description |
|--------|-------------|
| `electricity_access_pct` | Share of population with electricity access |
| `electricty_production_coal_pct` | Electricity from coal, % |
| `electricty_production_hydroelectric_pct` | Electricity from hydroelectric, % |
| `electricty_production_gas_pct` | Electricity from gas, % |
| `electricty_production_nuclear_pct` | Electricity from nuclear, % |
| `electricty_production_oil_pct` | Electricity from oil, % |
| `electricty_production_renewable_pct` | Electricity from renewables, % |
| `alternative_nuclear_energy_pct` | Alternative and nuclear energy, % |
| `energy_imports_pct` | Energy imports, % |
| `fossil_energy_consumption_pct` | Fossil fuel energy consumption, % |
| `renewable_energy_consumption_pct` | Renewable energy consumption, % |

### Emissions

| Column | Description |
|--------|-------------|
| `co2_emissions` | CO2 emissions |
| `methane_emissions` | Methane emissions |
| `nitrous_oxide_emissions` | Nitrous oxide emissions |
| `greenhouse_other_emissions` | Other greenhouse gas emissions |

### Health

| Column | Description |
|--------|-------------|
| `health_expenditure_pct_gdp` | Health expenditure as % of GDP |
| `health_expenditure_capita` | Health expenditure per capita |
| `hospital_beds` | Hospital beds per population |
| `hiv_incidence` | HIV incidence |
| `suicide_rate` | Suicide rate |
| `life_expectancy` | Life expectancy |
| `fertility_rate` | Fertility rate |
| `birth_rate`, `death_rate` | Birth and death rates |

### Population and demographics

| Column | Description |
|--------|-------------|
| `population` | Total population |
| `population_female`, `population_male` | Population by sex |
| `urban_population`, `rural_population` | Urban and rural population |
| `urban_population_under_5m` | Urban population under 5 million |
| `median_age` | Median age |
| `net_migration` | Net migration |
| `internet_pct` | Share of population using the internet |
| `internally_displaced_persons` | Internally displaced persons |

### Security

| Column | Description |
|--------|-------------|
| `armed_forces` | Size of armed forces |
| `military_expenditure_pct_gdp` | Military expenditure as % of GDP |

### Governance and politics

| Column | Description |
|--------|-------------|
| `democracy_score` | Democracy score |
| `democracy_type` | Type of democracy or government |
| `political_leader` | Name of the political leader |
| `title` | Title of the political leader |
| `women_parliament_seats_pct` | Share of parliament seats held by women, % |
| `press` | Press freedom measure |

## Missing values

Several columns have missing entries. The most affected are `internally_displaced_persons` (121 missing), `hiv_incidence` (61), `central_government_debt_pct_gdp` (74), and the electricity production and energy import columns (56 each). Columns such as `political_leader` and `title` have 7 missing values each.

## Example usage

```python
# Most populous country
df.loc[df["population"].idxmax(), "country"]

# Top 5 countries by democracy score
df.sort_values("democracy_score", ascending=False)["country"].head()

# Countries in Eastern Europe
df[df["region"] == "Eastern Europe"]["country"]
```