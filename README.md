# Supply Chain Logistics Dashboard | Power BI Portfolio Project

<div align="center">

**Interactive Power BI dashboard for supply chain analytics, inventory management, and logistics tracking — built as a portfolio project for Data Analyst roles**

</div>

***

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Business Problem](#business-problem)
- [Solution & Key Features](#solution--key-features)
- [Technologies Used](#technologies-used)
- [Key DAX Measures I Created](#key-dax-measures-i-created)
- [Data Modeling Approach](#data-modeling-approach)
- [Key Insights & KPIs](#key-insights--kpis)
- [Screenshots](#screenshots)
- [How to Reproduce](#how-to-reproduce)
- [What I Learned](#what-i-learned)
- [Get in Touch](#get-in-touch)

***

## 🎯 Project Overview

I built this **Supply Chain Logistics Dashboard** in Power BI to demonstrate my ability to:
- Transform raw supply chain data into actionable business insights
- Build interactive, professional dashboards for stakeholders
- Write advanced DAX measures for complex analytics
- Model data using best practices (star schema)
- Tell compelling data stories for business decision-making

This project covers the **entire supply chain workflow**: Supplier → Manufacturer → Inventory → Logistics → Customer, tracking critical KPIs like revenue, profit margins, on-time delivery, and inventory turnover .

***

## 🏢 Business Problem

Supply chain managers need to answer critical questions:
- How much revenue and profit are we generating?
- What's our profit margin percentage?
- How many orders are delivered defect-free AND on-time?
- What's our current inventory stock level?
- How long does supplier delivery take (lead time)?
- Are we meeting on-time delivery targets?
- What are our logistics/shipping costs?

**My Solution**: Built an interactive Power BI dashboard that answers all these questions with real-time visuals, slicers, and drill-down capabilities .

***

<img width="1326" height="731" alt="Power BI Desktop 01-06-2026 14_44_35" src="https://github.com/user-attachments/assets/56aa11a8-8d74-4cc1-ad48-53d67dbbe6d4" />


## ✨ Solution & Key Features

| Feature | What I Built |
|---------|--------------|
| **Interactive Dashboard** | Multi-page dashboard with slicers (Product, Date, Region) and drill-down  |
| **Supply Chain KPI Cards** | Real-time metrics: Revenue, Profit, Margin %, Perfect Order %, Stock Level  |
| **Advanced DAX Measures** | Custom calculations including `Perfect Order %` with complex logic  |
| **Power Query ETL** | Cleaned and transformed Samsung supply chain data from multiple CSV files  |
| **Star Schema Model** | Proper relationships between fact (Sales) and dimension tables  |
| **Geographic Maps** | Logistics route visualization with location-based insights  |
| **Theme Customization** | Professional color scheme for stakeholder presentations  |

***

## 🛠️ Technologies Used

| Technology | My Usage |
|------------|----------|
| **Power BI Desktop** | Dashboard development, visualization, and publishing |
| **DAX** | Created 8+ custom measures including profit margin, perfect order %, lead time |
| **Power Query (M)** | Data cleaning, folder-based import, parameter creation |
| **Excel/CSV** | Source data (Samsung supply chain dataset) |
| **Data Modeling** | Star schema with 8 tables and proper relationships |

***

## 🔢 Key DAX Measures I Created

I wrote these measures from scratch to calculate business-critical metrics:

### Basic Measures
```dax
Total Revenue = SUM('Sales'[Net Revenue])
```
```dax
Total Profit = SUM('Sales'[Profit])
```
```dax
Profit Margin % = DIVIDE([Total Profit], [Total Revenue])
```

### Advanced Measures
```dax
Total Sales Quantity = SUM('Sales'[Quantity])
```
```dax
Current Stock Level = SUM('Inventory'[Stock Level])
```
```dax
Average Lead Time = AVERAGE('Supply'[Lead Time])
```
```dax
Total Shipments = DISTINCTCOUNT('Shipment'[Shipment ID])
```

### ⭐ Perfect Order % (Complex Measure I Built)
```dax
Perfect Order % = 
VAR PerfectOrder = 
    CALCULATE(
        [Total Shipments],
        'Production'[Defect Rate] < 1,
        'Shipment'[Delivery Status] = "Successfully Delivered"
    )
VAR TotalOrders = [Total Shipments]
RETURN
    DIVIDE(PerfectOrder, TotalOrders) * 100
```

**Why this matters**: This measure tracks orders that are BOTH defect-free AND on-time — a critical supply chain KPI .

***

## 📊 Data Modeling Approach

I designed a **star schema** with:

- **1 Fact Table**: `Sales` (transactions, revenue, profit, quantity)
- **7 Dimension Tables**: `Products`, `Customers`, `Suppliers`, `Inventory`, `Production`, `Shipment`, `Date`

**Relationships I Created** (all One-to-Many):
- `Products[Product ID]` → `Sales[Product ID]`
- `Date[Date]` → `Sales[Order Date]`
- `Customers[Customer ID]` → `Sales[Customer ID]`
- `Suppliers[Supplier ID]` → `Purchase Orders[Supplier ID]`
- `Inventory[Product ID]` → `Sales[Product ID]`

I placed the fact table in the center and dimension tables around it — following Power BI best practices .

***

## 📈 Key Insights & KPIs Tracked

| KPI | Business Value |
|-----|----------------|
| **Total Revenue** | Tracks overall money generated  |
| **Total Profit** | Shows actual profit made after costs  |
| **Profit Margin %** | Indicates profitability efficiency  |
| **Perfect Order %** | Measures quality + on-time delivery performance  |
| **Current Stock Level** | Helps prevent stockouts and overstocking  |
| **Average Lead Time** | Identifies supplier performance issues  |
| **On-Time Delivery %** | Tracks logistics reliability  |
| **Inventory Turnover** | Shows how fast stock is moving  |

***

## 📸 Screenshots

**Dashboard Overview Page** — Main supply chain flow with KPI cards showing revenue, profit, margin, and perfect order percentage

*(Add your dashboard screenshot here by uploading to your repo and linking it)*

***

## 🚀 How to Reproduce

If you want to learn from this project or reproduce it:

1. **Get the dataset**: [Samsung Supply Chain Data (Google Drive)](https://drive.google.com/drive/folders/18b7oPFTuvEIxb5c79WNc-5AMij88Tclm) 
2. **Open Power BI Desktop** and import data from folder
3. **Create folder path parameter** (best practice for reusable queries) 
4. **Build star schema** with proper relationships 
5. **Write DAX measures** as shown in the "Key DAX Measures" section 
6. **Design dashboard** with KPI cards, charts, maps, and slicers 
7. **Publish to Power BI Service** for sharing with stakeholders

***

## 📚 What I Learned

Through this project, I developed skills in:

### Power Query
- Folder-based data import for multiple CSV files 
- Parameter creation for dynamic folder paths 
- ETL workflows for real-world supply chain datasets 

### DAX
- Writing measures from scratch for business metrics 
- Using `VAR` for complex calculations (Perfect Order %) 
- Understanding `CALCULATE`, `DIVIDE`, `DISTINCTCOUNT` functions 

### Data Modeling
- Identifying fact vs. dimension tables 
- Building star schema with proper relationships 
- Setting cross-filter direction best practices 

### Dashboard Design
- Creating interactive visuals (maps, charts, cards) 
- Storytelling with data for business stakeholders 
- Professional formatting and theme customization 

***

## 🤝 Get in Touch

**I'm Mohit Raj — a Data Analyst based in Bhopal, Madhya Pradesh, India.**

I'm actively looking for **Data Analyst, BI Analyst, or Data Visualization roles** where I can use my Power BI, DAX, and data storytelling skills.

📧 **Interested in discussing this project or potential opportunities?**

- Feel free to reach out via LinkedIn
- Check out my other portfolio projects in this repository
- Let's connect and explore how I can add value to your team

***

<div align="center">

**⭐ If this project is helpful, please give this repository a star!**

**📌 Skills Demonstrated**: Power BI | DAX | Data Modeling | Power Query | Data Visualization | Supply Chain Analytics | Business Intelligence

**💼 Perfect for**: Data Analyst Roles | BI Analyst Positions | Data Visualization Jobs | Portfolio Showcase

Made with ❤️ by **Mohit Raj** — Indore, India

</div>
