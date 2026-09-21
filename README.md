# ASEAN Energy Transition

A cross-country data analysis of renewable energy, carbon emissions, and electricity access across all 10 ASEAN member states, 2000 to 2022.

**Full report:** [report/asean-energy-transition-report.pdf](report/asean-energy-transition-report.pdf) ([Word version](report/asean-energy-transition-report.docx))

**Interactive dashboard:** [index.html](index.html) (standalone, opens in any browser)

## Background

ASEAN is one of the world's most economically diverse regions, spanning roughly a 180-fold income gap between its richest and poorest member states. That diversity makes any single "ASEAN energy transition" narrative misleading: a headline regional average can hide sharply different trajectories, and even similar-looking numbers can mean very different things depending on income level, energy mix, and political context. This analysis looks at four widely used World Bank indicators, renewable energy share, CO2 emissions per capita, electricity access, and GDP per capita, across all 10 member states over 23 years, to see what patterns actually hold up once countries are compared individually rather than as a bloc.

## Research questions

Is fossil fuel growth outpacing the renewable energy transition across ASEAN, or is the headline renewable share misleading? How are CO2 emissions per capita evolving across the region's income spectrum? Which countries have reached near-universal electricity access, and which remain behind? And is there early evidence of CO2-income decoupling in wealthier ASEAN states?

## Data source

World Bank World Development Indicators (WDI), retrieved April 2026, covering all 10 ASEAN member states over 2000 to 2022 (23 annual observations per country). Four indicators are used: renewable energy consumption as a share of total final energy consumption (EG.FEC.RNEW.ZS), CO2 emissions per capita in metric tons (EN.ATM.CO2E.PC), access to electricity as a percentage of population (EG.ELC.ACCS.ZS), and GDP per capita in current US dollars (NY.GDP.PCAP.CD). Linear interpolation was applied where intermediate annual values were unavailable.

## Methodology

The analysis is descriptive and exploratory. For each indicator, trends are plotted across all 10 countries over the full time series, then summarized as a 2022 snapshot for cross-country comparison. A composite Energy Transition Readiness score is constructed as an unweighted average of four normalized (0 to 1) sub-scores: current renewable share, CO2 per capita (inverted, so lower emissions score higher), electricity access, and the percentage-point change in renewable share from 2000 to 2022. This composite is illustrative rather than a validated index; the equal weighting is a modeling choice, not an empirical result. Full code is in `src/ASEAN_Energy_Transition_EDA.ipynb`.

## Findings

**Renewable share is falling in several of the largest economies, not because of less renewable adoption, but because fossil generation grew faster.** Indonesia's renewable share fell from about 44% to 15% between 2000 and 2022, driven by coal-fired power expansion outpacing renewables in absolute terms. The same pattern, a "falling floor," appears in Cambodia, Vietnam, and the Philippines. Vietnam is a partial exception: a feed-in tariff programme introduced after 2018 triggered a solar and wind boom that reversed its earlier decline, an example of how a specific policy lever can shift trajectory quickly.

**Regional renewable statistics substantially overstate clean energy progress in lower-income states.** Lao PDR, Cambodia, and Myanmar post the highest renewable shares in the region (69%, 38%, and 55% respectively), but this is driven mainly by traditional biomass use, cooking on wood and charcoal, rather than modern renewables such as solar, wind, or hydro. This is a development indicator, not a clean energy achievement, and conflating the two overstates the region's actual transition progress.

**CO2 emissions are rising fastest exactly where economic growth is most needed.** Vietnam's per-capita emissions grew roughly sixfold between 2000 and 2022 (0.5 to 3.0 metric tons), tracking rapid, coal-heavy industrialization. Cambodia, Lao PDR, and Indonesia show similar upward trajectories. This creates a real tension for regional climate policy: the economies that most need continued growth are also seeing the fastest emissions growth, and the power and industrial infrastructure being built now typically has a 30 to 40 year lifespan, meaning decisions made in the next few years will shape emissions trajectories well past 2050.

**There is early, tentative evidence of income-emissions decoupling at the top of the income range.** Malaysia's per-capita emissions appear to be stabilizing around 7.5 to 8 metric tons despite continued GDP growth, and Singapore shows a flat or slightly declining trend since roughly 2010. Brunei is a clear outlier in the other direction: at 20 metric tons per capita, its emissions are far above what its income level would predict, consistent with heavy energy subsidies and a fossil-fuel-dependent economy.

**Electricity access has improved dramatically almost everywhere, with one clear exception.** Cambodia went from about 20% to 87% access between 2000 and 2022, Lao PDR from 35% to 92%, and Indonesia from 72% to 99%, among the largest electrification gains recorded anywhere in this period. Five countries (Brunei, Malaysia, Singapore, Thailand, and Vietnam) have reached or are approaching universal access. Myanmar is the exception, at 65% access and the lowest in the region; political instability since 2021 appears to have reversed some earlier infrastructure gains, and its energy access gap increasingly reads as inseparable from a governance problem rather than a purely technical one.

**On a composite readiness score combining all four indicators, Lao PDR ranks highest and Brunei lowest**, but this ranking should be read carefully: Lao PDR's high score is substantially inflated by traditional biomass counted as renewable energy, illustrating exactly the measurement problem described above.

## Limitations

Traditional biomass use inflates renewable energy percentages for lower-income countries in a way that is not comparable to modern renewable generation, and this analysis does not separate the two because the underlying indicator does not distinguish them. Linear interpolation was used to fill gaps between annual observations, which smooths short-term volatility that may be analytically meaningful. The composite index uses equal weighting across four sub-scores as a simplifying choice, not an empirically derived one, and a different weighting scheme would produce a different ranking. GDP figures are in current US dollars rather than purchasing-power-adjusted terms, which affects cross-country income comparisons. Finally, this is a descriptive analysis: associations discussed here (for example, between policy changes and renewable share shifts) are consistent with a causal story but are not tested as one.

## Repository structure

```
src/        exploratory data analysis notebook (data and code)
figures/    chart images used in the report
report/     formal write-up (Word and PDF)
index.html  interactive dashboard
```

## Citation

Rachmania Dwipayani, A. (2026). *ASEAN Energy Transition: A Cross-Country Data Analysis.*
