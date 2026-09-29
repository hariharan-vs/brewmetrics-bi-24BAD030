# BrewMetrics Coffee Co. — Business Intelligence Solution

## Project Overview

BrewMetrics Coffee Co. is a coffee business operating Flagship, Kiosk, and Drive-Thru stores across multiple cities. This Business Intelligence project analyzes sales transactions to identify sales trends, product patterns, and differences in city performance.

The solution was developed using Power BI Desktop, Power BI Project format (PBIP), GitHub, and GitHub Copilot.

## Project Objectives

- Build a version-controlled Power BI solution.
- Transform the flat sales dataset into a star schema.
- Create DAX measures for sales analysis.
- Analyze month-over-month sales growth.
- Calculate cumulative sales.
- Rank cities based on sales performance.
- Calculate average transaction value.
- Identify the seasonal sales pattern of Cold Brew.
- Compare sales performance across cities.

## Data Model

The Power BI solution uses a star schema consisting of one fact table and four dimension tables.

### Fact Table

**Fact_Sales**

Contains the transactional sales information:

- sale_id
- date
- city
- store_format
- category
- item
- quantity
- unit_price
- sales_amount

### Dimension Tables

**Dim_Date**
- date
- Year
- Month
- Month Name
- Day

**Dim_City**
- city

**Dim_Product**
- category
- item

**Dim_Store_Format**
- store_format

### Relationships

The model uses one-to-many relationships from the dimension tables to `Fact_Sales`.

```text
Dim_Date ─────────────┐
Dim_City ─────────────┤
Dim_Product ──────────┼──→ Fact_Sales
Dim_Store_Format ─────┘


DAX Measures

Four main DAX measures were developed with assistance from GitHub Copilot.

1. MoM Sales Growth %

Calculates month-over-month sales growth.

2. Running Total Sales

Calculates cumulative sales from the earliest available date through the current date.

3. City Sales Rank

Ranks cities according to total sales, with the highest-sales city receiving rank 1.

4. Average Transaction Value

Calculates total sales divided by total quantity.

Dashboard

The final Power BI dashboard contains:

Total Sales KPI
MoM Sales Growth KPI
Average Transaction Value KPI
Monthly Sales Trend
Cold Brew Seasonal Sales Pattern
City Sales Performance
City Sales Ranking
City filter/slicer
Date drill-down hierarchy
Key Insights

The completed dashboard provides the following observations from the analyzed dataset:

City performance: Bengaluru records the highest total sales among the four cities in the dashboard, followed by Chennai, Hyderabad, and Coimbatore.
Cold Brew pattern: The Cold Brew analysis shows its sales pattern across the available months, allowing the seasonal variation to be identified directly from the dashboard.
Overall sales: The dashboard reports approximately ₹3.97 million in total sales across the available data.
Version Control

Git and GitHub were used to maintain a version-controlled Power BI project.

Major commits include:

Initial project setup
Add star schema: fact and dimension tables
Add month-over-month sales growth measure
Add running total sales measure
Add city sales ranking measure
Add average transaction value measure
Complete BrewMetrics sales dashboard
Tools Used
Power BI Desktop
Power BI Project (.pbip)
Power Query
DAX
Git
GitHub
GitHub Copilot