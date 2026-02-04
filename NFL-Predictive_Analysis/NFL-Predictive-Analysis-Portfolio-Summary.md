NFL Predictive Analysis
================
Andrew Stakem
2026-02-03

## Project Overview

This project features an ensemble machine learning pipeline designed to
predict NFL game outcomes Outright (ML) and Against the Spread (ATS). By
utilizing walk-forward validation on the 2025 season, the project
simulates a real-time production environment, proving the model’s
efficacy under true “out-of-sample” conditions.

------------------------------------------------------------------------

### Phases and Methods

The project consisted of three phases. Phase one is a model calibration
analysis for both the ML and ATS. This analysis sought to identify the
percentage of actual correct predictions based on the percent confidence
of the model. Will games that feature a 70% prediction for a given
outcome be correct 70% of the time? Phase two is a profitability
analysis if games were wagered ATS based on the model’s predictions. If
you use this model as a betting tool will it be profitable over the
course of a season? And the third phase is an analysis of the built-in
regression model’s score-gap predictions. Does the regression model
accurately predict the difference in score at the end of the game?

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

**The Analysis:** These calibration plots prove that as the model’s
confidence increases, its success rate follows linearly. In the
Moneyline Calibration Plot the model operates at about 10% below the
target line. The target line indicating a perfect calibration 50%/50%,
60%/60%, etc. The model did show increased accuracy as confidence levels
increased which indicates that the aggregated models and the features
present correlate confidence with successful predictions. The models
will still require refinement in order to strengthen the calibration.
The Against the spread calibration plot features a target line as well
as a break even line. The break even line (52.4%) indicates the level of
accuracy that would be required to break even if betting on the games
based on the predictions. The trend line indicates results comfortably
above the break even line regardless of confidence level. However there
is a lack of consistent upward trend as the confidence levels increase.
The accuracy remains stagnant and then spikes between 65% and 75% where
the 75% calibration is almost perfectly accurate. This shows a clear
“sweet spot” for using this model to confidently predict games. The
troubling factor is that after 75% the accuracy drops back down to the
mid 50% confidence levels of the other buckets used for the plot. An
investigation into the features and model functioning will be required
to identify why the calibration is inconsistent as confidence increases.
And just like the ML plot, the ATS calibration plot’s the models will
require refinement in order to produce a stronger correlation between
the confidence and correct results.

**Key Finding:** The ML model demonstrated a strong correlation between
increased confidence and accuracy showing value in using trusting the
model as confidence levels increase. The ATS model demonstrated elite
calibration in the 70-80% confidence bucket, hitting at a 71.4% clip.
Crucially, every confidence bucket remained above the 52.4% breakeven
mark, confirming a sustainable statistical edge over the sportsbooks’
“vig.”

------------------------------------------------------------------------

### Phase 2: Profitability & Risk Management (Wealth Curve)

<figure>
<img src="images/Profit_Plot.png" alt="Wealth Curve" />
<figcaption aria-hidden="true">Wealth Curve</figcaption>
</figure>

**The Analysis:** This visual tracks three distinct betting strategies
across 272 games only focusing on Against the Spread betting. It
highlights the trade-off between volume and precision using three
separate strategies, betting every game, betting only games with over
60% confidence and betting only games with over 70% confidence. A “Unit”
for the purposes of the plot is one standard wager amount. When a bet is
lost that is minus one unit and when a bet is won that is plus one unit.
For the purposes of accuracy we have to consider a 2.5% vig to the
sportsbook when wagers are won. This can be factored into the net result
on the plot. The trends clearly show value in every strategy with each
one resulting in a significant net-positive in units gained over the
course of the season. The strategy of betting every game will net the
most units gained, while the 60% strategy is next followed by the 70%
strategy. However, the accuracy levels are the inverse of the units
gained so depending on your needs as a user, the more efficient play
featuring the lowest risk is the 70% confidence level while the least
efficient play but featuring the highest potential profit is the bet
every game strategy. **The “Seasonality” Surge:** There is a noticeable
uptick in profitability after game 150. This suggests that the model’s
power ratings “converged” on the true strength of the teams once the
mid-season noise was smoothed out, leading to an incredibly strong
second half of the season.You can even adjust the models used depending
the time of year to limit losses early and then maximize profit late.

**Key Finding:** All strategies would be profitable based on the
outcomes of the 2025 season. The “High Conviction” (\>70%) strategy
achieved a 68.9% accuracy rate, capturing the majority of the season’s
total profit while significantly reducing exposure.

------------------------------------------------------------------------

### Phase 3: Precision & Error Diagnostics (Residuals)

<figure>
<img src="images/res_plot.png" alt="Residual Distribution" />
<figcaption aria-hidden="true">Residual Distribution</figcaption>
</figure>

**The Analysis:** This density plot audits the regression model’s
score-gap predictions. This is one model feature that will require
significant refinement in order to smooth out the bell curve. There is
significant error on both sides of the predictions indicating that there
is little validity in the regression model’s predictions. The width and
depth of the error curve at the extremes show that there are many score
outcomes that are never considered by the predictions because large
score gaps are not accounted for in the results. Something to consider
along with the results of this plot are the results of the ML
calibration plot. The models generally predict the correct team to win
so the predicted side for the score gap prediction is generally correct
but it does poorly in predicting the score outcome accurately.

**Key Finding:** While the model is highly accurate, the “wavy” left
tail in the distribution reveals a blind spot when it comes to blowouts
or large score gaps. There are model limitations that must be addressed
and corrected in order to put much confidence in the score gap feature
of the model.

------------------------------------------------------------------------

### Final Analysis Note

The core strength of this project is not just the 62.5% - 68.9% ATS
accuracy, but the rigorous validation framework. The model correctly
identifies a significant late-season edge, proving it can find market
inefficiencies as the season matures.
