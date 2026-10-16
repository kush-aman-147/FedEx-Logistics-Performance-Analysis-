# 🚚 FedEx Logistics Performance Analysis

> An exploratory data analysis (EDA) of shipment history data that measures delivery reliability, freight cost efficiency, shipment modes, and vendor performance, turning raw logistics records into KPIs for data-driven supply chain decisions.

---

## 📌 Overview

Logistics networks depend on on-time delivery and controlled freight costs. This project analyzes **10,324 shipment records** to evaluate how well deliveries perform against their schedules, what drives freight cost, and how shipment modes, vendors, countries, and product groups compare. The data is cleaned, enriched with engineered KPIs (lead time, on-time flag, freight per kg), and explored with visualizations.

The analysis is organized around four KPI dimensions:

- **Service Performance:** lead time, delay, and on-time delivery rate
- **Cost Efficiency:** total freight spend, freight cost per kg, freight-to-value ratio
- **Shipment Volume:** shipment counts, quantity, and value trends over time
- **Vendor, Route & Product Performance:** comparisons by vendor, country, and product group

## ❓ Problem Statement

Analyze historical shipment data to:

- Evaluate delivery performance and identify the causes of delays
- Find the main freight cost drivers and cost-saving opportunities
- Compare shipment modes (Air, Air Charter, Truck, Ocean) on cost and delivery efficiency
- Assess vendor and country-level performance gaps
- Build actionable KPIs to improve delivery reliability and cost-effectiveness

## 📂 Dataset

**File:** `SCMS_Delivery_History_Dataset.csv`

| Attribute | Details |
|---|---|
| Records | 10,324 rows × 33 columns |
| Period | 2006 – 2015 (scheduled delivery dates) |
| Coverage | 43 countries, 73 vendors, 4 shipment modes |
| Product groups | ARV, HRDT, ANTM, ACT, MRDT |
| Duplicates | 0 |
| Missing values | Shipment Mode (360), Dosage (1,736), Line Item Insurance (287) |

**Key columns:** Country, Vendor, Shipment Mode, Vendor INCO Term, Product Group, PO/Scheduled/Delivered dates, Line Item Quantity & Value, Weight (kg), Freight Cost (USD), Line Item Insurance (USD).

## 🛠️ Tools & Technologies

- **Language:** Python
- **Libraries:** Pandas, NumPy, Matplotlib, Seaborn
- **Environment:** Jupyter Notebook

## 🔬 Methods

1. **Data Loading & Inspection:** shape, info, summary statistics, duplicate and null checks
2. **Data Cleaning:** standardized column names, converted date columns to datetime, cleaned text-based numeric fields (freight cost, weight), and filled missing weight and freight values with the median
3. **Feature Engineering:**
   - `lead_time` = delivered date − PO sent date (days)
   - `on_time` flag = delivered date vs. scheduled date
   - `freight_per_kg` = freight cost ÷ weight
4. **KPI Calculation:** total shipments, average lead time, on-time/delay rate, total freight cost
5. **Visualization:** missing-value analysis, with planned charts for lead time by mode, country KPIs, and correlations

## 💡 Key Insights

- **Average lead time is about 105.6 days** from PO sent to delivery, indicating long procurement-to-delivery cycles.
- **About 15.8% of shipments were delivered after the scheduled date** (`on_time` flag = 1 when delivery is later than schedule), so roughly 84% arrived on or before schedule.
- **Total freight spend is about $88.98M** across all shipments (after median imputation of missing values).
- **Air dominates shipping:** 6,113 shipments (~59%), followed by Truck (2,830), Air Charter (650), and Ocean (371).
- **ARV products make up about 83% of shipments** (8,550 of 10,324).
- **Data quality matters:** zero-weight records make the average freight per kg infinite, so outlier handling is needed for reliable cost-per-kg analysis.

## 📊 Dashboard / Outputs

- `Performance_Analysis.ipynb`: data cleaning, feature engineering, KPI calculations, and the missing-values bar chart
- `Project_info.ipynb`: project summary, problem statement, and business objectives
- **KPI outputs:** total shipments, average lead time, on-time delivery rate, total freight cost

> No interactive dashboard is included; all outputs are notebook-based.

## ✅ Result & Conclusion

The project turns raw shipment records into a clean, analysis-ready dataset with core logistics KPIs. The results show long average lead times, a modest share of late deliveries, and a strong reliance on air freight, which together point to opportunities in cost optimization, shipment-mode selection, and vendor management. Future work can extend the analysis with mode-wise lead time and cost comparisons, vendor and country rankings, and an interactive dashboard (Power BI / Tableau).

---

**Author:** Aman Kushwaha
