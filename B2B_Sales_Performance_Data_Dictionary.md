# Power BI B2B Sales Performance & Profitability Analytics

## Data Dictionary

This document describes all tables, columns, data types, and analytical purposes in the uploaded B2B sales dataset.

## Workbook Overview

| Table | Rows | Purpose |
|---|---:|---|
| `DimDate` | 1,104 | Calendar and time intelligence dimension |
| `DimGeography` | 44 | Geographic hierarchy and market information |
| `DimProduct` | 28 | Product master and product hierarchy |
| `DimChannel` | 6 | Sales channel and sales motion information |
| `DimSalesperson` | 36 | Sales organization, manager, salesperson and territory information |
| `DimCustomer` | 900 | B2B customer master and segmentation information |
| `DimPromotion` | 6 | Promotion, campaign and discount information |
| `DimBusinessEvent` | 6 | Business events that may influence sales performance |
| `FactSales` | 6,000 | Transaction-level B2B sales, cost, profit, target and return data |
| `DAXMeasures` | 18 | Reference table containing predefined DAX measures |

## Detailed Data Dictionary

### DimDate

**Purpose:** Use for time intelligence, trends, YoY, MoM, quarterly analysis and seasonality.

| Column | Data Type | Description |
|---|---|---|
| `DateKey` | Integer | Unique numeric identifier for the date. |
| `Date` | Date | Actual calendar date. |
| `Year` | Integer | Calendar year. |
| `Quarter` | Text | Calendar quarter, such as Q1, Q2, Q3 or Q4. |
| `MonthNumber` | Integer | Numeric month from 1 to 12. |
| `MonthName` | Text | Full month name. |
| `MonthShort` | Text | Abbreviated month name. |
| `ISOWeek` | Integer | ISO week number. |
| `DayName` | Text | Name of the day of the week. |
| `DayIndex` | Integer | Numeric index representing the day position. |
| `IsWeekday` | Integer | Indicator showing whether the date is a weekday. |
| `SeasonGroup` | Text | Seasonal classification of the date. |

### DimGeography

**Purpose:** Use for regional, country, state/province and city analysis. Recommended hierarchy: Region → Country → StateProvince → City.

| Column | Data Type | Description |
|---|---|---|
| `GeographyKey` | Integer | Unique identifier for a geographic location. |
| `Region` | Text | Broad geographic region. |
| `Country` | Text | Country associated with the record. |
| `StateProvince` | Text | State or province. |
| `City` | Text | City. |
| `LocalCurrency` | Text | Local currency used in the geography. |
| `Latitude` | Decimal | Geographic latitude. |
| `Longitude` | Decimal | Geographic longitude. |

### DimProduct

**Purpose:** Use for product, category, subcategory, brand and lifecycle analysis. Recommended hierarchy: Category → Subcategory → Brand → ProductName.

| Column | Data Type | Description |
|---|---|---|
| `ProductKey` | Integer | Unique product identifier. |
| `Category` | Text | High-level product category. |
| `Subcategory` | Text | Product subcategory. |
| `ProductName` | Text | Product name. |
| `StandardListPrice` | Integer | Standard or list price of the product. |
| `StandardUnitCost` | Decimal | Standard cost per unit. |
| `RecurringRevenueFlag` | Text | Indicates whether the product generates recurring revenue. |
| `PortfolioTier` | Text | Strategic product portfolio classification. |
| `BusinessUnit` | Text | Business unit associated with the product. |
| `Brand` | Text | Product brand. |
| `ProductLifecycle` | Text | Product lifecycle stage. |
| `LaunchYear` | Integer | Year the product was launched. |

### DimChannel

**Purpose:** Use for channel and sales-motion comparisons. Recommended hierarchy: ChannelGroup → Channel → Motion.

| Column | Data Type | Description |
|---|---|---|
| `ChannelKey` | Integer | Unique sales channel identifier. |
| `ChannelGroup` | Text | High-level sales channel grouping. |
| `Channel` | Text | Specific sales channel. |
| `Motion` | Text | Sales motion used for the transaction. |

### DimSalesperson

**Purpose:** Use for sales-team performance and target achievement. Recommended hierarchy: SalesDirector → SalesTeam → Manager → Salesperson.

| Column | Data Type | Description |
|---|---|---|
| `SalespersonKey` | Integer | Unique salesperson identifier. |
| `Region` | Text | Broad geographic region. |
| `SalesTeam` | Text | Sales team responsible for the transaction. |
| `Manager` | Text | Salesperson's manager. |
| `Salesperson` | Text | Salesperson name. |
| `Role` | Text | Salesperson role. |
| `HireYear` | Integer | Year the salesperson joined the organization. |
| `SalesDirector` | Text | Sales director responsible for the sales organization. |
| `Territory` | Text | Assigned sales territory. |

### DimCustomer

**Purpose:** Use for B2B segmentation, industry, customer tier, lifecycle and account analysis. Recommended hierarchy: CustomerSegment → Industry → CustomerTier → CustomerName.

| Column | Data Type | Description |
|---|---|---|
| `CustomerKey` | Integer | Unique customer identifier. |
| `CustomerSegment` | Text | Customer segment, such as Enterprise, Mid-Market or SMB. |
| `Industry` | Text | Customer industry. |
| `CustomerName` | Text | Customer name. |
| `Region` | Text | Broad geographic region. |
| `Country` | Text | Country associated with the record. |
| `LifecycleStage` | Text | Customer lifecycle stage. |
| `EmployeeBandApprox` | Integer | Approximate employee-size band or employee count. |
| `EstimatedAnnualRevenue` | Integer | Estimated annual revenue of the customer. |
| `CustomerTier` | Text | Customer importance or account tier. |
| `AccountStatus` | Text | Current customer account status. |
| `AcquisitionYear` | Integer | Year the customer was acquired. |

### DimPromotion

**Purpose:** Use to evaluate promotions, campaigns, discount strategies, seasonality and margin impact.

| Column | Data Type | Description |
|---|---|---|
| `PromotionKey` | Integer | Unique promotion identifier. |
| `PromotionName` | Text | Promotion name. |
| `PromotionType` | Text | Type of promotion. |
| `DefaultDiscountPct` | Integer | Default discount percentage associated with the promotion. |
| `Campaign` | Text | Marketing campaign associated with the promotion. |
| `DiscountStrategy` | Text | Discount strategy used by the promotion. |
| `Season` | Text | Season associated with the promotion. |
| `MarketingObjective` | Text | Primary marketing objective of the campaign. |

### DimBusinessEvent

**Purpose:** Use to explain changes in sales caused by operational, market or seasonal events.

| Column | Data Type | Description |
|---|---|---|
| `BusinessEventKey` | Integer | Unique business-event identifier. |
| `BusinessEvent` | Text | Business event associated with the transaction or period. |
| `EventType` | Text | Type or category of business event. |
| `AffectedRegion` | Text | Region affected by the event. |
| `StartDate` | Date | Business event start date. |
| `EndDate` | Date | Business event end date. |
| `BusinessExplanation` | Text | Explanation of the business event. |
| `ExpectedImpact` | Text | Expected effect of the event on business performance. |

### FactSales

**Purpose:** Central transaction table. Use for revenue, orders, quantity, costs, profitability, targets, returns and currency analysis.

| Column | Data Type | Description |
|---|---|---|
| `SalesLineKey` | Integer | Unique identifier for a sales line. |
| `OrderID` | Text | Unique order identifier. |
| `OrderDateKey` | Integer | Foreign key linking the transaction to the order date. |
| `ShipDateKey` | Integer | Foreign key linking the transaction to the ship date. |
| `CustomerKey` | Integer | Unique customer identifier. |
| `ProductKey` | Integer | Unique product identifier. |
| `GeographyKey` | Integer | Unique identifier for a geographic location. |
| `SalespersonKey` | Integer | Unique salesperson identifier. |
| `ChannelKey` | Integer | Unique sales channel identifier. |
| `PromotionKey` | Integer | Unique promotion identifier. |
| `OrderStatus` | Text | Current order status. |
| `Quantity` | Integer | Number of units sold. |
| `ListUnitPrice` | Decimal | Original/list price per unit. |
| `DiscountPct` | Integer | Discount percentage applied to the transaction. |
| `NetUnitPrice` | Decimal | Unit price after discount. |
| `SalesAmount` | Decimal | Sales/revenue amount generated by the transaction. |
| `UnitCost` | Decimal | Cost associated with one unit. |
| `COGS` | Decimal | Cost of goods sold. |
| `GrossProfit` | Decimal | Gross profit after subtracting COGS from sales. |
| `GrossMarginPct` | Decimal | Gross profit as a percentage of sales. |
| `ShippingCost` | Integer | Shipping or logistics cost. |
| `ReturnQuantity` | Integer | Number of units returned. |
| `ReturnedAmount` | Decimal | Monetary value of returned sales. |
| `TargetSalesAmount` | Decimal | Sales target associated with the transaction. |
| `DataScenario` | Text | Scenario or business context associated with the transaction. |
| `InvoiceNumber` | Text | Invoice identifier. |
| `OrderPriority` | Text | Priority assigned to the order. |
| `PaymentMethod` | Text | Payment method used for the order. |
| `OrderType` | Text | Type of order. |
| `TransactionCurrency` | Text | Currency used for the transaction. |
| `ExchangeRateToUSD` | Decimal | Exchange rate used to convert transaction currency to USD. |
| `BusinessEventKey` | Integer | Unique business-event identifier. |

### DAXMeasures

**Purpose:** Reference table for predefined DAX calculations; this is not part of the analytical star schema.

| Column | Data Type | Description |
|---|---|---|
| `MeasureName` | Text | Field contained in the dataset. |
| `DAXExpression` | Text | Field contained in the dataset. |

## Recommended Power BI Relationships

The recommended model is a star schema with `FactSales` at the center.

```text
DimDate ───────────────┐
DimGeography ──────────┤
DimProduct ────────────┤
DimCustomer ───────────┤
DimChannel ────────────┤
DimSalesperson ────────┤──> FactSales
DimPromotion ──────────┤
DimBusinessEvent ──────┘
```

Recommended relationship direction: **one-to-many (1:*) from each dimension to FactSales**.

## Recommended Analytical Groups

### Sales Performance

`SalesAmount`, `Quantity`, `OrderID`, `OrderDateKey`, `TargetSalesAmount`

### Profitability

`GrossProfit`, `COGS`, `GrossMarginPct`, `ShippingCost`, `UnitCost`

### Returns

`ReturnQuantity`, `ReturnedAmount`

### Customer

`CustomerSegment`, `Industry`, `CustomerTier`, `LifecycleStage`, `AccountStatus`

### Product

`Category`, `Subcategory`, `Brand`, `ProductName`, `ProductLifecycle`, `PortfolioTier`

### Geography

`Region`, `Country`, `StateProvince`, `City`

### Sales Team

`SalesTeam`, `Manager`, `Salesperson`, `SalesDirector`, `Territory`

### Channel

`ChannelGroup`, `Channel`, `Motion`

### Promotions

`PromotionType`, `Campaign`, `DiscountStrategy`, `Season`, `MarketingObjective`

### Business Drivers

`BusinessEvent`, `EventType`, `AffectedRegion`, `BusinessExplanation`, `ExpectedImpact`

## Core DAX Measures

| Measure | DAX |
|---|---|
| **Gross Sales** | `SUM(FactSales[SalesAmount])` |
| **Returned Sales** | `SUM(FactSales[ReturnedAmount])` |
| **Net Sales** | `[Gross Sales] - [Returned Sales]` |
| **COGS** | `SUM(FactSales[COGS])` |
| **Gross Profit** | `SUM(FactSales[GrossProfit])` |
| **Gross Margin %** | `DIVIDE([Gross Profit], [Net Sales])` |
| **Gross Quantity** | `SUM(FactSales[Quantity])` |
| **Returned Quantity** | `SUM(FactSales[ReturnQuantity])` |
| **Net Units Sold** | `[Gross Quantity] - [Returned Quantity]` |
| **Order Count** | `DISTINCTCOUNT(FactSales[OrderID])` |
| **Average Order Value** | `DIVIDE([Net Sales], [Order Count])` |
| **Return Rate %** | `DIVIDE([Returned Sales], [Gross Sales])` |
| **Sales Target** | `SUM(FactSales[TargetSalesAmount])` |
| **Target Achievement %** | `DIVIDE([Net Sales], [Sales Target])` |
| **Sales vs Target** | `[Net Sales] - [Sales Target]` |
| **Sales vs Target %** | `DIVIDE([Sales vs Target], [Sales Target])` |
| **Profit per Order** | `DIVIDE([Gross Profit], [Order Count])` |
| **Revenue per Customer** | `DIVIDE([Net Sales], DISTINCTCOUNT(FactSales[CustomerKey]))` |
| **Returned Orders** | `CALCULATE(DISTINCTCOUNT(FactSales[OrderID]), FactSales[ReturnQuantity] > 0)` |
| **Return Order Rate %** | `DIVIDE([Returned Orders], [Order Count])` |
| **Discounted Sales** | `CALCULATE([Gross Sales], FactSales[DiscountPct] > 0)` |
| **Discounted Sales %** | `DIVIDE([Discounted Sales], [Gross Sales])` |
| **Discount Amount** | `SUMX(FactSales, FactSales[Quantity] * FactSales[ListUnitPrice] * FactSales[DiscountPct])` |

## Recommended 3-Page Report Structure

### Page 1 — Executive Sales Performance
- Net Sales
- Gross Profit
- Gross Margin %
- Orders
- Average Order Value
- Target Achievement %
- Sales and Target trend
- Regional performance
- Customer segment performance
- Channel performance

### Page 2 — Profitability & Customer Intelligence
- Product profitability
- Customer segment and industry performance
- Customer tier analysis
- Revenue vs Gross Margin scatter
- Product/category drill-down
- Return rate by product/customer segment

### Page 3 — Sales Team, Channel & Business Drivers
- Sales team and salesperson performance
- Sales vs target by salesperson
- Channel and sales-motion analysis
- Promotion effectiveness
- Returns analysis
- Business event impact

## Key Business Questions

1. How are net sales, orders and average order value changing over time?
2. Which products, regions and customer segments generate the strongest gross profit and margin?
3. Where is the business exceeding or falling behind sales targets?
4. Which customers, industries and product categories drive B2B sales?
5. Which channels, teams and salespeople perform best?
6. Where are returns affecting revenue and profitability?
7. Are promotions generating profitable growth or reducing margin?
8. Which business events help explain changes in sales and profitability?

---

Generated from the uploaded workbook: `Dataset_Power_BI_Sales_Dashboard_4U_August.xlsx`.