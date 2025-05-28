# 🧠 Data Warehouse Project

## 📊 Project Overview

This project is a full-stack **Data Warehouse solution** for a business involving sales, marketing, operations, and inventory. The objective is to provide actionable insights using KPIs through dimensional modeling and efficient ETL processes.

---

## 🎯 KPI Beneficiaries
- Sales Tracking
- Marketing Planning
- Operations Management
- Inventory Management

---

## 🔍 Business Insight Areas
- Sales Performance Over Time
- Product Performance & Sales Trends
- Customer Behavior & Cross-Selling
- Geographical Sales Performance
- Ad Timing Optimization
- Order Metrics & Sales Efficiency

---

## 📈 Key KPIs

### Sales Performance Over Time
- **Total Revenue** = `SUM(Quantity Ordered × Price Each)`
- **Total Orders** = `COUNT(DISTINCT Order ID)`

### Product Performance
- **Total Quantity Sold per Product**
- **Revenue per Product**
- **Product with Highest/Lowest Revenue**

### Geographical Analysis
- **Revenue by City**
- **Quantity Sold by City**
- **Top City by Sales Revenue**

### Marketing Optimization
- **Peak Purchase Hour**
- **Peak Purchase Day**
- **Ad Recommendation Hour**

### Sales Metrics
- **Average Order Value (AOV)** = `Total Revenue / Number of Orders`
- **Orders > $500** (Premium Buyers)

---

## 🏗️ Star Schema Design

### 📊 Fact Tables

| Fact Table          | Description                                           | Type                         |
|---------------------|-------------------------------------------------------|------------------------------|
| Fact_Sales          | Sales per product per order                           | Transactional                |
| Fact_HourlySales    | Aggregated hourly sales performance                   | Periodic Snapshot (Hourly)   |
| Fact_OrderSummary   | Summary of orders (quantity, value, items)            | Aggregated                   |


###Physical model of the source system 
<img width="377" alt="image" src="https://github.com/user-attachments/assets/b4d091c1-6523-4e3e-b406-6254c562e7d4" />


###Star Schema 
<img width="468" alt="image" src="https://github.com/user-attachments/assets/d4070002-51d9-45c1-8fc0-b9492e4ad7c6" />

---

### 📋 Dimension Tables

| Dimension      | Attributes                            | Type                         |
|----------------|----------------------------------------|------------------------------|
| Dim_Date       | Date_ID, FullDate, Day, Month, Year    | Conformed / Static           |
| Dim_Time       | Time_ID, Hour                          | Static / Role-playing        |
| Dim_Product    | Product_ID, Product_Name               | Conformed                    |
| Dim_Geography  | Geo_ID, Address, City, State           | Conformed                    |
| Dim_File       | FileSourceKey, FileName, Year, Month   | Outrigger (ETL Metadata)     |
| Dim_Order      | Order_ID, Date_ID, Geo_ID              | Degenerate / Role-playing    |

---

## 📏 Measures

### Fact_Sales
- `Quantity_Ordered` (Integer) – Additive
- `Price_Each` (Decimal) – Semi-additive
- `Total_Revenue` (Decimal) – Additive

### Fact_HourlySales
- `Orders_Count` – Additive
- `Hourly_Revenue` – Additive
- `Last_Extract_Date` – Descriptive

### Fact_OrderSummary
- `Total Order Value` – Additive
- `Total Quantity` – Additive
- `Number of Items` – Additive

---

## ⚙️ ETL Process

1. **Extract**: Source data from CSVs/files.
2. **Transform**:
   - Clean & map fields
   - Join dimensions
   - Calculate revenue and KPIs
3. **Load**:
   - Load into `Dim_*` and `Fact_*` tables
   - Use SSIS packages for automation

---

## 🗂️ ETL Screenshots Included
- Loading `Dim_Order`, `Dim_Geography`, `Dim_Time`
- Creating `Fact_Sales`, `Fact_HourlySales`, `Fact_OrderSummary`
- Control Flow Diagram
- Scheduling & Deployment Screens
- Truncation Queries

---

## 🛠️ Technologies Used
- **Microsoft SQL Server**
- **SSIS (SQL Server Integration Services)**
- **Power BI** (for dashboarding)
- **Star Schema Modeling**
- **Dimensional Data Warehousing**

---

## 📅 Scheduling & Deployment
- ETL pipelines scheduled via SQL Server Agent
- Full automation of extract, load, and refresh processes
- Control flow design for error handling and monitoring
- Dashboard : ![plpl](https://github.com/user-attachments/assets/52a06a83-dca5-460c-bff2-72fbd2ed492d)
![pkpk](https://github.com/user-attachments/assets/0ea5a617-0657-4ab9-aa42-2aa08849442f)



---

> ✅ This project provides a modern, maintainable Data Warehouse solution aligned with business strategy and BI best practices.

---

## 📬 Contact

For questions, feedback, or collaboration:
**Mohamed Rabea** – [LinkedIn](https://www.linkedin.com/in/mohamed-rabea-991373261/) | [Email](mailto:mhmdrby769@email.com)

