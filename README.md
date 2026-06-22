# Pizza Shop Sales Analysis
📊 *2026 Excel Project*

## 📌 Project Overview
A single-page Excel dashboard analyzing annual sales performance, 
seasonal trends, customer behavior patterns, and product mix optimization
for a pizza shop across hourly, daily, and monthly dimensions.

## 📜 Problem Statement
How can a pizza shop leverage sales data to identify revenue optimization 
opportunities, optimize staffing schedules, and make product/pricing 
decisions based on customer demand patterns across different time periods?

## 🗃️ Dataset
- **Source:** Kaggle — Pizza Sales Dataset
- **Coverage:** 48,621 Orders | 1 Calendar Year | 5 Data Files
- **Columns analyzed:** 10 raw variables + 5 calculated columns
- **Timespan:** Daily order transactions with timestamps (hourly granularity)

**Raw Data Files:**
1. orders.csv — Order header data (order_id, order_date, order_time)
2. order_details.csv — Line-item data (order_id, pizza_id, quantity, unit_price)
3. pizzas.csv — Product catalog (pizza_id, pizza_type_id, size, price)
4. pizza_types.csv — Pizza categories and names
5. Data Dictionary — Field definitions and data types

## 🛠️ Tools Used
| Tool | Purpose |
|---|---|
| Microsoft Excel | Single-page interactive dashboard, KPI cards, charts |
| Power Query | Data cleaning, merging 5 CSV files, ETL pipeline, 5 calculated columns |
| Pivot Tables | Summary analysis (by month, day, hour, product type, size) |
| Pivot Charts | Line charts, bar charts, pie chart visualizations |
| Excel Slicers | Interactive filtering by Month Name, Day Name (on pivots) |

## ✅ Key Findings

**1️⃣ Summer Peak Opportunity (July Revenue Surge)**
July generates $72,558 revenue (+11% above annual average of $65,155),
while May shows the highest order volume (1,935 orders). This paradox 
reveals July's success comes from premium pricing or larger orders, not 
volume. **Actionable:** Replicate July conditions to boost other months.

**2️⃣ Friday Dominates; Sunday Crashes Hard**
Friday captures 3,538 orders (35% more than Sunday's 2,624). Weekend 
is not the peak — mid-week Friday is. Sunday has the lowest order count
across all days. **Actionable:** "Sunday Family Feast" combo deals could 
recover 20-25% lost Sunday revenue (~$50k annual upside).

**3️⃣ Lunch Peak Drives Half of Daily Revenue**
12-1 PM generates 2,455-2,399 orders — the sharpest single-hour spike.
Combined with 11 AM-1 PM window, lunch accounts for ~15-18% of daily 
orders. Dinner period (5-8 PM) is more distributed. **Actionable:** 
Fast-track lunch processing, double staff 11:30 AM-1:30 PM.

**4️⃣ Chicken Pizzas Dominate (15.6% Revenue from 3 Items)**
Thai Chicken ($43.4k), BBQ Chicken ($42.8k), and Cali Chicken ($41.4k) 
account for nearly 1/6 of total revenue. Vegetarian alternatives (Brie 
Carré: $11.6k, Green Garden: $13.9k) massively underperform. 
**Actionable:** Pivot menu messaging to chicken; investigate veggie 
underperformance (marketing or demand gap?).

**5️⃣ Large is the Goldilocks Size (38% of Orders)**
Large pizzas capture 38% of all orders, followed by Medium (32%) and Extra (29%).
Extra Large is essentially niche (1% of orders). Clear size preferences suggest 
pricing optimization opportunity at Large tier. **Actionable:** Create Large-focused 
bundle (Large + 2 sides); test premium Large pricing.

**6️⃣ Order Consistency with Moderate Seasonal Variation**
Month-to-month variation is only ~$8,500 (13% range), indicating stable year-round 
demand with no dramatic crashes. This predictability enables reliable staffing and 
inventory planning. **Actionable:** Plan inventory based on monthly trends; use 
July peak insight to boost other months.


## 📊 Dashboard Preview

### Single Page Dashboard

<img width="1868" height="801" alt="Screenshot 2026-06-22 115733" src="https://github.com/user-attachments/assets/c019e92d-cc90-4f92-b339-2d680d4c3f74" />


## 📊 Dashboard Features

### Single Page Interactive Dashboard
- **5 KPI Cards:** Total Sales ($817,860), Footfall (21,350), Avg Sales/Person ($38), Avg Orders/Person (2.32), plus Month/Day slicers
- **6 Pivot Charts:**
  - Sales Trend Over the Year (line chart by month)
  - Monthly Order Trend (line chart showing order volume by month)
  - Order Volume by Hour (bar chart revealing hourly demand peaks)
  - Daily Orders (bar chart ranked by day of week)
  - Best Selling Pizzas (horizontal bar: top 3 chicken varieties)
  - Less Popular Pizzas (horizontal bar: underperforming veggie items)
  - Pizza Orders by Size (%) (pie chart showing size preference distribution)
- **2 Interactive Slicers:** Month Name, Day Name (filter all charts dynamically)
- **Professional Design:** Consistent color scheme, clear labeling, readable fonts

## 🧮 Calculated Columns (Power Query)

| Column | Logic | Type |
|---|---|---|
| **Total_Bill** | quantity × unit_price | Numeric (extends line-item price to revenue) |
| **Month_Name** | TEXT(order_date, "mmmm") | Text (Jan, Feb, Mar… for sorting) |
| **Month** | MONTH(order_date) | Numeric (1-12 for chart sorting) |
| **Day_Name** | TEXT(order_date, "dddd") | Text (Monday, Tuesday… for day-of-week analysis) |
| **Day_of_Week** | WEEKDAY(order_date) | Numeric (1=Sun, 7=Sat for consistent ordering) |
| **Hour** | HOUR(order_time) | Numeric (0-23 for hourly demand profiling) |

**Data Transformation Pipeline (Power Query):**
1. Loaded 5 CSV files separately
2. Merged orders + order_details on order_id
3. Merged pizza catalog (pizzas + pizza_types) on pizza_id
4. Removed duplicates, standardized data types
5. Added 5 calculated columns (listed above)
6. Final clean dataset: 48,621 rows × 16 columns

## 📐 Pivot Table Metrics

| Pivot | Dimensions | Measures | Purpose |
|---|---|---|---|
| Sales by Month | Month Name (rows) | SUM(Total_Bill) | Seasonal trends |
| Orders by Month | Month Name (rows) | COUNT(order_id) | Volume trends |
| Hourly Demand | Hour (rows) | COUNT(order_id) | Peak hour identification |
| Daily Orders | Day Name (rows) | COUNT(order_id) | Day-of-week patterns |
| Pizza Performance | Pizza Type (rows) | SUM(Total_Bill) | Product mix analysis |
| Size Distribution | Size (rows) | COUNT(order_id) in % | Preference profiling |

---

# 📂 Repository Structure
```
├── 01_Data
│   ├── 01_Raw_Data
│   │   ├── orders.csv
│   │   ├── order_details.csv
│   │   ├── pizzas.csv
│   │   ├── pizza_types.csv
│   │   └── Data_Dictionary.xlsx
│   │
│   └── 02_Working_Data
│       └── Cleaned_Dataset_48621_rows.xlsx
│
├── 02_Dashboard
│   └── Pizza_Shop_Sales_Dashboard.xlsx
│
├── 03_Images
│   └── Dashboard_Screenshot.png and pivot_tables images
│
└── README.md
```

## 🧮 Analytical Approach
1. **Data Integration:** Merged 5 CSV files using Power Query (relational joins on order_id, pizza_id)
2. **Data Cleaning:** Removed duplicates, standardized date/time formats, validated price ranges
3. **Feature Engineering:** Created 5 calculated columns (Month Name, Day Name, Hour, Total_Bill, etc.)
4. **Pivot Analysis:** Built 6 pivot tables capturing month, day, hour, product, and size dimensions
5. **Visualization:** Converted pivots to charts (line, bar, pie) for trend and comparison analysis
6. **Interactivity:** Added Month Name and Day Name slicers for dynamic filtering across all charts
7. **KPI Dashboard:** Assembled single-page view with KPI cards + 6 charts + slicers for executive insight

## 📊 Key Metrics Summary

| Metric | Value | Insight |
|---|---|---|
| **Total Revenue** | $817,860 | Annual sales base |
| **Total Orders** | ~21,350 | Unique customer transactions |
| **Total Footfall** | 21,350 | Unique customers (each ordered 2.32x) |
| **Avg Sales/Person** | $38 | Customer lifetime value per visit |
| **Avg Orders/Person** | 2.32 | Repeat customer frequency (excellent retention) |
| **Peak Month** | July: $72,558 | 11% above average — summer surge |
| **Peak Day** | Friday: 3,538 orders | 35% higher than Sunday |
| **Peak Hour** | 12-1 PM: 2,455 orders | Lunch rush dominates |
| **Top Pizza** | Thai Chicken: $43.4k | 5.3% of total revenue |
| **Preferred Size** | Large: 38% | Dominant customer choice |

## 💡 Business Recommendations

### Immediate Actions (Week 1-2)
- Investigate July peak drivers (event, promotion, weather?) and replicate
- Launch "Sunday Rescue" combo deals targeting 20% volume recovery
- Implement dynamic staffing schedule with Friday peak and lunch rush focus

### Short-Term (Month 1-3)
- Test premium pricing on Large pizzas during peak hours (12-1 PM, 5-7 PM)
- Create marketing campaign for underperforming Spinach Supreme + Green Garden
- Develop "Quick Lunch" fast-track menu for 11 AM-1 PM window

### Medium-Term (Month 3-6)
- Consolidate menu items using 80/20 rule — focus on top 5 performers
- Develop veggie pizza repositioning strategy (health/sustainability angle)
- Build customer loyalty program leveraging 2.32 repeat order rate

### Long-Term (Month 6-12)
- Analyze COGS by product type to calculate true profitability (not just revenue)
- Develop premium chicken pizza variants (clear demand signal)
- Implement delivery vs. pickup analysis to optimize logistics

## 🎯 Excel Skills Demonstrated

| Skill | Application |
|---|---|
| **Power Query** | 5-file merge, calculated columns (Text/Date functions), ETL pipeline |
| **Pivot Tables** | Multi-dimensional summarization (month, day, hour, category, size) |
| **Pivot Charts** | Line, bar, pie visualizations with dynamic chart titles |
| **Slicers** | Interactive Month Name and Day Name filtering across all pivots |
| **Formulas** | MONTH(), TEXT(), WEEKDAY(), HOUR() for time-based dimension creation |
| **Dashboard Design** | Single-page layout, KPI cards, 6 charts, 2 slicers, professional formatting |

---

# 👨‍💻 Author

**Suyog Lodhi**<br/>
Aspiring Data Analyst | Advanced Excel | Power Query | Pivot Tables | Data Visualization

🔗 LinkedIn: www.linkedin.com/in/suyog-lodhi-94a45825a

---


