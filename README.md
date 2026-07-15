# CRM Sales Pipeline Analysis


## 1. Project Overview and Objective

This project analyses a B2B CRM sales pipeline dataset covering four connected tables: sales transactions, client accounts, product catalog, and sales team structure. The work spans two stages: data cleaning and modeling in Excel and Power Query, followed by an interactive analytical dashboard built in Power BI.

The objective was to take raw, inconsistent CRM data and turn it into a reliable, well-modeled dataset. This dataset was then used to answer real business questions regarding which regions and products drive revenue, how effective the sales team is at converting deals, and whether deal size relates to how long a deal takes to close.

---

## 2. Problem Statement

* Analyse sales performance across regions and products to identify top-performing areas and revenue drivers.


* Evaluate the sales funnel and conversion effectiveness (win rate) of the sales team.


* Identify and resolve data quality issues in the raw CRM export in a structured, repeatable way.


* Test whether deal size is related to how long a deal takes to close.


* Restructure the flat CRM export into a proper fact-and-dimension model for scalable reporting.



---

## 3. Tools & Technologies

* **Excel & Power Query:** Used for data cleaning, transformation, calculated fields, pivot tables, and descriptive statistics.


* **Power BI:** Used for data modeling, relationships, DAX measures, and an interactive dashboard with slicers, drill-down, and bookmarks.



---

## 4. Data Pre-Processing

All four source tables (Sales Pipeline, accounts, Product, Sales Teams) were loaded into Power Query and cleaned individually.

### Cleaning Tasks Performed

* Removed duplicates and verified zero duplicate records across all four tables.


* Standardized formats by correcting spelling errors and product names so table joins work correctly.


* Handled missing values with reasoning, such as leaving blank Close Dates and Close Values as-is for open deals, and flagging blank Company Names as "Unknown Account".


* Created calculated fields, including Is_Closed to flag Won/Lost versus still-open deals, and Sales_Cycle_Days to measure days from engagement to close.



### Descriptive Statistics and Correlation Analysis

* Descriptive statistics were calculated for Deal Close Value and Sales Cycle Days.


* A correlation test checked whether longer sales cycles are associated with higher-value deals.


* The correlation coefficient came out to 0.05, meaning deal size and deal speed are independent in this dataset.



---

## 5. Data Modeling

The four cleaned tables were imported into Power BI and connected into a star schema.

* **Fact Table:** Sales Pipeline.


* **Dimension Tables:** Product, Sales Teams, and Client Details.


* **Date Table:** A dedicated Date table was created using `CALENDAR(DATE(2016,1,1), DATE(2017,12,31))` to support time-based calculations and account for gaps in raw deal dates.



---

## 6. DAX Measures

Five DAX measures were created to power the dashboard visuals:

* **Total Sales:** Sum of all recorded deal revenue.


* **Total Deals:** Count of all deals in the pipeline.


* **Win Rate %:** Share of decided deals (Won+Lost) that were Won.


* **Cumulative Sales:** Running total of revenue over time.


* **Sales Growth %:** Month-over-month percentage change in revenue.



---

## 7. Key Insights & Conclusions

### Descriptive Insights

* Total revenue across the pipeline is $10,005,534 from 8,800 recorded deals.


* The funnel breaks down as 48.16% Won, 28.1% Lost, 18.06% Engaging, and 5.68% Prospecting.


* Among decided deals, the win rate is 63.15%.


* The West region leads revenue with about $3.57M, followed by Central with about $3.35M and East with about $3.09M.


* GTX Pro is the top revenue-generating product, while MG Special contributes the least.



### Diagnostic Insights

* The near-zero correlation (0.05) between cycle length and deal value suggests outcomes are driven by product and client fit rather than time spent on a deal.


* Month-over-month growth is highly volatile, swinging between roughly +50% and -50%, indicating revenue is driven by clusters of large deals rather than steady growth.



### Prescriptive Recommendations

* Do not deprioritize slow-moving deals assuming they are low-value, as deal size and speed are unrelated.


* Investigate the characteristics of the 28.1% Lost deals to find a specific, fixable bottleneck.


* Study what the top-performing West region and top sales agents are doing differently, and replicate it across other regions.


* Reassess the active selling of MG Special, given its minimal revenue contribution.
