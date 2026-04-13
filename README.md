# Ontario Healthcare System — PESTEL Data Analytics Case Study

## Overview
This was a group project for DAMO-511 (Case Study) at the University of Niagara Falls Canada. The project applied the PESTEL framework to the Ontario healthcare system, with the team dividing responsibility across the Economic, Social, and Technological factors. I was solely responsible for the Technological factor — from data sourcing and statistical analysis through to the Jupyter notebooks and the Power BI dashboard components.

The goal was not just an environmental scan but a quantified one. Rather than describing technological trends in qualitative terms, each component of my analysis was backed by a statistical test or a forecasting model with measurable error bounds. All three factors were consolidated into a shared Power BI dashboard.

## What I Worked On
I handled the entire Technological factor independently, which covered three separate analyses across three dedicated Jupyter Notebooks, plus my contributions to the shared Power BI dashboard.

The first analysis looked at virtual care adoption. Ontario's virtual consultation rates surged dramatically during COVID-19, but the more meaningful question was whether that shift was permanent. I built a quadratic time-trend regression model on year-by-year data from 2019 to 2024, capturing the pre-pandemic baseline, the peak, and the post-COVID trajectory. The model confirmed that virtual care stabilized at approximately 27% of consultations — not a temporary response, but a structural change in how care is delivered.

The second analysis focused on Electronic Medical Record adoption gaps. Physicians in Ontario have near-universal EMR adoption, but patient-side engagement with digital health records is significantly lower. I applied Two-Sample Z-Tests comparing physician usage to patient engagement rates using 2021 and 2024 survey data, confirming the gap as statistically significant. The finding pointed to a digital access or awareness barrier on the patient side rather than a system-level failure.

The third analysis was the most involved. I examined Ontario's dependency on foreign supply chains for critical diagnostic and monitoring equipment. I ran One-Sample T-Tests against a 30% safety threshold to confirm that actual North American import dependency (US and Mexico combined) sits at approximately 65% — more than double the threshold. I then computed the Herfindahl-Hirschman Index (HHI) to quantify how concentrated that supplier dependency is, and applied linear trend regression to project how long it would take to reach safe diversification under current trajectories. The result was approximately 35 years — a sobering number for healthcare planners thinking about supply chain resilience post-pandemic.

## Key Findings

**Virtual Care**
- Post-COVID stabilization at ~27% of consultations — confirmed as a permanent structural shift rather than a temporary pandemic response

**EMR Adoption**
- Statistically significant gap between physician usage (near-universal) and patient engagement — Z-Test confirmed across both 2021 and 2024 data

**Medical Equipment Supply Chain**
- 65% dependency on North American suppliers against a 30% safety threshold
- HHI indicates high supplier concentration risk
- Linear trend regression projects ~35 years to reach safe diversification at current rates


## Methodology Notes
One challenge in the virtual care analysis was that raw consultation numbers varied significantly across years due to how the data was collected and categorized, particularly around the distinction between telephone and video visits. Getting consistent definitions across the 2019–2024 banner tables required careful cleaning before any model could be fit. The supply chain analysis similarly required building the trade share dataset from import reports that were not structured for direct statistical use out of the box — some of the most time-consuming work in the project was just getting the data into a shape where the T-Tests and HHI calculations made sense.

## Data Sources
- Canadian Institute for Health Information (CIHI) — virtual care and EMR data
- Statistics Canada — population and demographic data
- Health InfoBase Canada — physician and workforce indicators
- Ontario Ministry of Health — regional health technology data
- Trade import reports — medical equipment supply chain composition

## Tech Stack
Python, Jupyter, Pandas, Matplotlib, SciPy, StatsModels, Power BI, Excel

## How to Run

1. Clone the repository
2. Run `pip install jupyter pandas matplotlib scipy statsmodels openpyxl`
3. Open any notebook from the `notebooks/` folder in Jupyter
4. Run cells top to bottom with `Shift + Enter`
5. To view the dashboard, open `dashboard/Case_Study_Dashboard.pbix` in Power BI Desktop (free)

Note: If you get a `FileNotFoundError`, update the data path at the top of the notebook to match your local `data/` folder structure.

## What I Would Do Next
- Replace the Euclidean-equivalent distance assumptions in the virtual care access analysis with actual regional mapping to understand which specific communities are most affected by the digital access gap.
- Extend the supply chain analysis to include a scenario model — what does Ontario's equipment dependency look like under different diversification investment levels over a 10-year horizon rather than just projecting the current trajectory forward.
