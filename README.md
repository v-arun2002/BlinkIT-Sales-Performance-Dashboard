# BlinkIt Sales Analysis Dashboard

## Project Overview
This project presents a comprehensive Power BI dashboard analyzing sales data for BlinkIt, India's last-minute delivery service. The dashboard provides insights into sales performance, product distribution, outlet characteristics, and customer ratings across different regions and outlet types.

## Key Metrics

### Overall Performance
- **Total Sales**: $1.20M
- **Average Sales per Transaction**: $141
- **Total Items**: 8,523
- **Average Customer Rating**: 3.9/5.0

## Dashboard Features

### 1. Sales Analysis by Fat Content
- **Regular Fat Products**: $472.13K
- **Low Fat Products**: $336.40K
- Average sales remain consistent across both categories (~$141)

### 2. Outlet Location Performance
The analysis covers three tiers of outlet locations:
- **Tier 3**: $472.13K (highest performing)
- **Tier 2**: $393.15K
- **Tier 1**: $336.40K

### 3. Item Category Performance
Top performing categories by average sales:
1. Household items: $149.42
2. Dairy products: $148.50
3. Starchy Foods: $147.84
4. Snack Foods: $146.19
5. Fruits and Vegetables: $144.58

### 4. Outlet Type Analysis
Four outlet types analyzed:
- **Supermarket Type1**: $787.55K (65.5% of total sales, 5,577 items)
- **Grocery Store**: $151.94K (1,083 items)
- **Supermarket Type2**: $131.48K (928 items)
- **Supermarket Type3**: $130.71K (935 items)

### 5. Temporal Analysis
Outlet establishment timeline shows sales trends from 2012-2022:
- Peak year: 2018 with $205K
- Recent years (2020-2022) maintaining steady performance around $130K-$133K

## Interactive Filters

The dashboard includes three dynamic filter panels:
1. **Outlet Location Type**: Filter by Tier 1, 2, or 3
2. **Outlet Size**: Filter by outlet size categories
3. **Item Type**: Filter by specific product categories

## Key Insights

1. **Geographic Distribution**: Tier 3 locations generate the highest revenue, suggesting strong performance in smaller cities/towns
2. **Product Mix**: Household and dairy items command the highest average sales prices
3. **Outlet Performance**: Supermarket Type1 dominates with 65.5% market share
4. **Consistent Quality**: Average rating of 3.9 maintained across all outlet types
5. **Item Visibility**: Grocery stores have higher item visibility (0.10) compared to supermarkets (0.06)

## Technical Details

### Tools Used
- **Power BI Desktop**: Primary visualization and analysis tool
- **Data Processing**: ETL processes for data cleaning and transformation

### Visualizations Included
- KPI Cards (Total Sales, Avg Sales, Items, Rating)
- Donut Charts (Fat Content distribution, Outlet Location)
- Horizontal Bar Charts (Item Type performance, Fat by Outlet)
- Area Chart (Outlet Establishment timeline)
- Data Table (Outlet Type detailed metrics)
- Filter Slicers (Interactive filtering capabilities)

## Data Quality Metrics
- **Item Visibility Range**: 0.06 - 0.10
- **Rating Consistency**: 3.91 - 3.93 across outlet types
- **Complete Dataset**: All 8,523 items accounted for

## Business Recommendations

1. **Expand Tier 3 Presence**: Focus on expanding in Tier 3 locations given their superior performance
2. **Category Optimization**: Increase inventory of high-margin household and dairy products
3. **Supermarket Type1 Strategy**: Leverage the success model of Type1 supermarkets
4. **Grocery Store Enhancement**: Improve grocery store operations despite lower volumes but higher visibility

## How to Use This Dashboard

1. **Overview**: Start with the KPI cards at the top for quick insights
2. **Deep Dive**: Use the filter panel on the left to drill down into specific segments
3. **Comparisons**: Utilize the donut and bar charts to compare performance across categories
4. **Trends**: Review the timeline chart for historical performance patterns
5. **Details**: Refer to the outlet type table for comprehensive metrics


## Installation & Setup

### Prerequisites
- Power BI Desktop (latest version)
- Windows 10 or later

### Steps
1. Clone or download this repository
2. Open Power BI Desktop
3. Navigate to File > Open
4. Select the `BlinkIt_Dashboard.pbix` file
5. Refresh data connections if prompted

## Data Sources
The dashboard connects to the following data sources:
- Sales transaction data
- Product catalog
- Outlet information
- Customer ratings

## Future Enhancements

- [ ] Real-time data integration
- [ ] Predictive analytics for demand forecasting
- [ ] Customer segmentation analysis
- [ ] Seasonal trend analysis
- [ ] Profitability analysis by category
- [ ] Mobile-responsive dashboard version
- [ ] Automated email reports
