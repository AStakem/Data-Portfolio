NFL Predictive Analysis
================
Andrew Stakem
2026-02-03

## Project Overview

This project features an ensemble machine learning pipeline designed to
predict NFL game outcomes Against the Spread (ATS) and Outright (SU). By
utilizing walk-forward validation on the 2025 season, the project
simulates a real-time production environment, proving the model’s
efficacy under true “out-of-sample” conditions.

------------------------------------------------------------------------

### Phase 1: Model Reliability (Calibration)

#### Moneyline Calibration

<figure>
<img src="images/ML_CAL_PLOT.png" alt="ML Calibration" />
<figcaption aria-hidden="true">ML Calibration</figcaption>
</figure>

#### Against the Spread (ATS) Calibration

<figure>
<img src="images/ATS_CAL_PLOT.png" alt="ATS Calibration" />
<figcaption aria-hidden="true">ATS Calibration</figcaption>
</figure>

**The Analysis:** A model is only as good as its probability estimates.
These calibration plots prove that as the model’s confidence increases,
its success rate follows linearly.

**Key Finding:** The model demonstrated elite calibration in the 70-80%
confidence bucket, hitting at a 71.4% clip. Crucially, every confidence
bucket remained above the 52.4% breakeven mark, confirming a sustainable
statistical edge over the sportsbooks’ “vig.”

------------------------------------------------------------------------

### Phase 2: Profitability & Risk Management (Wealth Curve)

<figure>
<img src="images/Profit_Plot.png" alt="Wealth Curve" />
<figcaption aria-hidden="true">Wealth Curve</figcaption>
</figure>

**The Analysis:** This visual tracks three distinct betting strategies
across 272 games. It highlights the trade-off between volume and
precision.

**Key Finding:** The “High Conviction” (\>70%) strategy achieved a 68.9%
accuracy rate, capturing the majority of the season’s total profit while
significantly reducing exposure.

**The “Seasonality” Surge:** There is a noticeable uptick in
profitability after game 150. This suggests that the model’s power
ratings “converged” on the true strength of the teams once the
mid-season noise was smoothed out, leading to a dominant fourth-quarter
performance.

------------------------------------------------------------------------

### Phase 3: Precision & Error Diagnostics (Residuals)

<figure>
<img src="images/res_plot.png" alt="Residual Distribution" />
<figcaption aria-hidden="true">Residual Distribution</figcaption>
</figure>

**The Analysis:** This density plot audits the regression model’s
score-gap predictions.

**Key Finding:** While the model is highly accurate, the “wavy” left
tail in the distribution reveals a “Blowout Blindness.” Analysis of the
outliers (e.g., Week 18 Miami/NYJ) shows the model struggles with
late-season motivation shifts where teams “quit” or rest starters.

**Technical Maturity:** Identifying this non-normal distribution
demonstrates the ability to diagnose model limitations and propose
future feature engineering (e.g., a late-season “Motivation Index”).

------------------------------------------------------------------------

### Final Analysis Note for Recruiters

The core strength of this project is not just the 62.5% - 68.9% ATS
accuracy, but the rigorous validation framework. The model correctly
identifies a significant late-season edge, proving it can find market
inefficiencies as the season matures.
