# Xbox Game Pass – Excel Dashboard

This project shows the end-to-end creation of a sales dashboard for Xbox Game Pass subscriptions in Excel, from the raw data table through pivot-table analysis to the final management dashboard.

## Files

- `base_dashboard_DIO.xlsx` – starter workbook containing:
  - **Assets**: colour palette and visual references.
  - **Bases**: full subscription dataset.
  - **Cálculos / Dashboard**: empty sheets to be built by the user.

- `dashboard_finalizado_DIO.xlsx` – reference workbook with:
  - Completed pivot-table calculations on **Cálculos**.
  - Final dashboard layout and title on **Dashboard**.

## Data structure

The sheet **Bases** contains one row per subscriber, with the main fields:

- `Subscriber ID`, `Name`, `Plan`, `Start Date`, `Auto Renewal`
- `Subscription Price`, `Subscription Type`
- `EA Play Season Pass`, `EA Play Season Pass Price`
- `Minecraft Season Pass`, `Minecraft Season Pass Price`
- `Coupon Value`, `Total Value`

The sheet **Assets** provides the colour palette (Xbox green, menu colours and “negative zone”) and serves as a design reference for the dashboard.

## Data preparation

1. Convert the **Bases** range into an Excel Table (`tblBases`).
2. Make sure categorical fields are standardised (e.g. `Yes/No`, `Monthly/Quarterly/Annual`).
3. Ensure numeric fields are formatted as numbers.
4. Optionally, recompute `Total Value` with a formula to validate the dataset.

## Business questions (pivot tables)

All analysis is built in the sheet **Cálculos** using pivot tables based on `tblBases`.

1. **Business Question 1** – Total revenue from annual plans (all annual subscriptions aggregated).  
   - Filter: `Subscription Type = Annual`  
   - Values: Sum of `Total Value`.

2. **Business Question 2** – Total revenue from annual plans split by auto-renewal.  
   - Filter: `Subscription Type = Annual`  
   - Rows: `Auto Renewal`  
   - Values: Sum of `Total Value`.

3. **Business Question 3** – Total revenue from EA Play Season Pass.  
   - Filter: `Subscription Type = Monthly`  
   - Rows: `Plan`  
   - Values: Sum of `EA Play Season Pass`.

4. **Business Question 4** – Total revenue from Minecraft Season Pass.  
   - Filter: `Subscription Type = Monthly`  
   - Rows: `Plan`  
   - Values: Sum of `Minecraft Season Pass Price`.

For each pivot table, a dedicated cell in **Cálculos** stores the main KPI (Grand Total), which is then linked to the dashboard.

## Dashboard

The sheet **Dashboard** presents a management view titled **“XBOX GAME PASS SUBSCRIPTIONS SALES”**, built with:

- Cards showing:
  - Total annual revenue.
  - Annual revenue split by auto-renewal (Yes/No).
  - Total EA Play revenue.
  - Total Minecraft Season Pass revenue.
- Formulas in each card pointing to the KPI cells in **Cálculos**.
- Colours taken from **Assets**, using Xbox greens for emphasis and neutral tones for background areas.

This workbook can be used as a template for basic sales analytics and dashboard design in Excel.
