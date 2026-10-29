# European Emission Trend (1990–2023)

Data visualization project analysing greenhouse gas emission trends across the EU-27, Norway and Iceland between 1990 and 2023, using Eurostat data, Python (pandas, Matplotlib, scikit-learn) and Tableau.

> Individual assignment for the **Data Visualization** course – University of Milano-Bicocca.
> Author: **Chiara Mezzanzanica**

📊 **Presentation:** [`European Emission Trend_presentation.pptx`](./European%20Emission%20Trend_presentation.pptx)

---

## Research questions

1. **Is Europe on track to meet the 2030 target of cutting total greenhouse gas emissions by 55% compared to 1990 levels?**
   - Have any European countries already reached this target?
   - Are emission trends influenced by geopolitical and economic events?
2. **Is the level of per-capita emissions linked to the socio-economic structure of a country?**
   - How does population change affect emissions per capita?
   - Which country currently has the highest per-capita emissions?

## Data

- **Source:** Eurostat – *Domestic net greenhouse gas emissions* ([metadata](https://ec.europa.eu/eurostat/cache/metadata/en/sdg_13_10_esmsip2.htm)).
- **Coverage:** 1990–2023, 27 EU member states plus Norway and Iceland.
- **Origin of the figures:** national reports to the UNFCCC, compiled via the European Environment Agency (EEA). Accuracy may therefore vary between countries.
- **Licence:** Eurostat allows free reuse of its data provided Eurostat is cited as the source.
- **Preprocessing:** no missing values were found. The original file was split into four internally consistent datasets, according to the unit of measure and the selection of categories in the Kyoto basket of greenhouse gases. Two of them are used in this project:

| File | Unit | Used in |
|------|------|---------|
| `totx4190.xlsx` | Index, 1990 = 100 | `Analisi_eurostat_dataset_i90.ipynb` |
| `totx4t_hab.xlsx` | Tonnes of emissions per capita | `Analisi_eurostat_dataset_tpc.ipynb` |

## Methodology

1. **Data cleaning and exploration** with pandas: structural cleaning, descriptive statistics, correlations and basic plots.
2. **Indexed emissions (1990 = 100)** – Matplotlib visualizations of the average EU/EEA trend, the min–max range across countries, the 2030 target (index = 45), and the main economic shocks (2008 recession, 2020 pandemic). Country rankings identify the best and worst performers in 2023.
3. **Per-capita emissions** – time series, comparison between 1990 and 2023, and analysis of the demographic effect on the per-capita figures.
4. **K-means clustering** (scikit-learn) on standardised per-capita trajectories. The number of clusters (k = 4) was chosen with the elbow method. Results were exported to CSV and visualised on a map in **Tableau**.

## Key findings

- The EU/EEA average index in 2023 is roughly **10% below 1990 levels** in the country-level average, against a 2030 target of index 45 (−55%).
- **Four countries** – Romania, Latvia, Lithuania and Estonia – have already surpassed the −55% target. **Cyprus and Iceland** are the only two countries above their 1990 emissions in 2023.
- Extremes of the indexed series: maximum **179.4** (Cyprus, 2008), minimum **27.0** (Estonia, 2023). Most volatile country: Denmark; most stable: Norway.
- Per-capita emissions range from **34.6 t** (Luxembourg, 1991) to **4.0 t** (Malta, 2020), with an average of **10.3 t**.
- Population change matters: demographic decline inflates per-capita reductions, while population growth (e.g. Luxembourg, about +80%) can mask real decarbonisation progress.
- Clustering identifies four groups of countries with distinct decarbonisation patterns; Luxembourg forms a cluster of its own.
- If current trends continue without substantial acceleration, the European average is unlikely to reach index 45 by 2030.

## Repository structure

```
.
├── README.md
├── European Emission Trend_presentation.pptx
├── notebooks/
│   ├── Analisi_eurostat_dataset_i90.ipynb    # indexed emissions (1990 = 100)
│   └── Analisi_eurostat_dataset_tpc.ipynb    # per-capita emissions + k-means clustering
└── data/
    ├── totx4190.xlsx                          # Eurostat data, index 1990 = 100
    └── totx4t_hab.xlsx                        # Eurostat data, tonnes per capita
```

> The notebooks are commented in Italian.

## How to reproduce

1. Clone the repository:
   ```bash
   git clone https://github.com/mezza04/Data_Visualization_Project.git
   cd Data_Visualization_Project
   ```
2. Install the dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
   ```
3. Open the notebooks in Jupyter and make sure the Excel files are read from the `data/` folder, e.g.:
   ```python
   df = pd.read_excel("../data/totx4190.xlsx")
   ```
4. Run the notebooks from top to bottom. The per-capita notebook also exports `cluster_europei_emissioni.csv`, which was used as input for the Tableau map.

## Tools

Python · pandas · NumPy · Matplotlib · seaborn · scikit-learn · Tableau · Claude (used to help convert country identifiers into a Tableau-compatible format)

## Licence

- **Data:** © European Union, Eurostat – reused under the [Eurostat licence policy](https://ec.europa.eu/eurostat/web/main/help/copyright-notice).

## Contact

Chiara Mezzanzanica – c.mezzanzanica2@campus.unimib.it
