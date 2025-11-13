📈 Marketing Mix Modeling (MMM) – Basic End-to-End Project

A simple, educational Marketing Mix Modeling (MMM) pipeline built in Python.
This project simulates a realistic marketing dataset, applies adstock transformations, fits an OLS regression model, evaluates the contributions of each channel, and visualizes key insights.

Perfect for learning MMM fundamentals or showcasing analytical skills in a portfolio.

Overview

This project demonstrates how Marketing Mix Modeling can be used to understand the impact of different marketing channels on a business KPI — in this case, daily registrations.
The project includes:

Synthetic data generation for 2 years of daily marketing activity
Modeling of baseline demand, trend, and weekly seasonality
Adstock transformations to account for carryover effects
OLS regression using statsmodels
Model diagnostics (coefficients, confidence intervals, VIF)
Visualization of spend patterns, registrations, predicted vs actual, and channel contributions


Data
Because real marketing datasets are hard to access, this project generates synthetic data that mimics real-world behavior:
date — 2 years of daily timestamps
baseline — natural demand without marketing
trend — long-term growth in demand
seasonality — weekly repeating patterns (weekend uplift)
facebook_spend — daily ad spend
search_spend — daily ad spend
display_spend — daily ad spend
adstock_facebook/search/display — transformed spend capturing carryover
registrations — simulated business outcome (KPI), influenced by marketing and natural factors

This allows you to learn MMM techniques without relying on private or sensitive datasets.

Methodology
1. Data Simulation

The script generates realistic marketing and business data including:
baseline demand
upward trend
weekly cycles
marketing spend for 3 channels
noise to mimic real-world randomness

2. Adstock Transformation
Marketing impact lingers beyond the day of spend.
Adstock is applied using:
adstock_t = spend_t + decay * adstock_(t−1)
This models how advertising effects fade over time.

3. OLS Regression (MMM Model)
We fit an OLS regression using:
trend
seasonality
adstock_facebook
adstock_search
adstock_display
The model quantifies how each factor contributes to registrations.

4. Model Evaluation
The script prints:
coefficients
confidence intervals
multicollinearity (VIF)
condition number
These help ensure the model is stable and interpretable.

Results

Key takeaways from the model:
Search is the strongest contributor to registrations
Facebook has moderate impact
Display contributes least
Demand grows naturally over time (+1 per day)
Weekends significantly boost registrations
Baseline demand is captured via the regression intercept
These align with the simulated “true” marketing effectiveness values.

Plots

The project generates several visualizations:
1. Daily Spend by Channel
Shows daily fluctuations in Facebook, Search, and Display budgets.

2. Daily Registrations
Visualizes the KPI trend over time.

3. Predicted vs Actual
Evaluates model accuracy by comparing regression predictions with actual registrations.

4. Channel Contributions
Calculates and plots:
coefficient × mean(adstocked spend)

This gives a clear sense of which channels drive the most value.

Next Steps

Potential improvements to extend this project:
Add saturation curves (e.g., Hill function)
Add diminishing returns modeling
Implement Bayesian MMM with PyMC
Build ROI and marginal ROI calculations
Create a budget optimization module
Convert this into a Jupyter Notebook with narrative explanations
Add confidence intervals for predictions

Use regularization (Ridge, Lasso) to handle noisy or real-world data
