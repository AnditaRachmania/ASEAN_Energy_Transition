# ASEAN Energy Transition — Cross-Country Data Analysis

A structured exploratory data analysis of energy transition progress across all 10 ASEAN member states, using 23 years of annual data (2000–2022) from the World Bank World Development Indicators (WDI).

---

## Project Files

| File | Description |
|------|-------------|
| `ASEAN_Energy_Transition_EDA.ipynb` | Jupyter notebook — full analysis with charts and methodology |
| `ASEAN_Energy_Transition_Dashboard.html` | Standalone interactive dashboard (open in any browser, no server needed) |
| `ASEAN_Energy_Transition_Report.pptx` | 10-slide summary presentation |

---

## Research Questions

1. **Renewable Share** — Is fossil fuel growth outpacing renewables? Is the headline share misleading?
2. **Carbon Trajectory** — How are CO₂ emissions evolving across the ASEAN income spectrum?
3. **Energy Access** — Which nations have reached universal electricity access, and who is left behind?
4. **GDP vs CO₂** — Does higher income mean higher emissions across ASEAN — and is that relationship starting to change?

---

## Data Source

**World Bank World Development Indicators (WDI)**
`databank.worldbank.org/source/world-development-indicators` · Retrieved April 2026

| Indicator Code | Description | Unit |
|----------------|-------------|------|
| `EG.FEC.RNEW.ZS` | Renewable energy consumption (% of total final energy consumption) | % of TFEC |
| `EN.ATM.CO2E.PC` | CO₂ emissions per capita | Metric tons |
| `EG.ELC.ACCS.ZS` | Access to electricity | % of population |
| `NY.GDP.PCAP.CD` | GDP per capita (current US$) | USD |

**Coverage:** 10 ASEAN member states · 23 annual observations per country (2000–2022)

**Note on interpolation:** Where intermediate annual values were not available at time of retrieval, linear interpolation was applied between published WDI anchor observations. Endpoint and recent values (2000, 2018–2022) are sourced directly from WDI published series.

---

## Composite Scorecard Methodology

The composite scoring is illustrative — intended to summarise relative performance, not serve as a definitive index.

**Four normalised sub-scores (each 0–1 scale, within ASEAN):**

| Score | Source Indicator | Direction | Formula |
|-------|-----------------|-----------|---------|
| Renewable Share | `EG.FEC.RNEW.ZS` (2022) | Higher = better | min-max normalise |
| Low CO₂ | `EN.ATM.CO2E.PC` (2022) | Lower = better | min-max normalise, then invert |
| Electricity Access | `EG.ELC.ACCS.ZS` (2022) | Higher = better | min-max normalise |
| Renewable Growth | `EG.FEC.RNEW.ZS` (2022 − 2000) | Higher growth = better | min-max normalise pp change |

**Composite score** = unweighted average of the four sub-scores.

**Normalisation formula:**
```
score = (value − min_ASEAN) / (max_ASEAN − min_ASEAN)
```

Scores are relative to the ASEAN group only — a score of 1.00 means best within ASEAN, not globally.

**Key assumptions:**
- Equal weight (25%) for each indicator
- Renewable share includes traditional biomass per WDI definition — inflates scores for Lao PDR, Myanmar, Cambodia
- Renewable Growth = absolute percentage point change (2022 − 2000), not an annual rate
- 2022 snapshot only for the level indicators

---

## Key Findings

- **Indonesia's falling floor:** Renewable share dropped from 44% → 15% (2000–2022) as coal expansion outpaced renewables in absolute energy terms
- **Vietnam's solar inflection:** Feed-in tariff reforms post-2018 triggered a rapid solar and wind buildout, reversing a decade of decline
- **Cambodia & Myanmar access gains:** Among the fastest electricity access expansions globally — Cambodia: 20% → 87%; Myanmar: 15% → 65%
- **Myanmar's persistent gap:** Lowest electricity access in ASEAN at 65%; political instability since 2021 has reversed earlier infrastructure progress
- **Brunei's emissions outlier:** Highest CO₂ per capita in ASEAN (20t) — driven by deep energy subsidies and structural fossil-fuel dependence
- **Malaysia & Singapore levelling:** Both countries have seen per-capita CO₂ stabilise despite continued GDP growth

---

## How to Run

**Notebook:**
```bash
# Requires: Python 3.8+, numpy, pandas, matplotlib
jupyter notebook ASEAN_Energy_Transition_EDA.ipynb
```

**Dashboard:**
Open `ASEAN_Energy_Transition_Dashboard.html` in any modern browser. No installation required — all data is embedded and charts load from the Plotly CDN.

---

## Limitations

- Traditional biomass is included in the WDI renewable energy indicator — headline renewable shares for lower-income ASEAN countries are not directly comparable to modern clean energy metrics
- Linear interpolation introduces smoothing between anchor years
- Composite scorecard uses equal indicator weights — results are sensitive to weighting choices
- GDP per capita is in current USD, not adjusted for purchasing power parity

---

## Author

**Andita Rachmania** · Data & Analytics Analyst · MSc Environmental Engineering (ITB)  
`andita.rachmania@gmail.com` · [linkedin.com/in/andita-rachmania-3754561b6](https://linkedin.com/in/andita-rachmania-3754561b6)
