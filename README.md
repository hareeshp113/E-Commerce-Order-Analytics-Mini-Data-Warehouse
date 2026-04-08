# E-Commerce Order Analytics — Mini Data Warehouse

## Project Overview
This project simulates a mini data warehouse for an e-commerce business.  
The raw data was stored in messy CSV files, so I built a Python ETL pipeline to clean the data, generated staging files, loaded them into SQLite, created a Star Schema, and answered business questions using SQL.

## Tech Stack
- Python
- Pandas
- SQLite
- SQL
- Google Colab

## Project Workflow
1. Extract raw CSV files
2. Clean customers, products, and orders data
3. Generate staging CSV files
4. Load staging data into SQLite
5. Create Star Schema tables:
   - dim_customers
   - dim_products
   - dim_date
   - fact_orders
6. Run business SQL queries

## Files
- `mini_project.py` → main ETL + warehouse script
- `raw_orders_project.csv` → raw orders data
- `raw_customers.csv` → raw customers data
- `raw_products.csv` → raw products data
- `stg_orders.csv` → cleaned staging orders
- `stg_customers.csv` → cleaned staging customers
- `stg_products.csv` → cleaned staging products

## Data Cleaning Rules
### Orders
- Removed duplicate orders
- Dropped rows with missing customer_id
- Dropped rows with missing order_date
- Filled missing unit_price using product master lookup
- Added `total_amount = (quantity * unit_price) - discount`

### Customers
- Removed duplicate customer rows
- Filled missing email with placeholder format
- Filled missing age with median age
- Filled missing city with `Unknown`
- Added `age_group`

### Products
- Removed duplicate products
- Filled missing category with `Electronics`
- Converted product names to title case

## Star Schema
### Dimension Tables
- `dim_customers`
- `dim_products`
- `dim_date`

### Fact Table
- `fact_orders`

## Business Questions Answered
1. Which customer spent the most in total?
2. Which product generates the highest total revenue?
3. How does revenue trend week by week across January?
4. Which store has the highest average order value?
5. What percentage of orders have a discount applied?

## How to Run
```bash
pip install -r requirements.txt
python mini_project.py
