# Retail Report — Sales & Profit Analysis (Excel)

An Excel business-intelligence project analyzing **9,994 order lines (5,009 orders)** from a U.S. e-commerce retailer, 2020–2023. Built during the **Per Scholas AI-Native Business Intelligence** program.

**Business question:** Where is the company making money, and where is it losing it?

📊 **File:** [`Retail_Report.xlsx`](Retail_Report.xlsx) (download and open in Excel; the Dashboard sheet is the summary)

![Dashboard](images/dashboard.png)

---

## Tools & Techniques

- **Power Query:** imported 4 CSV sources (Orders, Customers, Products, Location), set data types, and merged them into one model table (`Full_Sales_Table`) with left-outer joins on Customer ID, Postal Code, and Product ID
- **PivotTables & PivotCharts:** 5 pivots that slice sales and profit by category, region, city, and product
- **Slicers:** interactive filtering by Region and City
- **Structured references:** KPI formulas like `SUM(Full_Sales_Table[Sales])`
- **Dashboard:** KPI cards linked to live formulas, plus 4 charts

## Data Model

| Table | Rows | Key |
|---|---|---|
| Orders | 9,994 | Row ID |
| Customers | 793 | Customer ID |
| Products | 1,862 | Product ID |
| Location | 630 | Postal Code |
| **Full_Sales_Table** (merged) | 9,994 | — |

## Data Cleaning

- Converted `Order Date` and `Ship Date` from text (DD/MM/YYYY) to true Excel dates, in the Power Query step so the fix holds on refresh
- Changed the order KPI from a row count (9,994 line items) to a **distinct count of Order IDs (5,009 orders)**
- Removed the Country level from the city pivot so cities compare directly

## Key Findings

| Category | Sales | Profit | Margin |
|---|---|---|---|
| Technology | $836K | $145K | **17.4%** |
| Office Supplies | $719K | $122K | **17.0%** |
| Furniture | $742K | $18K | **2.5%** |
| **Total** | **$2.30M** | **$286K** | **12.5%** |

1. **Furniture is the problem category.** It sells nearly as much as the other two categories but earns roughly one-seventh of the profit of either one.
2. **Central-region Furniture lost money (–$2,871).** It's the only category–region combination that did.
3. **The West leads profit at $108K**, about 2.7× the Central region ($40K).
4. **One product carries a lot of weight.** The Canon imageCLASS 2200 copier made $25.2K profit, more than all Furniture combined.

### Follow-up analysis (from the same data)
- **Tables (–$17.7K) and Bookcases (–$3.5K)** are the sub-categories behind Furniture's weak margin.
- **Heavy discounting loses money:** order lines discounted more than 20% lost about $135K in total, while undiscounted lines earned about $321K.

## Recommendations

- Review discount policy, especially caps above 20% on Furniture (Tables, Bookcases)
- Investigate pricing and shipping costs for Furniture in the Central region
- Protect and expand high-margin Technology lines (copiers, printers)

## Repository Structure

```
Retail-Report/
├── README.md
├── Retail_Report.xlsx
└── images/
    └── dashboard.png
```

---

*Author: Akai Outlaw · Software Engineering & Data Analytics student*
