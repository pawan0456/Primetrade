# Trader Performance vs. Bitcoin Market Sentiment

A quantitative analysis of Hyperliquid trader behavior across Bitcoin Fear & Greed sentiment regimes — built as a Data Science internship assignment for a Web3 trading company.

## Overview

This project merges trade-level data from Hyperliquid with the Bitcoin Fear & Greed Index to explore how market sentiment relates to trader performance, position sizing, and buy/sell behavior. It covers data cleaning, merging, exploratory data analysis, correlation analysis, and business/trading recommendations.

## Project Structure

```
project/
├── trader_sentiment_analysis.ipynb        # Main Jupyter notebook (full analysis)
├── historical_data.csv                    # Hyperliquid trade-level data
├── fear_greed_index.csv                   # Bitcoin Fear & Greed Index data
├── Trader_Sentiment_Analysis_Report.docx  # Professional written report
├── figures/                                # Auto-generated charts (created when notebook runs)
└── README.md                               # This file
```

## Datasets

**`historical_data.csv`** — 211,224 Hyperliquid trade executions from 32 accounts (May 2023 – May 2025).
Key columns: `Account`, `Coin`, `Execution Price`, `Size Tokens`, `Size USD`, `Side`, `Timestamp IST`, `Direction`, `Closed PnL`, `Fee`.

**`fear_greed_index.csv`** — Daily Bitcoin Fear & Greed Index (Feb 2018 – May 2025).
Columns: `date`, `value` (0–100 score), `classification` (Extreme Fear / Fear / Neutral / Greed / Extreme Greed).

## Requirements

- Python 3.9+
- Packages: `pandas`, `numpy`, `matplotlib`, `seaborn`, `ipykernel` (for running in VS Code / Jupyter)

Install everything with:

```bash
pip install pandas numpy matplotlib seaborn ipykernel
```

## How to Run

1. Make sure `trader_sentiment_analysis.ipynb`, `historical_data.csv`, and `fear_greed_index.csv` are all in the same folder.
2. Create an empty folder named `figures` in that same directory (the notebook saves chart images there):
   ```bash
   mkdir figures
   ```
3. Open the folder in VS Code (or Jupyter Lab/Notebook).
4. Open `trader_sentiment_analysis.ipynb`, select a Python kernel/interpreter, and run all cells (**Run All**, or `Shift+Enter` cell by cell).

The notebook will:
- Load and clean both datasets
- Merge trades with daily sentiment classification
- Generate 12 visualizations (saved to `figures/`)
- Produce sentiment-wise and symbol-wise performance tables
- Print business insights, recommendations, limitations, and an executive summary as markdown output

## Key Findings

- **Performance is U-shaped across sentiment, not linear.** Traders performed worst in Extreme Fear (76.2% win rate, $71.03 avg PnL/trade) and best in Extreme Greed (89.2%, $130.21 avg PnL/trade), with Fear as a strong second-best regime.
- **Position sizing is inversely related to edge.** Traders take their largest average positions in Fear ($7,816) and smallest in Extreme Greed ($3,112) — the opposite of what their own performance would justify.
- **Sell pressure rises with euphoria.** Buy share falls from 51.1% (Extreme Fear) to 44.9% (Extreme Greed), consistent with profit-taking into strength.
- **Sentiment score is a weak daily PnL predictor** (correlation ≈ -0.098) — better used as a regime-level risk overlay than a daily trading signal.
- **Meme/narrative coins** (TRUMP, FARTCOIN, MELANIA, BERA, KAITO) were the worst-performing symbol in every sentiment regime.

Full details, charts, and methodology are in the notebook and the Word report.

## Limitations

- No explicit `leverage` column exists in the source data; `Size USD` is used as a position-size/exposure proxy throughout.
- The dataset covers only 32 unique trader accounts — results may reflect a specific (possibly semi-professional) cohort rather than the broader market.
- Win rate and average PnL/trade are calculated on closed trades only (`Closed PnL ≠ 0`); trade-opening executions are excluded from those two metrics.

## Author

Pawan — B.Tech Information Technology, IEC College of Engineering & Technology, Greater Noida
