# Car Sales Dashboard (Power BI and Excel)
 
Two interactive dashboards built on the **same car sales dataset**: one in **Power BI** and one in **Excel**. Both show sales performance across companies, regions, customer groups, and time.
 
| Dashboard | Tool | Theme |
|-----------|------|-------|
| Part 1 | Power BI | Dark side panel, company filter, BMW drill-down page |
| Part 2 | Excel | Blue theme, Male/Female slicers, sidebar company totals |
 
## About the Project
 
This is a beginner project I made to learn data analysis and dashboard design. My goal was to take a raw car sales dataset, clean it, and turn it into dashboards that answer simple business questions such as:
 
- How many cars were sold, and how much revenue did we make?
- Which company sells the most cars?
- Which dealer region performs best?
- Which income group buys the most cars?
- How do sales change by day of the week, by month, and from year to year?
I built the dashboard twice, first in Power BI and then in Excel, to understand the strengths of each tool.
 
---
 
# Part 1: Power BI Dashboard
 
<img width="1920" height="956" alt="Car Sales" src="https://github.com/user-attachments/assets/80259b8d-6429-41d2-b53b-675a70962daa" />
<img width="1920" height="966" alt="Car Sales (2)" src="https://github.com/user-attachments/assets/7ec67dba-b9fd-4d4e-bb42-d59a101d6061" />
 
> Add your screenshots to the repository and rename them to match the file names above (or update the links).
 
## Key Numbers (KPI Cards)
 
| KPI | All Companies | BMW |
|-----|---------------|-----|
| Total Transaction | 24K | 790 |
| Total Revenue | 672M | 20M |
| Average Order Value | 28.09K | 25.09K |
| YoY Growth | 24.57% | 28.99% |
 
- **Total Transaction:** number of cars sold
- **Total Revenue:** total sales amount
- **Average Order Value:** revenue divided by number of transactions
- **YoY Growth:** growth compared with the previous year
## Pages
 
### Page 1: Dashboard (Overall Sales)
 
| Visual | Chart Type | What It Shows |
|--------|-----------|---------------|
| Total Quantity by Month and Year | Line chart | Monthly sales trend, 2022 compared with 2023 |
| Total Quantity by Gender | Donut chart | Split of buyers by male and female |
| Total Quantity by Dealer_Region | Bar chart | Sales by dealer city (Austin is highest at 4.1K) |
| Total Quantity by Income Group | Bar chart | Sales by customer income range ($900K+ buys the most at 10.7K) |
| Total Quantity by Company | Column chart | Cars sold per brand (Chevrolet leads with 1819) |
 
### Page 2: BMW Report (Drill-Down)
 
Choose **BMW** in the company filter to see BMW-only data.
 
| Visual | Chart Type | What It Shows |
|--------|-----------|---------------|
| Average Order Value by Month and Year | Column chart | Average order value for each month, 2022 vs 2023 |
| Total Quantity by Model | Donut chart | Sales split across BMW models (528i, 323i, 328i) |
| Dealer_Region | Map | Where BMW dealers are located across the USA |
| Total Revenue and Count of Dealer_Name by Month | Combo chart | Monthly revenue (columns) and number of dealers (line) |
| CY Total Quantity by Year and Month | Line chart | Running growth of BMW sales through 2022 and 2023 |
 
## Power BI Features
 
- **Company filter:** a "Search Company" dropdown that updates every chart on the page
- **Home and back buttons:** easy navigation between pages
- **Custom design:** dark side panel with a car image, rounded KPI cards, and a light background
- **Year comparison:** 2022 and 2023 shown side by side
- **Map visual:** shows dealer locations geographically
## Data Model
 
| Table | Purpose |
|-------|---------|
| `car+sales+cleaned (1)` | Main sales data (company, model, gender, income, dealer, price, date) |
| `Calendar Table` | Date table used for month, year, and YoY calculations |
| `Measure` | Holds all the DAX measures |
| `Sheet1` | Extra helper data |
 
## Sample DAX Measures
 
These are example formulas to show the idea. Change the table and column names to match your file.
 
```DAX
Total Transaction = COUNTROWS('car+sales+cleaned (1)')
 
Total Revenue = SUM('car+sales+cleaned (1)'[Price])
 
Average Order Value = DIVIDE([Total Revenue], [Total Transaction])
 
CY Revenue = CALCULATE([Total Revenue], YEAR('Calendar Table'[Date]) = 2023)
 
PY Revenue = CALCULATE([Total Revenue], YEAR('Calendar Table'[Date]) = 2022)
 
YoY Growth = DIVIDE([CY Revenue] - [PY Revenue], [PY Revenue])
```
 
## How to Open the Power BI File
 
1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows only).
2. Download this repository:
```bash
   git clone https://github.com/abinanthan1/CarSalesDashboard.git
```
3. Open the `CarSalesDashboard.pbix` file in Power BI Desktop.
4. If asked, click **Refresh** to load the data. If the data source path breaks, go to **Home > Transform data > Data source settings** and point it to your local data file.
5. Use the **Search Company** dropdown to filter the dashboard.
---
 
# Part 2: Excel Dashboard
 
<img width="1766" height="982" alt="Car sales(3)" src="https://github.com/user-attachments/assets/adde74fd-a8bf-4199-9534-789787f46603" />

 
> Add your Excel screenshot to the repository as `Excel_Dashboard.png` (or update the link).
 
## Overview
 
The Excel dashboard is titled **"Turn Dreams into Drives"**. It focuses on **demography analysis and sales trends**, showing who buys the cars and when. It has three sheets:
 
| Sheet | Purpose |
|-------|---------|
| `Data` | The cleaned car sales dataset |
| `Analysis` | Pivot tables and calculations that feed the charts |
| `Dashboard` | The final view with KPI cards, charts, and slicers |
 
## Key Numbers (KPI Cards)
 
| KPI | Value |
|-----|-------|
| Total Sales | 23,906 |
| Total Revenue | ₹ 67,15,25,465 |
| Average Order Value | ₹ 28,090 |
| Growth Rate | 24% |
 
## Sidebar: Sales by Company
 
| Company | Cars Sold |
|---------|-----------|
| Chevrolet | 1,431 |
| Dodge | 1,327 |
| Ford | 1,247 |
| Volkswagen | 1,044 |
| Mercedes-B | 1,008 |
 
The sidebar also has **Help Center**, **Settings**, and **Logout** icons for a professional app-style look.
 
## Charts
 
| Visual | Chart Type | What It Shows |
|--------|-----------|---------------|
| Top 5 Customers by Quantity | Column chart | Thomas (92), Emma (90), Lucas (88), Nathan (80), Louis (76) |
| Gender by Percentage Quantity | Donut chart | Female 21.37% and Male 78.63% of purchases |
| Salary Group by Quantity | Bar chart | Cars sold per income range ($900k+ is highest at 10,654) |
| Weekly Sales Trend | Line chart | Sales for each day of the week (Sunday to Saturday) |
| Monthly Sales Trend | Line chart | Sales for each month (January to December) |
 
## Excel Features
 
- **Slicers:** Female and Male buttons filter all charts at once
- **Pivot tables and pivot charts:** summarise thousands of rows in seconds
- **KPI cards:** key numbers shown with icons at the top
- **Smooth line charts:** make trends easy to read
- **Clean layout:** grid lines hidden, cards with shadows, one blue colour theme
## How to Open the Excel File
 
1. Download this repository (see Part 1, step 2).
2. Open the `CarSalesDashboard.xlsx` file in **Microsoft Excel** (2016 or later; slicers work best in Excel 2013 and above).
3. Click the **Dashboard** sheet.
4. Click **Female** or **Male** to filter the charts. Click the same button again (or the clear-filter icon) to reset.
5. If pivot tables look outdated, go to **Data > Refresh All**.
---
 
# Power BI vs Excel
 
| Point | Power BI | Excel |
|-------|----------|-------|
| Ease of learning | Needs a little practice | Easier for beginners |
| Handling big data | Very good | Slower with very large files |
| Formulas | DAX | Excel formulas and pivot tables |
| Interactivity | Filters, drill-through, map | Slicers |
| Sharing | Publish online | Share the file |
 
Both dashboards show the same story. For example, the **$900K+ income group** is the top buyer in both, with about 10.7K cars.
 
## Tools Used
 
| Tool | Purpose |
|------|---------|
| Power BI Desktop | Building the interactive report |
| DAX | Creating measures like revenue and YoY growth |
| Power Query | Cleaning the raw data |
| Microsoft Excel | Pivot tables, slicers, and the Excel dashboard |
| CSV / Excel file | Source data |
 
## What I Learned
 
- Cleaning and preparing data with Power Query and Excel
- Creating a Calendar table for date-based analysis
- Writing basic DAX measures (SUM, COUNTROWS, DIVIDE, CALCULATE)
- Building pivot tables, pivot charts, and slicers in Excel
- Choosing the right chart for the right question
- Designing clean, professional-looking dashboards in two different tools
## Insights from the Data
 
- **Chevrolet** sells the most cars, followed by Dodge and Ford.
- **Austin** is the top dealer region for sales.
- The **$900K+ income group** buys far more cars than any other group.
- About **79% of purchases are by males** and about **21% by females**.
- **BMW** has a higher YoY growth (28.99%) than the overall business (24.57%), though its average order value is a little lower.
- Sales dip in the middle of the week (Thursday is the lowest) and are lowest early in the year (January and February), then rise towards the end of the year.
## Future Improvements
 
- Add a year and month slicer to both dashboards
- Add a tooltip page in Power BI with extra details
- Publish the Power BI report to Power BI Service and share the link
- Add a profit analysis page
- Add mobile layout view
- Add macros or buttons in Excel for easier navigation
## Author
 
**Abinanthan**
GitHub: [abinanthan1](https://github.com/abinanthan1)
 
## License
 
This project is free to use for learning purposes.
 
