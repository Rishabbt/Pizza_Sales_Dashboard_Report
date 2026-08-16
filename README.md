# Pizza_Sales_Dashboard_Report
Pizza Sales Report — Power BI Dashboard 📝 Description

This Power BI report analyzes a full year of pizza sales transactions — orders, revenue, pizza categories, sizes, and timing — to help a pizza business understand what's selling, when it's selling, and how individual menu items are performing. It is built as a two-page interactive dashboard: a HOME overview page and a Best/Worst Sellers performance page, both connected to a single sales fact table.

❓ The Business Problem

A pizza business generates large volumes of raw transactional data (every order, every pizza, every timestamp) but that data on its own doesn't answer the questions that actually run the business:

Which days and months drive the most orders, and are sales trending up or down? Which pizza categories and sizes make up the bulk of revenue? Which specific pizzas are top performers — and which ones are underperforming or possibly worth dropping from the menu? Is the business getting enough value (revenue) per order and per pizza sold?

Without a consolidated view, this analysis would require manually querying the database and building ad-hoc spreadsheets every time someone asks — slow, inconsistent, and hard to monitor over time.

🎯 Goal of the Dashboard

The dashboard is designed to give managers and stakeholders a single, self-service, always-current view of sales performance, so they can:

Monitor overall sales health at a glance (revenue, order count, pizzas sold) Spot demand patterns by day and month for staffing, inventory, and promotions planning Understand the sales mix across pizza category and size Identify best- and worst-selling pizzas to guide menu, pricing, and marketing decisions Filter and drill into any of the above without needing to write a query

📊 Key Visuals --- HOME page --- Visual Chart Type Why This Chart

KPI Cards (Total Revenue, Total Orders, Total Pizzas Sold, Avg Order Value, Avg Pizza per Order) Card Cards surface the handful of headline numbers that matter most, at a glance, with no interpretation needed — the right choice for metrics people will check first, every time.
Daily Sales for Total Orders Clustered Column Chart Column charts are the standard for comparing a metric across discrete categories (days of the week). Bar height makes it immediately easy to spot which days are busiest.
Monthly Trend for Total Orders Stacked Area Chart Area charts emphasize magnitude and trend over a continuous timeline, making it easy to see whether order volume is growing, shrinking, or seasonal across the year.
Percentage of Sales by Pizza Category Donut Chart Donut charts suit part-to-whole comparisons with a small number of categories — here, showing how revenue splits across Classic, Supreme, Veggie, and Chicken categories.
Percentage of Sales by Pizza Size Donut Chart Same reasoning as above, applied to a different dimension (size: Regular, Medium, Large, X-Large), letting the two donuts be compared side by side.
Total Pizzas Sold by Pizza Category Funnel Chart A funnel naturally visualizes a descending ranked sequence — it draws the eye straight to which category leads and how sharply volume drops off toward the smallest category. Slicers (2) Slicer Slicers let users filter every visual on the page interactively (e.g., by date, category, or size) without editing the report — essential for self-service exploration.
--- Best/Worst Sellers page ---

Visual Chart Type Why This Chart

KPI Card Card Keeps a key headline metric visible while the user explores rankings below.
Top 5 Pizzas by Revenue Clustered Bar Chart Horizontal bars are the standard choice for ranked comparisons, especially when category labels (pizza names) are long — they stay readable without truncation or rotation.
Bottom 5 Pizzas by Revenue Clustered Bar Chart Same rationale, mirrored to immediately surface underperformers next to top performers for contrast.
Top 5 Pizzas by Quantity Clustered Bar Chart Ranks by units sold rather than revenue, surfacing popular but possibly lower-priced items — a different lens on "performance."
Bottom 5 Pizzas by Quantity Clustered Bar Chart Flags pizzas with low sell-through volume, a candidate list for menu review.
Top 5 Pizzas by Total Orders (×2 visuals) Clustered Bar Chart Ranks by number of distinct orders containing the pizza, highlighting how often an item gets ordered regardless of quantity or price. Slicers (2) Slicer Lets users narrow the rankings by date, category, or size to answer more specific questions (e.g., "best sellers in Q2" or "worst sellers among Large pizzas").
💡 Business Impact & Insights

This dashboard is built to support decisions such as:

Staffing & inventory planning — daily and monthly order trends indicate when to schedule more staff or stock more ingredients ahead of peak days/months. Menu engineering — the Best/Worst Sellers page identifies pizzas that consistently underperform on revenue, quantity, or order count, flagging candidates for reformulation, repricing, promotion, or removal — and identifies top performers worth protecting or featuring. Category/size strategy — the sales-mix donuts show whether revenue is concentrated in a few categories or sizes, which can inform pricing strategy or targeted upsell offers (e.g., promoting upgrades to Large/X-Large if Regular dominates). Order economics — Avg Order Value and Avg Pizza per Order indicate how much each transaction is worth and whether customers are buying multiple pizzas per order, both levers for combo deals or upsell tactics.

⚠️ Data quality note: The Avg Order Value measure is currently defined as Total Orders ÷ Total Revenue, which is inverted — it should be Total Revenue ÷ Total Orders to correctly represent average revenue per order. This should be corrected before using that KPI to make decisions.

ℹ️ Additional Important Info File type: Pizza_Sales_Report.pbit is a Power BI template — it contains the full data model, transformations, measures, and report design, but no embedded data. Opening it will prompt for a data source connection. Data source: SQL Server (localhost\SQLEXPRESS), database PizzaDB, table dbo.pizza_sales_2025. To use your own data, point the connection at a database with a matching schema, or edit the query in Power Query Editor. Data prep already applied: pizza size codes are relabeled for readability (L → Large, M → Medium, S → Regular, XLarge → X-Large), and helper columns (Day Name/Number, Month Name/Number, Order Day, Order Month) are derived from order_date to support the trend charts and correct sort order. Leftover artifact: there's an empty placeholder measure named Measure in the data model with no formula — safe to delete. To publish: open the .pbit in Power BI Desktop, connect it to your data, verify the Avg Order Value fix, then save as .pbix to preserve the data connection and set up a refresh schedule.
