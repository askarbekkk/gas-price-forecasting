# Henry Hub Natural Gas Price Forecasting

Monthly forecast of Henry Hub natural gas prices 1, 2, and 3 months ahead, using a
strict walk-forward backtest so no future information ever leaks into a prediction.

I compared a naive random-walk baseline against Ridge, Lasso, and an Optuna-tuned
LightGBM model, one model per horizon, trained on 8 engineered features (price lags,
calendar seasonality, and a gas storage delta). LightGBM beat the baseline at every
horizon, both during validation and on the true 2020–2024 test backtest — a period
that happens to include the 2021 Texas freeze and the 2022 Ukraine-driven price
spike. The notebook also includes a SHAP-based error analysis of specific moments
where the model missed, mostly around sudden, one-off supply/demand shocks that a
lagged-price feature set can't anticipate.

## Contents

- `solution.ipynb` — full pipeline, executed end-to-end
- `submission.csv` — final 1/2/3-month forecasts
- `report.pptx` — summary slide deck
- `requirements.txt` — exact dependencies

Raw input data isn't included — it was provided privately for a coding exercise.

## Run it

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute --inplace solution.ipynb
```
