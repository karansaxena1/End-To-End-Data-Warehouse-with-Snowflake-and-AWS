# 📦 End-to-End Data Warehouse Project 📊

## 📝 Overview
This project builds a data warehouse in Snowflake, transforming 3NF CSV data from AWS S3 into a structured model. It features raw ingestion, staging, and a DW layer with initial/incremental loads, using SCD Type 1 for Customer_Dim and SCD Type 2 for Product_Dim. Includes a Calendar_Dim created with Recursive CTE. 🌐

## 📂 Project Files
- **RAW_DDL.txt**: Schemas for raw tables (Cities, Customers, Orders, Order_Items, Products, Pincodes, Subcategories, Shipments). 🗃️
- **STAGING_LAYER.txt**: SQL for staging data transformations. 🔄
- **DW_LAYER(FINAL_LAYER).txt**: DDL/DML for Customer_Dim, Product_Dim, FCT_Orders, and Calendar_Dim with load scripts. 🏁
- **COPY_COMMANDS.txt**: COPY commands for S3 data ingestion. 📥

## 🛠️ Data Warehouse Structure
- **Raw Layer**: 8 tables with `last_updated_at` for tracking. 📋
- **Staging Layer**: Joins raw data (e.g., Customers with Pincodes/Cities) based on updates. ⚙️
- **Data Warehouse Layer**: 
  - **Customer_Dim**: Dimension table with SCD Type 1, updating attributes like Segment and Postal_Code in place. 🌍
  - **Product_Dim**: Dimension table with SCD Type 2, tracking history with Effective_Date and End_Date (e.g., '9999-12-31' for current). 📦
  - **FCT_Orders**: Fact table joining Orders and Order_Items for metrics. 📊
  - **Calendar_Dim**: Date table (2000-2050) generated using Recursive CTE. 📅

## 🚀 Key Features
- **Integration**: AWS S3 to Snowflake via IAM. ☁️
- **Transformation**: SQL-based ETL with joins/filters. ❄️
- **Load Types**: Initial and incremental loads. 🔄
- **SCD Implementation**: 
  - **SCD Type 1**: Customer_Dim overwrites old values. 🔄
  - **SCD Type 2**: Product_Dim creates new records for changes. ⏳
- **Calendar_Dim**: Recursive CTE generates daily dates with Year/Month. ⏳
- **Data Model**: Star schema with FCT_Orders and dimensions. ⭐

## 📋 Setup and Usage
1. **Prepare Data**: Upload CSVs to `s3://bucketofks/orders/2025-06-28/`. 📤
2. **Ingest Data**: Run COPY_COMMANDS.txt. 📋
3. **Create Schemas**: Execute RAW_DDL.txt. 🛠️
4. **Stage Data**: Run STAGING_LAYER.txt. 🔄
5. **Build DW**: Execute DW_LAYER(FINAL_LAYER).txt. 🏁
6. **Verify**: Use SELECT queries to check data. ✅

## 🎉 Credits
Developed with ❤️ by [Your Name]. Powered by Snowflake and AWS. Thanks to the community! 🚀

## ⏰ Last Updated
12:55 PM IST, Saturday, June 28, 2025. 🕒