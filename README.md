# Supply Chain Data Analysis Python Project

> A comprehensive supply chain analytics project using **Python NumPy, Pandas, Matplotlib and Seaborn** to transform raw operational data into actionable business insights.
<img width="1536" height="684" alt="Copilot_20260903_165929" src="https://github.com/user-attachments/assets/cdcd4a4c-1c2c-4c52-b3d7-8521fdaa95ae" />

## 📌 Project Overview

This project analyzes a multi-country supply chain involving suppliers, warehouses, carriers, shipping modes, products, inventory, orders and delivery performance.

The objective is to create a structured analytics workflow that helps answer practical supply chain questions around:

- Supplier quality and defect rates
- Carrier delivery performance
- Shipping-mode efficiency
- Product and category demand
- Warehouse inventory levels
- Order and sales trends
- Delivery performance
- Discounts, costs, and operational KPIs

The project follows a complete workflow from **data inspection and cleaning to feature engineering, exploratory analysis, univariate and bivariate analysis, time-series analysis, KPI calculation and business-question analysis**.

## 🎯 Business Problem

The organization manages a complex supply chain across multiple countries, suppliers, warehouses, carriers and transportation modes. Operational information is available across systems, but it is not consistently analyzed.

This makes it difficult for leadership to make data-backed decisions about:

- Supplier selection
- Carrier contracts
- Inventory planning
- Shipping-mode selection
- Product demand
- Delivery performance
<img width="1536" height="612" alt="Copilot_20260903_165836" src="https://github.com/user-attachments/assets/01bfcefd-fcbc-4f8e-b6cc-d2a4d18d6c71" />

## 💡 Solution Approach

The analysis follows these major steps:

1. Load and inspect the raw dataset
2. Identify data-quality issues
3. Clean and standardize the data
4. Handle missing values and duplicates
5. Validate numerical and date fields
6. Engineer operational and time-based features
7. Perform univariate analysis
8. Perform bivariate analysis
9. Analyze monthly sales and order trends
10. Calculate supply chain KPIs
11. Answer business-focused questions
12. Summarize the major findings

## 📊 Dataset

The raw dataset contains **105,000 rows and 32 columns**.
> The dataset used in this project is synthetically generated for project purpose and does not represent an original company dataset.
> 
Key fields include:

| Area | Example Fields |
|---|---|
| Orders | `Order_ID`, `Order_Date`, `Order_Status`, `Quantity` |
| Products | `SKU`, `Product_Name`, `Category`,`Quantity`,`Notes` |
| Suppliers | `Supplier_Name`, `Supplier_Country` |
| Warehouses | `Warehouse_Code`, `Warehouse_City`, `Warehouse_Country` |
| Transportation | `Carrier`, `Shipping_Mode` |
| Delivery | `Ship_Date`, `Delivery_Date`, `Lead_Time_Days` |
| Cost | `Unit_Cost`, `Total_Cost`, `Currency`, `Payment_Terms`, `Discount_Percent` |
| Inventory | `Warehouse_Stock_Level`, `Reorder_Point` |
| Quality | `Defective_Units` |
| Customer / Destination | `Customer_Name`, `Customer_Contact`,`Customer_Email`,`Destination_City`, `Destination_Country` |

> **Data Privacy Note:** The original dataset contains customer contact, customer email and notes fields. These fields were removed because they are not useful for analysis purposes

## 🧹 Data Cleaning & Preparation

The project performs several data-quality and preprocessing steps.

### Standardization

- Removed leading/trailing whitespace
- Standardized column names to lowercase
- Standardized text capitalization
- Standardized identifiers such as order IDs, SKUs, warehouse codes, and currency values
- Standardized date fields
- Cleaned cost fields and converted them to numeric values
- Normalized inconsistent on-time delivery flags such as `1`, `Y`, `True`, and `Yes`

### Missing Values

- Missing numeric values were handled using median imputation where appropriate
- Missing categorical values were replaced with `Unknown` where appropriate

### Duplicate Handling

- Checked duplicate rows
- Checked duplicate order IDs
- Removed duplicate order IDs while keeping the first occurrence

### Validation

The project validates:

- Negative values in operational and financial measures
- Logical date relationships such as:
  - Order Date ≤ Ship Date
  - Ship Date ≤ Delivery Date

### Removed Fields

The following fields were removed because they were not required for the analysis:

- `Notes`
- `Customer_Contact`
- `Customer_Email`

## ⚙️ Feature Engineering

Several analytical features were created from the cleaned data.

### Delivery Metrics

The following features were created:

- `delivery_time`
- `delivery_delay_days`
- `delivery_status`

Delivery status is classified as:

| Status | Condition |
|---|---|
| Early | Delivery delay < 0 |
| On Time | Delivery delay = 0 |
| Late | Delivery delay > 0 |

### Cost Metric

A `cost_per_unit` feature was calculated using total cost and quantity.

### Time Features

The project extracts:

- `order_year`
- `order_month`
- `order_month_name`
- `order_quarter`
- `order_day`

## 📈 Exploratory Data Analysis

### 1. Univariate Analysis
> Analysis of a single variable to understand its distribution, frequency and key characteristics.
<p>The project examines the distribution of key supply chain variables, including:</p>

- 💱 Currency distribution
- ⏳ Lead-time distribution
- 📦 Order quantity distribution
- 💰 Unit-cost distribution
- 📋 Order-status distribution
- 🚚 Shipping-mode distribution

### 2. Bivariate Analysis
> Analysis of two variables to identify relationships, patterns or differences between them.
<p>Relationships between key operational and financial variables were analyzed, including:</p>

- 📦 Product category vs. quantity
- 🚛 Shipping mode vs. order rate
- 💰 Quantity vs. unit cost
- 🏭 Warehouse stock level by country
- 📈 Correlation among operational and financial variables

### 3. Time-Series Analysis
> Analysis of data over time to identify trends, patterns, and changes across different time periods.
<p>Monthly trends were analyzed to identify changes in:</p>

- 💰 Sales
- 📦 Order volume

## 📊 Data Visualization
<img width="1500" height="500" alt="Fig_1_currency_distribution" src="https://github.com/user-attachments/assets/8382164a-0f61-40b3-84cf-e96d3006b5f3" />
<img width="1000" height="500" alt="Fig_2_leadtime_distribution" src="https://github.com/user-attachments/assets/817c9dd0-4aa1-4f22-8ae1-147322e5f6bd" />
<img width="1000" height="500" alt="Fig_3_quantity_distribution" src="https://github.com/user-attachments/assets/6266ea99-61fc-4e4e-b81b-6e85e735426e" />
<img width="1000" height="500" alt="Fig_4_unitcost_distribution" src="https://github.com/user-attachments/assets/3c6602f5-cd01-45b6-95f8-4fccad5d691b" />
<img width="1500" height="500" alt="Fig_5_orderstatus_distribution" src="https://github.com/user-attachments/assets/32730257-14ad-4bc2-ac9d-c3b8c8c016f4" />
<img width="1500" height="500" alt="Fig_6_shipmode_distribution" src="https://github.com/user-attachments/assets/0a02fe80-24fd-4d05-bab7-95b2d69b716c" />
<img width="1500" height="500" alt="Fig_7_cat_qty" src="https://github.com/user-attachments/assets/173ad6ad-fdea-4852-8491-028988cab50d" />
<img width="1200" height="800" alt="Fig_8_order_shipmode" src="https://github.com/user-attachments/assets/8564b501-34c7-4801-aca8-6fab67b2c731" />
<img width="640" height="480" alt="Fig_9_qty_unitcost" src="https://github.com/user-attachments/assets/091817a4-6f1f-4bea-8025-67aa3250c9b8" />
<img width="640" height="480" alt="Fig_10_stock_country" src="https://github.com/user-attachments/assets/d598675f-f2fe-415c-bded-9854efb597c1" />
<img width="1000" height="800" alt="Fig_11_heatmap" src="https://github.com/user-attachments/assets/6038ec22-715a-4376-b731-5db60abbf491" />
<img width="500" height="500" alt="Fig_12_monthlysales" src="https://github.com/user-attachments/assets/39ae17c4-3d10-40b5-bfd9-24decf682852" />
<img width="500" height="500" alt="Fig_13_monthlyorders" src="https://github.com/user-attachments/assets/8105d816-01fa-4b6b-acde-69587ecc3526" />


## 📊 Key Performance Indicators

| KPI | Result |
|---|---:|
| Total Sales | **$311,594,979,119.00** |
| Total Orders | **72,000** |
| Total Units Sold | **249,466,945** |
| Average Unit Cost | **$1,243.02** |
| Average Delivery Time | **1 day** |
| On-Time Delivery | **98.00%** |
| Average Discount | **3.25%** |
| Average Warehouse Stock | **25,017.12 units** |

## ❓ Business Questions Answered

The project directly answers the following business questions:

1. Which 10 products have the highest order quantities?
2. Which suppliers have the highest defect rates?
3. Which carrier has the highest average delivery delay?
4. Which shipping mode has the longest average lead time?
5. What is the most common order status?
6. Which five product categories have the highest average discount?
7. Which warehouse country has the highest average stock level?
8. Which years recorded the highest number of orders?
9. Which carrier has the highest on-time delivery rate?
10. Which countries receive the most late deliveries?

## 🔎 Key Business Findings

### 📦 Product & Demand

- **Spark Plug Set** ranked first by total ordered quantity, with **3,973,447 units**.
- **Home & Kitchen** recorded the highest category sales volume.
- **Electronics** recorded the lowest category sales volume among the analyzed categories.
- Most orders involve quantities below **2,000 units**.

### 🏭 Suppliers & Quality

- **Dhaka Apparel Manufacturing** recorded the highest supplier defect rate in the analysis.

### 🚚 Transportation & Delivery

- **Air, Road, and Sea** are the dominant shipping modes, together accounting for roughly three-quarters of orders.
- **Rail** has the longest average lead time among shipping modes.
- **DB Schenker** has the highest average delivery delay.
- **Nippon Express** has the highest on-time delivery rate at **98.33%**.
- Overall on-time delivery performance is **98.00%**.
- **Canada** recorded the highest number of late deliveries, followed by **France, Brazil, and the United States**.

### 🏢 Inventory

- Warehouse stock levels generally have median values around **23,000–28,000 units** across countries.
- **Australia** has the highest average warehouse stock level.

### 💰 Sales & Orders

- **April and July** recorded the highest sales.
- **February** recorded the lowest sales.
- **December** recorded the highest number of orders.
- **February** recorded the lowest number of orders.
- **2023 and 2024** recorded the highest order counts, at approximately **2,285 and 2,286 orders**, respectively.
- **USD** was the most frequently used currency, with **17,849 transactions**.

### 📈 Cost & Correlation

- **Quantity** has the strongest relationship with total cost, with a correlation of **0.80**.
- **Delivery time** is strongly associated with delivery delays, with a correlation of **0.71**.
- **Unit cost** has a relatively weak relationship with total cost, with a correlation of **0.27**.
- The quantity vs. unit-cost regression indicates **little to no clear relationship** between order quantity and unit cost.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| **Python** | Programming language |
| **NumPy** | Numerical computations and data processing |
| **Pandas** | Data loading, cleaning, transformation and analysis |
| **Matplotlib** | Creating charts and visualizing trends |
| **Seaborn** | Statistical visualizations and exploratory analysis |
| **Jupyter Notebook** | Interactive environment for analysis and visualization |
