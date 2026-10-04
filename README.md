# Adidas Sales Performance Analysis

An interactive Power BI dashboard exploring Adidas sales, operating profit, product performance, and regional distribution.

## Project Overview

This project analyses the Adidas US sales dataset through regional, retailer, product, and monthly comparisons.

The dashboard presents financial and sales indicators alongside interactive region and date filters to support exploratory business analysis.

The displayed date slicer spans **January 1, 2020 to December 31, 2021**.

## Dashboard Preview

![Adidas Sales Dashboard](screenshort%201.jpeg)

## Business Objectives

- Compare sales performance across regions and states.
- Identify leading retailers and product categories.
- Examine monthly sales distribution.
- Monitor operating profit, units sold, and pricing metrics.
- Explore regional performance through interactive filters.

## Tools and Technologies

| Tool | Application |
|---|---|
| Power BI Desktop | Data modelling and dashboard development |
| Power Query | Excel import, data type conversion, and month extraction |
| DAX | Average price and margin calculations |
| Microsoft Excel | Source dataset format |

## Dataset Structure

The main table, `Data Sales Adidas`, contains the following fields:

| Field | Description |
|---|---|
| `Retailer` | Retailer name |
| `Retailer ID` | Retailer identifier |
| `Invoice Date` | Sales invoice date |
| `Region` | Geographic sales region |
| `State` | US state |
| `City` | City associated with the record |
| `Product` | Product category |
| `Price per Unit` | Recorded unit price |
| `Units Sold` | Quantity sold |
| `Total Sales` | Recorded sales amount |
| `Operating Profit` | Recorded operating profit |
| `Operating Margin` | Recorded operating margin |
| `Sales Method` | Sales channel or method |
| `month` | Three-letter month label derived from Invoice Date |

The source workbook is referenced by the template but is not included in this repository.

## Dashboard Features

- Sales, profit, units sold, average price, and average margin cards.
- Regional sales treemap.
- State-level sales map.
- Retailer and product sales rankings.
- Monthly sales chart.
- Region slicer and invoice-date range filter.

Some KPI values are truncated in the uploaded screenshot. Exact totals should be confirmed in Power BI.

## Key Findings

### 1. Regional Sales Performance

| Region | Displayed Sales |
|---|---:|
| West | $270M |
| Northeast | $186M |
| Southeast | $163M |
| South | $145M |
| Midwest | $136M |

The West region records the highest displayed sales, while the Midwest records the lowest.

Regional differences should be investigated alongside distribution coverage, retailer mix, and product demand.

### 2. Retailer Sales Performance

| Retailer | Displayed Sales |
|---|---:|
| West Gear | $243M |
| Foot Locker | $220M |
| Sports Direct | $182M |
| Kohl's | $102M |
| Amazon | $78M |
| Walmart | $75M |

West Gear leads the displayed retailer ranking, followed by Foot Locker and Sports Direct.

Sales contribution alone does not establish retailer profitability or operational efficiency.

### 3. Product Sales Performance

| Product Category | Displayed Sales |
|---|---:|
| Men's Street Footwear | $209M |
| Women's Apparel | $179M |
| Men's Athletic Footwear | $154M |
| Women's Street Footwear | $128M |
| Men's Apparel | $124M |
| Women's Athletic Footwear | $107M |

Men's Street Footwear generates the highest displayed sales, followed by Women's Apparel.

Several product labels are truncated in the screenshot and should be expanded for clearer presentation.

### 4. Monthly Sales Distribution

The displayed month totals range from approximately **$57M in March** to **$95M in July**.

However, the chart's month labels are not arranged chronologically. A numeric month sort column is needed before interpreting the visual as a time trend.

Month-name grouping also combines the same month across years in the selected period. A Year-Month axis would support a clearer analysis of changes over time.

> Findings use rounded values visible in the dashboard screenshot. The source workbook has not been independently recalculated or validated.

## DAX Measures

The following explicit measures are included in the template:

### Average Price per Unit

```dax
Avg Price Per Unite =
AVERAGEA('Data Sales Adidas'[Price per Unit])
```

### Average Operating Margin

```dax
Avg Margin =
AVERAGE('Data Sales Adidas'[Operating Margin])
```

The average margin is an arithmetic average of record-level margins. It is different from an overall margin calculated as total operating profit divided by total sales.

## Suggested Model Enhancements

The following measures are proposed improvements and are not listed as existing measures in the inspected template:

```dax
Total Sales =
SUM('Data Sales Adidas'[Total Sales])

Total Operating Profit =
SUM('Data Sales Adidas'[Operating Profit])

Total Units Sold =
SUM('Data Sales Adidas'[Units Sold])

Overall Operating Margin =
DIVIDE(
    [Total Operating Profit],
    [Total Sales]
)

Sales per Unit =
DIVIDE(
    [Total Sales],
    [Total Units Sold]
)
```

Format Overall Operating Margin as a percentage and Total Units Sold as a number.

Sales per Unit uses recorded sales and quantities. Its interpretation should be checked against the dataset's pricing and discount definitions.

### Month Sorting Column

```dax
Month Number =
MONTH('Data Sales Adidas'[Invoice Date])
```

Select the `month` column and use **Sort by column → Month Number**.

For analysis across multiple years, use a date table with a chronologically sorted Year-Month field.

## Analysis Workflow

1. Import the Excel worksheet through Power Query.
2. Promote the first row to column headers.
3. Assign appropriate data types to dates, quantities, and financial fields.
4. Derive abbreviated month labels from Invoice Date.
5. Create average price and margin measures.
6. Build regional, retailer, product, geographic, and monthly visuals.
7. Add region and date filters.

## Business Recommendations

- Investigate the drivers of stronger sales in the West region.
- Review the product and retailer mix in lower-sales regions.
- Assess inventory requirements for leading product categories.
- Compare retailer sales with operating profit before making allocation decisions.
- Correct the month ordering before assessing seasonal patterns.
- Extend the report to compare Sales Method performance.

These recommendations are proposed analytical actions. Their business impact has not been measured.

## Repository Contents

| File | Description |
|---|---|
| `adidas analysis .pbit` | Power BI report template |
| `screenshort 1.jpeg` | Sales dashboard screenshot |
| `README.md` | Project documentation |

## How to Open the Project

1. Download or clone this repository.
2. Open `adidas analysis .pbit` in Power BI Desktop.
3. Obtain a compatible `Adidas US Sales Datasets.xlsx` workbook.
4. Open Power Query and update the Source file path.
5. Confirm the `Data Sales Adidas` worksheet.
6. Apply changes and refresh the report.

> The template references an Excel file on the author's local computer. Refreshing requires access to a compatible source workbook.

## Limitations and Future Improvements

- Document the dataset source, licence, and record-level definition.
- Include the source workbook where sharing permissions permit.
- Replace the fixed file path with a configurable parameter.
- Expand KPI cards to display complete labels and values.
- Remove currency formatting from Units Sold.
- Format operating margins consistently as percentages.
- Distinguish average record-level margin from overall operating margin.
- Sort months chronologically.
- Add Year-Month trends and year-over-year comparisons.
- Validate map locations and state-level aggregation.
- Expand truncated product labels.
- Validate sales, quantities, and profit before drawing financial conclusions.
- Add sales-method comparisons and regional profit analysis.

## Author

**Junaed Bogdadi**

[GitHub Profile](https://github.com/junaed-bogdadi)
