    
# 📊 Sales Dashboard – Power BI

**File:** `Sales dashboard.pbix`  
**Tool Used:** Power BI Desktop  
**Author:** Pooja VT  
**Purpose:** Interactive sales analytics dashboard with dynamic KPIs controlled by user selection.

---

## 🔧 Features

### 1. Dynamic KPI Switching
The measure `Selected Measure2` dynamically updates based on the selection in `'Table (2)'[Selector]`.

- **Selector Options:**
  - `1` → Total Sales: `SUM(sales_value)`
  - `2` → Profit: `SUM(sales_value) - SUM(cost_of_sales)`
  - Default fallback → `SUM(sales_value)`

### 2. Interactivity
- Users can switch KPI focus using:
  - A **slicer** bound to `'Table (2)'[Selector]`
  - Or **buttons** with **bookmarks** that set specific slicer values

### 3. Report Elements
- **KPI Cards:** Real-time value updates based on selected metric
- **Line Charts:** Sales trends over time
- **Bar Charts:** Product or region-level breakdown
- **Slicers:** Custom date, region, category filtering

---

## 🧠 DAX Logic

```dax
Selected Measure2 = 
SWITCH(
    SELECTEDVALUE('Table (2)'[Selector]),
    1, SUM('classicmodels sales_data_for_power_bi'[sales_value]),
    2, SUM('classicmodels sales_data_for_power_bi'[sales_value]) - SUM('classicmodels sales_data_for_power_bi'[cost_of_sales]),
    SUM('classicmodels sales_data_for_power_bi'[sales_value])
)
```

---

## 📌 Notes

- Buttons alone cannot change measure context — use them with **bookmarks + visible slicer**.
- Always ensure `'Table (2)'[Selector]` slicer is connected properly.

---

## 📤 Usage Instructions

1. Open the `.pbix` file using Power BI Desktop.
2. Use the **Selector Slicer** or **buttons** to switch between metrics.
3. Interact with filters to view dynamic updates in charts and KPIs.

---

## 🛠 Future Enhancements (Optional)
- Add Profit Margin (%)
- Add ROI metric
- Add Export-to-PDF or Share-to-email automation

---

    
