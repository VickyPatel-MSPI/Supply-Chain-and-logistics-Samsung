# 📦 Samsung Supply Chain & Logistics Dashboard — Power BI

[![Power BI](https://img.shields.io/badge/Power%20BI-FF2E00?style=flat&logo=powerbi&logoColor=white)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-0078D4?style=flat&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/dax/)
[![Power Query](https://img.shields.io/badge/Power%20Query-217346?style=flat&logo=microsoft&logoColor=white)](https://learn.microsoft.com/en-us/power-query/)
[![Excel](https://img.shields.io/badge/Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)](https://www.microsoft.com/en-us/microsoft-365/excel)

## 📌 Project Overview

This project is an end-to-end **interactive Supply Chain & Logistics Dashboard** built in Microsoft Power BI, themed around **Samsung's product supply chain**. It covers the full analytical pipeline — from raw data ingestion and transformation using Power Query, to advanced KPI calculations using DAX, to a polished multi-page dashboard designed for real-world business decision-making.

The dashboard spans **6 report pages**: Home, Overview, Supplier, Inventory, Shipment, and Customer — each delivering targeted insights to different stakeholders across the supply chain.

---

## 🎯 Problem Statement

Modern supply chains face challenges across multiple fronts — supplier delays, excess or insufficient inventory, shipment failures, and declining customer profitability. Without a unified analytics view, these issues remain siloed and hard to act upon.

This project addresses the following key business questions:

- Which suppliers have the longest lead times and highest unit costs?
- Which products have high defect rates or fall below safety stock thresholds?
- Which carriers are responsible for the most delayed shipments — and why?
- Which customers and sales channels are generating the most revenue and profit?
- How do inventory levels, shipment performance, and revenue trend over time?

The goal is to provide **a single source of truth** for supply chain stakeholders to monitor KPIs, identify bottlenecks, and make data-driven decisions.

---

## 🛠️ Tools & Technologies

| Tool / Technology | Purpose |
|---|---|
| **Microsoft Power BI Desktop** | Dashboard development and data visualization |
| **Power Query (M Language)** | Data ingestion, cleaning, and transformation (ETL) |
| **DAX (Data Analysis Expressions)** | KPI measures, ratios, time intelligence calculations |
| **Data Modeling** | Star schema relationships between fact and dimension tables |
| **Custom Theme** | Visual styling via [PowerBI Studio Theme Generator](https://www.powerbistudio.com/) |
| **Power BI Page Navigator** | Cross-page navigation for seamless UX |

---

## 🗂️ Dataset Description

The dataset simulates a real-world Samsung supply chain environment and includes data across the following domains:

| Table / Domain | Key Fields |
|---|---|
| **Suppliers** | `supplier_name`, `country`, `lead_time`, `unit_cost` |
| **Products** | `product_name`, `category`, `defect_rate`, `safety_stock`, `reorder_point` |
| **Inventory** | `inventory_value`, `current_stock`, `safety_stock`, `days_of_inventory` |
| **Orders** | `order_qty`, `order_date`, `channel_type`, `discount_%` |
| **Shipments** | `carrier`, `shipment_status`, `delay_reason`, `shipment_cost`, `shipped_qty`, `delivered_qty` |
| **Customers** | `customer_name`, `channel_type`, `net_revenue`, `profit`, `sales_quantity` |
| **Date Table** | `Month Short` (used for time-series trend analysis) |

Key DAX measures created include:

```dax
Total Profit          = SUM(Orders[Profit])
Profit_Margin %       = DIVIDE([Total Profit], [Total Net Revenue], 0)
Perfect order %       = DIVIDE([Perfect Orders], [Order_QTY], 0)
Average_Lead_Time     = AVERAGE(Suppliers[lead_time])
Days of Inventory     = DIVIDE([Inventory_Value], [Total Net Revenue] / 365, 0)
Delivered %           = DIVIDE([Total Deliverd Ship], [Total_Shipment], 0)
Defect_Rate           = DIVIDE([Defective Units], [Total Units], 0)
Growth Revenue        = -- Month-over-month revenue growth measure
```

---

## 📊 Power BI Dashboards

The report consists of **6 interactive pages**:

---

### 🏠 Page 1 — Home
A landing page with a branded layout and a **page navigator** to jump directly to any section of the dashboard.

---

### 🔍 Page 2 — Overview
A **cross-functional summary** giving leadership a bird's-eye view of the entire supply chain.

**KPI Cards:** Total Profit · Profit Margin % · Perfect Order % · Total Shipments · Order Quantity · Inventory Value · Total Net Revenue · Delivered Quantity

**Visuals:**
- 📊 Avg Lead Time by Supplier *(bar chart)*
- 📊 Inventory Stock by Product *(bar chart)*
- 📊 Total Delay Shipments by Carrier *(bar chart)*
- 📊 Total Revenue by Customer *(bar chart)*
- 🍩 Inventory vs Safety Stock *(donut chart)*
- 🍩 Shipment vs Delay Breakdown *(donut chart)*
- 🍩 Delivered vs Delayed Quantity *(donut chart)*

---

### 🏭 Page 3 — Supplier
Evaluates **supplier reliability, cost efficiency, and delivery performance**.

**KPI Cards:** Order Quantity · Avg Lead Time · Avg Unit Cost · Total Unit Cost

**Visuals:**
- 📊 Supplier by Avg Lead Time *(bar chart)*
- 📊 Supplier by Order Quantity *(bar chart)*
- 📊 Supplier by Cost *(bar chart)*
- 📊 Country by Avg Lead Time *(column chart)*
- 📈 Unit Cost Trend by Month *(line chart)*
- 🔘 Slicer: Cost / Qty / Supplier filter

---

### 📦 Page 4 — Inventory & Production
Monitors **stock levels, safety thresholds, reorder points, and product quality**.

**KPI Cards:** Avg Safety Stock · Days of Inventory · Inventory Value · Safety Stock

**Visuals:**
- 📊 Defect Rate by Product *(bar chart)*
- 📊 Current Stock vs Safety Stock vs Reorder Point *(combo chart)*
- 📈 Avg Defective Units by Month *(line chart)*
- 📈 Inventory Value over Time *(line chart)*

---

### 🚚 Page 5 — Shipment
Tracks **carrier performance, delivery rates, delay reasons, and shipping costs**.

**KPI Cards:** Total Delays · Shipment Quantity · Delivered Shipments · Delivered % · Total Shipment Cost

**Visuals:**
- 📊 Total Delay by Carrier *(bar + column charts)*
- 📊 Delay by Reason *(bar chart)*
- 🍩 Shipment Status Breakdown *(donut chart)*
- 📈 Shipment Cost over Time *(line chart)*

---

### 👥 Page 6 — Customer
Analyzes **revenue, profitability, channel mix, discount impact, and growth trends**.

**KPI Cards:** Total Profit · Profit Margin % · Perfect Order % · Total Net Revenue

**Visuals:**
- 📊 Revenue & Profit by Customer *(bar chart)*
- 🍩 Revenue by Channel Type *(donut chart)*
- 📈 Monthly Revenue & Profit Trend with Growth *(combo chart)*
- 🔵 Discount % vs Sales Quantity by Category *(scatter chart)*
- 🔘 Slicers: Parameter selector · Product name filter

---

## ✅ Analytical Outcomes

The dashboard delivers the following actionable insights:

- **Supplier Risk Identification** — Pinpoints suppliers with above-average lead times and unit costs, enabling procurement teams to negotiate or diversify sourcing.
- **Inventory Optimization** — Highlights products falling below safety stock or approaching reorder points, reducing the risk of stockouts or overstock situations.
- **Shipment Bottleneck Detection** — Identifies which carriers and delay reasons are responsible for the highest delivery failures, informing logistics partner decisions.
- **Customer Profitability Ranking** — Reveals which customers and sales channels drive the highest margins, helping focus retention and growth efforts.
- **Quality Control Monitoring** — Tracks defect rates by product over time to support production improvement initiatives.
- **Revenue Trend Analysis** — Month-over-month revenue and profit trends enable forecasting and early identification of performance dips.
- **Discount Impact Assessment** — Scatter analysis of discount percentage vs. sales volume uncovers whether discounting is translating into profitable volume growth.

---

## Conclusion 🎯

This Samsung Supply Chain & Logistics Dashboard demonstrates how Power BI can unify disparate supply chain data sources into a single, interactive analytics platform. By combining **Power Query ETL**, **advanced DAX measures**, and **thoughtful visual design**, the dashboard empowers operations managers, procurement teams, logistics coordinators, and sales analysts to monitor performance, detect inefficiencies, and make evidence-based decisions — all from one report.

The project serves as a strong **portfolio piece** showcasing real-world supply chain analytics skills applicable across industries including retail, manufacturing, and e-commerce.

---

## Contributions

Explore the Power BI dashboard for interactive visualizations: 
Explore the Excel word file for query and data analysis: 

> ⭐ If you found this project helpful, consider giving it a star — it helps others discover it!
