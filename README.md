# Greek Electricity Demand Forecasting

## Overview

This project forecasts hourly electricity load in Greece using machine learning. We compare three forecasting approaches to predict demand based on historical load patterns and weather data.

**Result:** Linear Regression with engineered features achieves **4.95% MAPE**, outperforming both a simple baseline and a complex Prophet model.

## Problem Statement

Greece's electricity grid requires accurate demand forecasting for:
- Efficient power generation scheduling
- Renewable energy integration planning
- Cost optimization and resource allocation

This project demonstrates that simple, interpretable models can outperform complex ones when combined with domain-relevant features.

## Data

### Sources
- **Electricity Load:** ENTSO-E Transparency Platform (2023-2026, hourly)
- **Weather:** Open-Meteo API (Athens coordinates, hourly temperature)

### Dataset
- **Time Period:** January 2023 – December 2026
- **Frequency:** Hourly (31,500+ observations)
- **Variables:** Load (MW), Temperature (°C)

## Models Tested

| Model | MAPE | Training Time | Complexity |
|-------|------|---------------|-----------|
| **Linear Regression** | **4.95%** ✓ | < 1 sec | Low |
| Baseline (Lag-168) | 7.39% | Instant | Minimal |
| Prophet v2 | 7.86% | 1-2 min | High |

## Key Findings

### Model Performance
- **Linear Regression wins** with 4.95% mean absolute percentage error
- Lagged load features (especially 168-hour lag) are the strongest predictors
- Complex Prophet model underperforms despite more sophisticated approach

### Where Each Model Struggles
- **Peak Hours (2-4pm):** Highest error (~9.8%) — volatile demand patterns
- **August:** Highest seasonal error (~8.4%) — extreme AC usage
- **Overnight (4-5am):** Lowest error (~5.7%) — stable, predictable demand

### Insights
1. Simple lag-based features capture demand patterns better than learned seasonality
2. Temperature effects are significant but secondary to temporal patterns
3. Linear relationships work well for electricity load forecasting
4. Over-engineering with Prophet adds complexity without accuracy gains

   ### Required Packages
- pandas — data manipulation
- numpy — numerical computing
- matplotlib — visualization
- scikit-learn — Linear Regression model
- prophet — time series forecasting
- entsoe-py — ENTSO-E API client
- openmeteo-requests — weather API client


  ## Results

### Visualizations Included
- **Hourly Patterns:** Load variation across 24 hours, all models compared
- **Daily Trends:** Day-by-day forecast accuracy
- **Seasonal Patterns:** Monthly load variation and model performance
- **Error Analysis:** Where and when the baseline forecast fails
- **Model Comparison:** MAPE across three approaches

### Highlights
- Linear Regression achieves 4.95% error on 2025-2026 test set
- Model generalizes well across seasons and daily cycles
- Lagged load (168-hour) is the single strongest feature

## Limitations

- **Perfect weather assumption:** Uses actual temperature (mild data leakage); real forecasts would need weather predictions
- **No holiday modeling:** Excludes Greek holidays; could improve accuracy for special days
- **Single country:** Results specific to Greek demand patterns; may not generalize to other grids
- **Linear model ceiling:** Doesn't capture nonlinear interactions; ensemble methods could improve further
- **4-year window:** Limited to 2023-2026; longer historical context could help

## Future Improvements

1. **Add official ENTSO-E forecast** as a baseline for comparison
2. **Implement ensemble methods** combining Linear Regression + Prophet
3. **Include holiday flags** for Easter, August 15, New Year
4. **Model volatility separately** for peak-hour prediction
5. **Geographic expansion** to regional demand forecasting
6. **Power BI Dashboard** for interactive exploration

## Technologies Used

- **Python 3.x** — data processing and modeling
- **Scikit-learn** — Linear Regression
- **Prophet** — time series forecasting
- **Pandas/NumPy** — numerical computing
- **Matplotlib** — data visualization
- **ENTSO-E API** — real electricity data
- **Open-Meteo API** — weather data


### Power BI Dashboard
- Interactive visualization of demand patterns
- Hourly, weekly, and seasonal trends
- Temperature correlation analysis
- Data model with proper relationships



## Author

Giorgos — Data Analyst & Mathematics Student

## Contact

For questions or suggestions, feel free to open an issue or reach out.

## License

This project is open source and available under the MIT License.

---

**Last Updated:** August 2026
