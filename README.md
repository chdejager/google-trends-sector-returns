# Google Search Attention And Sector Returns

This project studies whether Google Trends search-attention factors help explain or predict GICS sector returns. The workflow builds a cleaned Google Trends keyword panel, extracts principal components, and evaluates their relationship to sector ETF returns.

This repository accompanies the SSRN preprint **Googling the Market: Latent Attention Factors and Sector-Level Equity Return Predictability**.

## Project Summary

Investor attention is difficult to observe directly, but search behavior offers a high-frequency proxy for what market participants are watching. This project uses Google Trends keyword interest data to build latent attention factors, then tests whether those factors are related to sector-level equity return predictability. The empirical workflow filters a broad keyword universe, extracts principal components from the cleaned search panel, and evaluates in-sample, out-of-sample, directional, and portfolio-style evidence using GICS sector ETF returns.

## Headline Results

- The preprocessing pipeline reduces the keyword universe from 1,446 collected terms to 163 PCA inputs after missing-value, zero-value, mean-interest, and manual relevance filters.
- The first principal component explains roughly 56% of keyword-panel variance, while the first 5 and 10 PCs explain about 81% and 88%, respectively.
- Granger-style diagnostics identify several sector/PC relationships at the 5% level, especially for Consumer Discretionary, Communication Services, Technology, Energy excess returns, and related sector series.
- Out-of-sample return forecasts are modest overall, with average OOS R2 generally close to zero or negative across model classes.
- Portfolio-style tests show stronger performance for some one-month horizon strategies, but these should be interpreted as empirical diagnostics rather than live trading recommendations.

## Repository Structure

- `notebooks/`: analysis notebooks in execution order.
- `data/raw/`: collected input data.
- `data/processed/`: cleaned panels and reusable intermediate datasets.
- `data/results/`: model diagnostics, Granger tests, and portfolio/backtest outputs.
- `figures/`: exported figures for papers, slides, or README images.

## Notebook Workflow

1. `notebooks/1_stabiltiy_analysis.ipynb`: checks whether `"stock market"` is a stable Google Trends anchor.
2. `notebooks/2_preprocessing_data.ipynb`: filters and prepares the keyword panel.
3. `notebooks/3_pca_analysis.ipynb`: estimates PCA factors from the filtered keyword panel.
4. `notebooks/4_predictive_analysis.ipynb`: tests predictive relationships with sector ETF returns.

The notebooks are written to run from either the repository root or the `notebooks/` directory.

## Reproducing The Analysis

Run the notebooks in numerical order. The first three notebooks use local CSV files included in the repository. The fourth notebook downloads monthly sector ETF and SPY prices with `yfinance`, so those results may change slightly if the upstream data source revises historical prices.

Primary generated files:

- `data/processed/trends_final_filtered.csv`
- `data/processed/pca_scores.csv`
- `data/processed/pca_loadings.csv`
- `data/processed/analysis_panel.csv`
- `data/results/granger_sector_to_pc_best_by_sector.csv`
- `data/results/oos_model_average_results.csv`
- `data/results/portfolio_summary.csv`

## Citation

De Jager, C. (2026). *Googling the Market: Latent Attention Factors and Sector-Level Equity Return Predictability*. SSRN preprint. Available at SSRN 6971058.
