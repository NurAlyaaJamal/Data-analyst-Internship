# Automated Inventory Control Dashboard System with Forecasting (Excel)

Practicum project for **SQQXK49512**, Universiti Utara Malaysia (UUM), carried out at **The House of Taste Sdn Bhd**, Kuala Lumpur.

An Excel workbook that turns the daily pantry stock count and the storehouse records of the **Uber Pantry** into a live dashboard, a ranked purchase order, ABC/XYZ classes, safety stock and reorder points, and forecast and data accuracy checks. Management enters only the daily counts and storehouse movements, and everything else is calculated by formulas.

> **Author:** Nur Alyaa binti Jamal (Matric 294262)
> **Supervisor (UUM):** Dr Nurul Najiha binti Jafery
> **Status:** Practicum project, September 2026 data

---

## Why this project

The Uber Pantry stock records were kept in separate sheets, and the purchase estimate was rebuilt by hand every time. There was no single view of what was running out, what to order, or how reliable the estimate was. This workbook links the sheets and adds the controls below.

## Features

- **Dashboard** with filters for week, category, flavour profile, date, day, brand and item. It has separate Pantry and Storehouse sections.
- **Stock status** for each item: Out of stock, Critical (3 days or less of cover), Low (7 days or less), Watch (14 days or less), Healthy and No usage.
- **Purchase order** that lists only items that need ordering, most urgent first, in cartons and units with estimated cost.
- **ABC and XYZ classification.** ABC uses 80% and 95% value cut-offs. XYZ uses coefficient of variation cut-offs of 0.5 and 1.0.
- **Safety stock and reorder point** from a lead time and a service level.
- **Storehouse reconciliation** of stock out, spoiled or damaged units and stock received, plus the physical count tally.
- **Preference index and trend** to flag low-preference items for phase-out or review.
- **Accuracy Check** with data validation checks, 95% confidence intervals, outlier days, a forecast back-test (MAE, WAPE, bias, tracking signal) and a stock-out record.

## Workbook structure

| Sheet | Purpose |
|---|---|
| Pantry Inventory | Daily opening stock, stock in, closing stock and consumption per item, in weekly blocks |
| Storehouse Replenishment Schedule | Stock out to the pantry, stock in from suppliers, spoiled or damaged units, closing stock and physical count |
| Daily Data | Formula sheet that reshapes the pantry counts into one row per item per day |
| Item Purchases | Purchase estimate, status, ABC/XYZ class, safety stock, reorder point, preference verdict and all settings |
| Purchase Order | Draft purchase order of items to order, most urgent first |
| Accuracy Check | Data checks, confidence intervals, outlier days, forecast back-test, stock-out record |
| Dashboard | Pantry and storehouse insights with filters |

**Only manual inputs:** the daily closing counts (Pantry Inventory), the storehouse movements and physical count (Storehouse Replenishment Schedule), and a few settings in Item Purchases.

## Methods

| Indicator | Definition |
|---|---|
| Average daily use | Total consumption divided by the counted days on which the item was in stock |
| Days of cover | Stock remaining (pantry + storehouse) divided by average daily use |
| Estimated need | Average daily use multiplied by the days to the cover-until date, minus stock remaining |
| Safety stock | z × standard deviation of daily use × √(lead time) |
| Reorder point | Average daily use × lead time + safety stock |
| Default settings | Lead time 5 days, service level 95% (z = 1.645) |
| Preference index | Item average daily use divided by the average of active items in the same category |
| Forecast back-test | First 70% of counted days to learn, remaining days to test; MAE, WAPE, bias, tracking signal (±4) |

## Results (September 2026, 22 counted days)

- 26 items, 15 brands (11 snacks, 15 beverages); 5,172 units consumed, worth RM10,290.19.
- 11 Class A items make up 80.7% of consumption value.
- 22 items need ordering: 354 cartons, 4,939 units, about RM9,575.52.
- Overall forecast WAPE is 41.3%, so the forecasts are indicative only.

See the full report for the analysis and recommendations.

## How to use

1. Open the workbook in **Microsoft Excel** (desktop version recommended, so that formulas and charts refresh correctly).
2. Enter the closing stock for each item on each working day in **Pantry Inventory**.
3. Record stock out, stock in, spoiled units and the month-end physical count in **Storehouse Replenishment Schedule**.
4. Check or change the settings (lead time, service level, cover-until date, unit prices, carton sizes) in **Item Purchases**.
5. Open **Dashboard** to see stock status and use the filters. Open **Purchase Order** for the items to order, and **Accuracy Check** to confirm the data checks pass before relying on the order.

To reuse the workbook for another month or outlet, update the item list and the dates, and keep item names identical across all sheets.

## Repository contents

```
.
├── README.md
├── workbook/      # Excel workbook (use the sample or anonymised version, see note below)
├── report/        # Practicum report (Word/PDF)
└── images/        # Dashboard screenshots
```

## Limitations

- Only one month of data (22 counted days), so seasonality and trends could not be studied.
- Demand during stock-outs is not observed and may be understated.
- The forecast is the average daily use, with no trend or weekday effect.
- Prices, carton sizes and the 5-day lead time are fixed settings and should be confirmed with suppliers.

## Possible next steps

- Test a moving average or exponential smoothing with a weekday effect, using at least three months of data.
- Reuse the workbook for the other outlets.
- Connect the workbook to Power BI or Power Query for automatic refresh.

## Data and confidentiality

The workbook contains operating records and prices of The House of Taste. Only dummy data is used to imitates the real situation.

## Acknowledgement

Thanks to The House of Taste Sdn Bhd for the placement and to Universiti Utara Malaysia for supervision.

Company data stays the property of The House of Taste Sdn Bhd.
