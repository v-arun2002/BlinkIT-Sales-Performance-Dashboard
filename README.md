# BlinkIT Sales Analysis Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-Data%20Analysis%20Expressions-blue?style=for-the-badge)

## Project Overview

A comprehensive, multi-page Power BI dashboard analyzing sales performance for BlinkIT, India's last-minute grocery delivery service. The project demonstrates end-to-end BI development including data modeling, DAX measure authoring, row-level security, and interactive report design.

**Total Sales:** $1.20M | **Avg Sales:** $141 | **Total Items:** 8,523 | **Avg Rating:** 3.9

---

## Data Model — Star Schema

The original flat dataset was restructured into a proper star schema to enable scalable reporting and enforce data modeling best practices.

```
Dim_Item ——— Fact_Sales ——— Dim_Outlet
```

### Tables

| Table | Type | Key Columns |
|---|---|---|
| `Fact_Sales` | Fact | Item_Identifier, Outlet_Identifier, Sales, Rating, Item_Visibility |
| `Dim_Outlet` | Dimension | Outlet_Identifier, Outlet_Type, Outlet_Size, Outlet_Location_Type, Outlet_Establishment_Year |
| `Dim_Item` | Dimension | Item_Identifier, Item_Type, Item_Fat_Content |
| `Dim_Date` | Date Table | Date, Year, Month, Quarter (used for time intelligence measures) |

### Relationships
- `Dim_Outlet[Outlet_Identifier]` → `Fact_Sales[Outlet_Identifier]` (1 to many)
- `Dim_Item[Item_Identifier]` → `Fact_Sales[Item_Identifier]` (1 to many)

> Note: `Dim_Date` is available in the model for time intelligence DAX measures but does not have an active relationship with `Fact_Sales`.

---

## DAX Measures

All measures are stored in a dedicated `_Measures` table following best practices.

### Core Measures
```dax
Total Sales = SUM(Fact_Sales[Sales])

Avg Sales = AVERAGE(Fact_Sales[Sales])

Avg Rating = AVERAGE(Fact_Sales[Rating])

No Of Items = COUNTROWS(Fact_Sales)
```

### Time Intelligence
```dax
Sales LY = 
CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Dim_Date[Date]))

YoY Growth = 
DIVIDE([Total Sales] - [Sales LY], [Sales LY], 0)

Cumulative Sales = 
CALCULATE([Total Sales], DATESYTD(Dim_Date[Date]))
```

### Advanced
```dax
Item Sales Rank = 
RANKX(ALL(Dim_Item[Item_Type]), [Total Sales], , DESC)

Sales vs Target = 
IF(
    [Total Sales] >= 'Sales Target'[Sales Target Value],
    "Above Target",
    "Below Target"
)

Outlet_Establishment_Year = 
LOOKUPVALUE(
    'BlinkIT Grocery Data'[Outlet Establishment Year],
    'BlinkIT Grocery Data'[Outlet Identifier],
    Dim_Outlet[Outlet Identifier]
)
```

---

## Row Level Security (RLS)

Three security roles are configured to restrict data access by outlet location tier. Each role filters the `Dim_Outlet` table and cascades to `Fact_Sales` through the active relationship.

| Role | Filter |
|---|---|
| Tier 1 | `[Outlet_Location_Type] = "Tier 1"` |
| Tier 2 | `[Outlet_Location_Type] = "Tier 2"` |
| Tier 3 | `[Outlet_Location_Type] = "Tier 3"` |

---

## Report Pages

### Page 1 — Main Dashboard
The primary analytics view with interactive filter panel for Outlet Location Type, Outlet Size, and Item Type. Includes KPI cards, sales by fat content, sales by item type, outlet establishment trend, outlet location breakdown, and outlet type performance table.

### Page 2 — Outlet Detail (Drill-Through)
A drill-through page activated by right-clicking any outlet type on Page 1. Displays outlet-specific KPIs including Total Sales, Avg Sales, No Of Items, Avg Rating, sales by item type bar chart, and fat content donut chart. Features an automatic back navigation button.

### Page 3 — Sales Target Analysis (What-If)
An interactive scenario analysis page powered by a What-If Parameter slider ranging from $0 to $1,000,000. Users can dynamically adjust the sales target and the dashboard updates in real time to flag each outlet as "Above Target" or "Below Target."

### Page 4 — Executive Summary
A single-page executive view designed for non-technical stakeholders. Displays only the four most critical KPIs at a glance with a key business insight: *Supermarket Type1 drives 65% of total revenue across Tier 3 locations.*

---

## Key Insights

- **Tier 3 locations** generate the highest revenue at $472K, outperforming Tier 1 ($336K) and Tier 2 ($393K)
- **Supermarket Type1** dominates with $787K in sales — 65.5% of total revenue
- **Fruits & Vegetables** and **Snack Foods** are the top-selling item categories
- **Average customer rating** is consistently 3.9 across all outlet types
- **2018** was the peak year for outlet establishment with $205K in sales

---

## Technical Skills Demonstrated

| Skill | Details |
|---|---|
| Data Modeling | Star schema design, fact and dimension table separation |
| DAX | Time intelligence, RANKX, CALCULATE, DIVIDE, LOOKUPVALUE, What-If |
| Row Level Security | Role-based data filtering by outlet tier |
| Report Design | Drill-through, bookmarks, tooltips, interactive slicers |
| Power Query | Data transformation and table merging |
| Dashboard Design | Multi-page layout, executive summary, consistent theming |

---

## Project Structure

```
blinkit-sales-dashboard/
│
├── README.md
├── dashboard/
│   └── BlinkIT_Dashboard.pbix
├── data/
│   └── BlinkIT_Grocery_Data.csv
└── assets/
    ├── page1_main_dashboard.png
    ├── page2_outlet_detail.png
    ├── page3_sales_target.png
    └── page4_executive_summary.png
```

---

## Setup Instructions

1. Clone or download this repository
2. Open **Power BI Desktop**
3. Open `BlinkIT_Dashboard.pbix`
4. Refresh data connections if prompted
5. To test RLS: **Modeling tab → View as → Select a role**

---

## About

**Tool:** Power BI Desktop  
**Data Source:** BlinkIT Grocery Sales Dataset  
**Rows:** 8,523 transactions  
**Domain:** Retail & Grocery Analytics
