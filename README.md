 NIFTY50 Implied Volatility Surface Reconstruction

Finance Club IIT Roorkee — Open Project 2026

Objective

Reconstruct the 5,460 missing implied volatility (IV) values in a partially observed NIFTY50 option surface and minimize Mean Squared Error (MSE) against the hidden ground-truth IVs.

This is a surface reconstruction problem, not a forecasting problem.



Dataset

* 975 timestamps
* 13 trading days
* 5-minute frequency
* 07-Jan-2026 → 27-Jan-2026
* Single expiry: 27-Jan-2026
* 14 Call strikes + 14 Put strikes
* 27,300 total IV cells
* 5,460 hidden cells (20%)

Input:

* datetime
* underlying_price
* observed option IVs

Output:

 complete IV surface with no missing values

---

 Approach

The pipeline reconstructs the IV surface using:

1. Cross-sectional smile reconstruction
2. Moneyness and expiry structure
3. Historical IV dynamics
4. Residual learning via Gradient Boosting
5. Time-aware ensemble modelling

Instead of predicting IV directly, the model learns:

Residual = Observed IV − Surface IV

which improves stability and reduces prediction variance.

---

 Validation

Performance is evaluated through leakage-free reconstruction validation using strictly chronological folds.

All predictions are generated using information available at or before the prediction timestamp.

---

 No-Lookahead Guarantee

The solution prohibits:

* Future timestamps
* Future IV values
* Future underlying prices
* Lead variables
* Forward-looking rolling statistics
* Target leakage
* Fold contamination

Only historical and same-timestamp information is used.

---

Deliverables

 filled_dataset.csv
 submission.csv
 Complete reconstruction notebook

---

Goal

Recover the hidden implied-volatility surface as faithfully as possible while preserving smile structure, temporal consistency, and strict competition compliance.

Success is measured solely by the accuracy of the reconstructed hidden IV values.
