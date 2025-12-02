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

milestone-2: 
Feature Engineering Categories:
2.1 Time-Based Features:

These features capture seasonal patterns, weekday trends, and holiday/weekend effects on sales.
Features Created
Day, Month, Year – breaks down temporal sales patterns
Day of Week (0–6) – useful for weekly demand cycles
Weekend Flag – sales often differ on weekends
Season (Winter, Spring, Summer, Autumn) – seasonality impacts product demand

Why These Matter
Time-driven purchasing behavior significantly affects pricing decisions. These features help forecast demand cycles and optimize prices accordingly.

2.2 Price-Based Features:
These features capture historical pricing patterns and discount behavior.
Features Created
Price Lag (1, 7 days) – previous prices affect customer expectations
Price Change % – signals how customers react to price adjustments
Discount Percentage – measures discounting relative to competitor price

Why These Matter
Dynamic pricing heavily depends on understanding how price movements influence demand.

2.3 Demand Features:

Demand trends help forecast future sales volume.
Features Created
Sales Lag (1, 7, 30 days) – past sales data to capture memory effect
Rolling 7-Day Mean – short-term trend
Rolling 7-Day Standard Deviation – demand volatility

Why These Matter
Predicting demand is core to setting optimal prices. These features enhance time-series forecasting.

2.4 Price Elasticity Features:

Elasticity indicates how sensitive customers are to price changes.
Features Created
Demand Change %
Elasticity = % demand change / % price change
Elasticity Buckets (Highly Elastic, Elastic, Inelastic)

Why These Matter
Products with high elasticity require competitive pricing; low elasticity products can sustain higher margins.

2.5 Inventory Features
Pricing should consider stock availability to avoid stockouts or overstock.
Features Created
Inventory Ratio = Units Sold / Stock Level
Days to Stockout – predicts how quickly stock will run out
Low Stock Flag – early warning for price adjustments

Why These Matter
Inventory-aware pricing helps maximize revenue while maintaining stock balance.

2.6 Competitor Features
Competitor behavior is key for dynamic pricing decisions.

Features Created:
Price Differential = Price – Competitor Price
Competitor Cheaper Flag
competitor Index = Price / Competitor Price

Why These Matter
Allows the model to react to competitor pricing and maintain competitiveness.

2.7 Profit-Based Features:

These features directly capture profitability metrics.

Features Created

Profit per Unit = Price – Cost Price

Profit Margin % = Profit per Unit / Price

Why These Matter

Dynamic pricing must optimize not just revenue, but profit margins.

2.8 Interaction Features:

Interactions help capture complex relationships between variables.

Features Created

Weekend × Price – captures special weekend pricing effects

Season × Discount – adjusts pricing for seasonal promotions

Inventory × Price – price sensitivity based on stock levels

Why These Matter

Interactions reveal patterns that simple features cannot capture alone.

2.9 Categorical Encoding:

Categorical variables must be converted into numeric formats for ML models.

Features Created

Category Encoding

Competitor Name Encoding

Product ID Encoding

Season One-Hot Encoding

Why These Matter

Encodes product identity, category-specific behavior, and competitor attributes for model training.
