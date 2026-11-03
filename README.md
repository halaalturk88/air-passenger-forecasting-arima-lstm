# Air Passenger Forecasting: ARIMA vs LSTM

**Type:** Academic Machine Learning / Deep Learning project  
**Focus:** Time Series Analysis, Forecasting, ARIMA, LSTM

## Overview
This project explores monthly airline passenger forecasting using classical time-series modeling (**ARIMA**) and a recurrent neural network (**LSTM**). The notebook visualizes trends and seasonality, tests stationarity using the Augmented Dickey-Fuller test, and compares forecasting approaches.

## Workflow
- Parse monthly passenger counts from `AirPassengers.csv`.
- Explore the time series through plots, seasonal decomposition, differencing, ACF and PACF.
- Fit an ARIMA (2,1,1) model with one-step rolling forecasts using an 80/20 chronological split.
- Build a tuned LSTM using 24-step input windows, log transformation, differencing, MinMaxScaler and Keras Tuner Bayesian optimization.
- Evaluate forecasts with RMSE, and R² (ARIMA also reports MAE).

## Results recorded in the original notebook

| Model | RMSE | R² | Other metric |
| --- | ---: | ---: | --- |
| ARIMA rolling forecast | 44.218 | 0.680 | MAE: 37.713 |
| Tuned LSTM | 20.45 | 0.9250 | — |

**Important:** These numbers are from saved notebook outputs, not independently reproduced in this repository. The model comparisons are illustrative, not a controlled apples-to-apples benchmark: the ARIMA evaluation updates with true observations in its rolling history, while the LSTM pipeline fits its scaler before splitting the windows into training and test sets (possible data leakage). The LSTM forecast reconstruction also uses the preceding true log value. A stronger evaluation would fit transformations on the training period only and use a shared forecasting protocol.

## Files
- `air_passenger_forecasting.ipynb` — original notebook, with its dataset path changed to a relative local path.
- `docs/Air_Passenger_Forecasting_Presentation.pptx` — original course presentation.
- `requirements.txt` — packages used in the notebook (un-pinned; compatibility can vary).
- `data/README.md` — expected data location.

## Run locally
1. Install Python and Jupyter Notebook or use Jupyter in VS Code.
2. Install dependencies: `python -m pip install -r requirements.txt`.
3. Obtain the **AirPassengers.csv** dataset from an authorized source. Ensure it has the `Month` and `#Passengers` columns, and save it as `data/AirPassengers.csv`.
4. Open `air_passenger_forecasting.ipynb` and run cells from top to bottom.

The LSTM tuner can take time and may write local output files to `tuning_results/`, which are excluded by `.gitignore`.

## Project context
University coursework demonstrating practical exposure to time-series forecasting and deep learning. No work experience, deployment, or verified production performance is claimed.
