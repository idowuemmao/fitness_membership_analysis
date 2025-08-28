---

# **🔹 GitHub README**

## 📌 Fitness Membership Analytics Report – Power BI

### **Overview**



---

### **Dataset**

**Table: `fact_data`** – includes member demographics, subscription details, service usage, and activity logs.

Key fields:

* **Demographics:** Age, Gender, Location, Join Date
* **Membership Details:** Membership Type, Subscription Model, Access Hours, Multi-Location Access
* **Financials:** Subscription Price, Discount Type, Adjusted Price, Final Price
* **Engagement:** Visits per Week, Days per Week, Avg Check-in/Check-out Time, Duration in Gym
* **Services:** Personal Training, Group Lessons, Sauna, Drink Subscription
* **Retention:** Last Visit Date, Tenure, Retention Flags

---

### **Report Structure**

The report is designed as a **3-page interactive Power BI dashboard** with storytelling flow:

#### 🔹 **Page 1 – Membership & Revenue Landscape**

**Objective:** Identify high-value segments and revenue sources.
**Visuals:**

* KPI Snapshot: Total Members, Total Revenue, ARPM, Retention Rate
* Time Series: Revenue/Members trend by Subscription Model
* Column + Line Chart: Membership Type vs Retention (30D)
* Donut Chart: Age Group & Gender distribution
* Column Chart: Revenue & Members by Subscription Model × Multi-Location Access
* Bar Chart: Location performance

**Insights:** Revenue is concentrated among specific subscription models, with multi-location members contributing higher ARPM.

---

#### 🔹 **Page 2 – Engagement & Service Impact**

**Objective:** Understand how services influence loyalty and spend.
**Visuals:**

* KPI Cards: ARPM baseline vs uplift (Drink, PT, Group, Sauna)
* Scatter Plot: Retention vs Service Count × Membership Type
* Bar Chart: Retention by Service Count
* Clustered Column: Duration, Visits/Week, Check-in Hour by Access Hour
* Cards: Revenue contribution by individual services
* Matrix: Membership × Multi-Location × Age Group segmentation
* Scatter Plot: Retention by Location × Subscription Model

**Insights:** Members engaging in multiple services retain significantly longer and generate higher revenue.

---

#### 🔹 **Page 3 – Retention & Churn Risk**

**Objective:** Spot churn risks and evaluate pricing/discount effectiveness.
**Visuals:**

* KPI Snapshot: Members, At-Risk Members, Avg Discount, ARPM, 30D Churn Rate
* Bar Chart: At-Risk Members by Tenure × Membership Type
* Bar Chart: Members, Discounts, Revenue by Access Hour
* Bar Chart: ARPM & Retention by Discount Type
* Bar Chart: ARPM & ADPM by Subscription Model × Tenure × Membership Type
* Bar Chart: Check-in Hour by Membership Type
* Matrix: Tenure × Access Hour
* Matrix: Check-in × Check-out

**Insights:**

* Early-tenure members are at higher churn risk.
* Certain discount types reduce ARPM without improving retention.
* Access-hour segmentation influences both revenue and churn patterns.

---

### **Key DAX Measures**

Some of the important DAX measures used:

```DAX
Total Revenue = SUM(fact_data[final_price])
Total Members = DISTINCTCOUNT(fact_data[member_id])
ARPM = [Total Revenue] / [Total Members]
Retention 30D = 
    DIVIDE(
        CALCULATE(DISTINCTCOUNT(fact_data[member_id]), fact_data[last_visit_date] >= TODAY()-30),
        [Total Members]
    )
Service Count = 
    (INT(fact_data[personal_training]) + INT(fact_data[attend_group_lesson]) 
    + INT(fact_data[uses_sauna]) + INT(fact_data[has_drink_subscription]))
```

---

### **Recommendations**

* **Upsell services**: Encourage single-service users to adopt at least one additional service.
* **Discount Strategy**: Optimize discount offerings — focus on loyalty discounts, reduce reliance on promos.
* **Churn Prevention**: Proactively target at-risk members in their first 3 months with engagement programs.
* **Access Optimization**: Reassess pricing for off-peak vs all-hour access to balance load and profitability.
* **Location Benchmarking**: Scale successful practices from high-performing gyms across weaker locations.

---

### **Tools & Techniques**

* **Data Prep:** Power Query for transformations, calculated columns for tenure, churn flags, and time extraction.
* **Modeling:** Star schema with supporting lookup tables (Date, Membership Type, Subscription Model, Discount Type, Gender, Location, Access Hours).
* **Visualization:** Combination of KPI cards, time series, bar/column charts, scatter plots, matrices, and funnels.
* **Interactivity:** Drill-throughs, synced slicers (Location, Membership, Date), and parameterized visuals.

---

### **Conclusion**

This report demonstrates how **data storytelling with Power BI** can transform raw membership and transaction data into **strategic insights** for:
✔ Revenue growth
✔ Retention improvement
✔ Smarter service design
✔ Optimized facility allocation

#DataAnalytics #PowerBI #CustomerRetention #FitnessAnalytics #DataStorytelling

---
