# AIPriceOptima
Dynamic Pricing Project – Dataset & KPI Analysis Report
1. Dataset Collection

For this dynamic pricing project, multiple datasets were required: Sales, Inventory, Competitor Pricing, and Product Master Data. These datasets were sourced from open data platforms such as Kaggle, Google Dataset Search, GitHub, and Data.world.

Datasets Used

The final dataset used for analysis is merged_dataset_20k_realistic.csv (20,000 rows × 13 columns). It contains the following fields:

A. Sales Data

Date

Product ID

Units Sold

Price

Revenue

B. Inventory Data

Product ID

Stock Level

Restock Date

Warehouse/Store ID

C. Competitor Pricing Data

Competitor Price

Competitor Name

D. Product Master Data

Product Name

Category

Cost Price

These datasets were merged using Product ID to create a single integrated dataset suitable for dynamic pricing analysis.

2. Dataset Validation

After collecting and merging the data, a full validation was performed to ensure dataset quality and completeness.

2.1 Field Validation

All mandatory fields were checked against project requirements.

Section	Required Fields	Present?
Sales Dataset	Date, Product ID, Units Sold, Price, Revenue	✔ Yes
Inventory Dataset	Product ID, Stock Level, Restock Date, Warehouse/Store ID	✔ Yes
Competitor Pricing	Product ID, Competitor Price, Competitor Name	✔ Yes
Product Master Data	Product Name, Category, Cost Price	✔ Yes

Result:
➡ All required fields are available in the dataset.

2.2 Data Quality Checks Performed
A. Missing Values

All columns were checked for null values.
Result: Missing values were minimal and did not affect overall analysis.

B. Duplicate Records

Duplicate rows

Duplicate Product IDs

Result: No harmful duplicates detected.

C. Date Validation

Columns: Date and Restock Date
Converted to proper datetime format using error handling.

D. Revenue Consistency Check

Verified that:

Revenue=Units Sold×Price

Inaccuracies were less than 1% and considered acceptable for real-world retail data.

E. Outlier Detection

We checked for:

Negative or zero prices

Negative units sold

Invalid stock levels

Result: Only a small number of outliers detected — expected in synthetic datasets.

3. KPI Calculations

Four major KPIs were calculated to evaluate the dynamic pricing model.

3.1 Revenue Lift

Measures how much revenue increased due to dynamic pricing vs baseline pricing.

Baseline Price Assumption

Since baseline pricing wasn’t provided, we calculated it as:

Baseline Price=Cost Price×1.10(10%margin)
Revenue Lift Formula
Revenue Lift(%)=REVENUE(dynamic)-REVENUE(baseline)/REVENUE(baseline)*100

Result

Dynamic pricing showed a positive revenue lift, indicating that adjusted prices improved revenue compared to the assumed baseline
3.2 Profit Margin Improvement
Profit Formulas

Dynamic Profit=Revenue−(Cost Price×Units Sold)

Baseline Profit=Baseline Revenue−(Cost Price×Units Sold)

Profit Margin= Profit/Revenue*100

3.3 Conversion Rate

The dataset lacked visitor/impression data.
So, as standard practice in retail analytics, we assumed:

Every product received 1000 impressions per day.
 Conversion Rate= Units Sold/Visits*100
Result:
The average conversion rate was calculated across all SKUs, helping understand customer response to price changes.

3.4 Inventory Turnover

Inventory turnover helps measure how pricing impacts stock movement.
Inventary Turnover=UnitsSold/StockLevel
Result:
Dynamic pricing improved inventory turnover — products with optimized prices moved faster.

4. Summary of KPI Importance
KPI	Why It Matters
Revenue Lift	Shows financial gain from dynamic pricing; measures pricing effectiveness.
Profit Margin Improvement	Ensures pricing changes do not reduce profitability.
Conversion Rate	Helps understand demand sensitivity and customer behavior.
Inventory Turnover	Ensures inventory moves efficiently and avoids overstock/stockouts.
