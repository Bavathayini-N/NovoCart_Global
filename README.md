# NovoCart Global - E-Commerce Platform

##  Project Overview

NovaCart Global is a fast-growing international online marketplace specializing in consumer electronics and accessories, including laptops, mobile devices, peripherals, and smart gadgets. 

The project implements a medallion architecture (Bronze → Silver → Gold) to process and analyze sales data across multiple countries, channels, and product categories.

##  Architecture

### Data Pipeline Layers


Bronze Layer (Raw Data)
    ↓
Silver Layer (Cleaned & Transformed)
    ↓
Gold Layer (Business Logic & Analytics)
    ↓
KPI and Dashboard (Visualizations)


#### Bronze Layer
- **Purpose**: Ingests raw sales, product, and customer data from source systems.
- **Characteristics**: Contains unprocessed, original data with minimal validation.


#### Silver Layer
- **Purpose**: Cleans, validates, and transforms raw data for analytics.
- **Characteristics**: Removes duplicates, standardizes formats, enriches with reference data.
- **Outputs**: Cleaned sales, product, and customer tables ready for business logic.

#### Gold Layer
- **Purpose**: Applies business logic, aggregates metrics, and prepares data for reporting.
- **Characteristics**: Contains curated tables for KPIs, dashboards, and data cubes.
- **Outputs**: Fact and dimension tables, KPI calculations, multi-dimensional analytics.

### Technology Stack
- **Platform**: Databricks
- **Language**: PySpark (Python)
- **Storage**: Unity Catalog
- **Visualization**: Lakeview Dashboards

## 📁 Project Structure


NovoCart_Global/
├── bronze/          # Raw data ingestion notebooks
├── silver/          # Data cleaning and transformation
├── gold/           
│   ├── nb_gold     # Gold layer transformations
│   └── nb_gold_kpi # KPI calculations and data cube
└── README.md       # This file


## 🗄️ Data Model

### Catalog: `novocart_global`
### Schema: `novocart_gold`

#### Fact Table
- **fact_sales**: Core sales transactions with order details, quantities, prices, and status

#### Dimension Tables
- **dim_product**: Product information (ID, name, category, price, currency)
- **dim_customer**: Customer details (ID, name, email, country, channel, registration date)
- **dim_country**: Country reference data
- **dim_channel**: Sales channel information (web, mobile)

## 📈 Key Performance Indicators (KPIs)

### 1. Total Revenue
**Metric**: Sum of all sales revenue in USD  

### 2. Revenue by Country
**Metric**: Sales breakdown by geographic region  
**Countries**: UK, DE, ES, CN, IN  
**Visualization**: Bar chart

### 3. Revenue by Channel
**Metric**: Sales performance across channels  
**Channels**: Web vs Mobile  
**Visualization**: Pie chart

### 4. Completed Order Count
**Metric**: Number of successfully completed orders  
**Filter**: `order_status = 'completed'`

### 5. Completed Order Rate
**Metric**: Percentage of orders that reach completion  
**Formula**: (Completed Orders / Total Orders) × 100

### 6. Average Order Value (AOV)
**Metric**: Mean revenue per order  
**Formula**: Total Revenue / Total Orders

### 7. Top 5 Products by Revenue
**Metric**: Best-performing products  
**Visualization**: Horizontal bar chart  
**Includes**: Product ID, name, and total revenue

### 8. Active Customers Count
**Metric**: Unique customers excluding unknown/invalid records    

### 9. Customer Acquisition by Month
**Metric**: Monthly customer registration trends  
**Visualization**: Line chart  
**Time Range**: Aggregated by month

### 10. Data Quality Score
**Metric**: Percentage of valid customer records in sales data  
**Value**: 0.98  
**Formula**: (Valid Records / Total Records) × 100

## 🎯 Data Cube

### Multi-Dimensional Analysis

The data cube provides comprehensive analytics across multiple dimensions:

**Dimensions:**
- Country Code
- Sales Channel
- Product ID & Name
- Year & Month

**Metrics:**
- Total Revenue
- Order Count
- Average Order Value
- Active Customers Count


## 📊 Dashboard

### NovoCart Global KPIs Dashboard

Interactive dashboard featuring:

**Counter Widgets (6):**
- Total Revenue
- Completed Orders
- Order Completion Rate
- Average Order Value
- Active Customers
- Data Quality Score

**Visualizations (4):**
- Revenue by Country (Bar Chart)
- Revenue by Channel (Pie Chart)
- Top 5 Products by Revenue (Bar Chart)
- Customer Acquisition by Month (Line Chart)

**Data Table (1):**
- Data Cube - Multi-dimensional analysis table