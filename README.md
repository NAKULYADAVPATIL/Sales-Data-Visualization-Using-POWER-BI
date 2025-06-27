
# **Sales Performance Analysis for Esparx Matrix Solutions** 
Sales performance analysis is critical for organizations looking to **optimize revenue, monitor trends, and enhance strategic decision-making**. This project applies **best practices in business intelligence (BI) and data visualization** to provide actionable insights into **YoY growth, customer satisfaction, and profitability**.  

---

## **🔹 Key Features & Functionalities**  

###  Executive-Level Insights**  
- **YoY Growth Analysis:** High-level growth trends using **REMOVEFILTERS()** to ensure business-wide visibility.  
- **Gross Sales & Profit KPIs:** Key financial indicators with comparisons to historical performance.  
- **Customer Satisfaction Score:** Aggregated customer feedback displayed dynamically.  

###  Operational-Level Insights**  
- **Monthly & Yearly Trend Analysis:** Performance tracking over time, responding to slicer selections.  
- **Dynamic Bookmarking:** Interactive navigation for seamless storytelling.  
- **DAX-Based Performance Metrics:** Implementing **calculated measures for in-depth analysis** of sales trends.  

###  Advanced DAX Calculations**  
- **Dynamic YoY Growth:**  
   - **Executive View:** Business-wide perspective ignoring slicer filters.  
   - **Operational View:** YoY growth influenced by user-selected filters.  
- **Customer Satisfaction Score:** Aggregating satisfaction ratings dynamically.  

---

##  Technologies & Tools Used**  
| **Technology** | **Purpose** |  
|---------------|------------|  
| Power BI | Data visualization & dashboard development |  
| DAX (Data Analysis Expressions) | Advanced calculations & KPIs |  
| Power Query | Data transformation & cleansing |  
| SQL (optional) | Data extraction & preprocessing |  
| Excel | Initial dataset review & structuring |  

---

## **📂 Project Structure**  
```bash
📁 Sales-Performance-Analysis
│── 📂 Data          # Contains raw & cleaned data files  
│── 📂 PowerBI       # Power BI .pbix file with reports  
│── 📂 DAX           # Custom DAX scripts & calculations  
│── 📂 Screenshots   # Dashboard previews & insights  
│── 📜 README.md     # Documentation (this file)  
```


##  DAX Code Snippets**  

### **YoY Growth – Executive Level**  
```DAX
Executive YoY% Dynamic = 
VAR _LatestYear = 
    CALCULATE( MAX( CalendarTable[Year] ), ALL( CalendarTable ) )

VAR _PreviousYear = _LatestYear - 1

VAR _Current12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _LatestYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Previous12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _PreviousYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Result =
    IF(
        NOT(ISBLANK(_Previous12MonthSales)), 
        (_Current12MonthSales - _Previous12MonthSales) / _Previous12MonthSales, 
        BLANK()
    )

RETURN _Result
```
---
