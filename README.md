# Inventory-Analysis-To-Flag-At-Risk-Inventory

## Project Preview

Stop losing sales to stockouts! 
build a dynamic inventory risk dashboard to predict stockouts 4 weeks ahead and prevent $1.2M in losses—perfect for Black Friday, holidays, or demand surges.

<img width="1346" height="457" alt="Week 2 Screenshot (100)" src="https://github.com/user-attachments/assets/5e9a150f-a44f-498a-9bf8-ff1511048ca2" />
<img width="1326" height="473" alt="week 2 Screenshot " src="https://github.com/user-attachments/assets/b6606cbe-4d76-4bfc-93c6-5951aeec0053" />


### Data Sources

Sales Data: The primary data used for the analysis is DA & BI Week 2 Project

### Tools

- Excel Power Query
- Power Pivot
- DAX Measures 
- PivotTables, Slicers, Conditional Formatting


### Data Cleaning/Preparation

In this initial phase, i perform the fellowing tasks:
 - Clean & model data with Power Query (no coding!)
 - Power Pivot relationships (star schema)
 - Write DAX formulas to forecast demand & flag risks

### EExploratory Data Analysis

- Which products are at risk of stockout in the next 4 weeks?
- Does current inventory cover the predicted demand for each product?
- Which product categories are most vulnerable to stockouts?

### Data Analysis

Including some interesting DAX formula
```DAX
Forecast4Weeks:=CALCULATE(SUM(Forecast[Forecast Quantity]),DATESINPERIOD(Dates[Dates],TODAY(),28,DAY))

RiskFlag:=IF(ISBLANK([Forecast4Weeks]),"No Forecast",IF([Forecast4Weeks]>SUMX(RELATEDTABLE(Inventory),[Current Stock]),"AT RISK","OK"))

SurgeAdjustedForecast:=[Forecast4Weeks]*IF(HASONEVALUE(Surge_Control[Surge Factor]),VALUES(Surge_Control[Surge Factor]),1)

Risk_Flag:=IF([SurgeAdjustedForecast]>SUM(Inventory[Current Stock]),"AT RISK","OK")
```
### Result/Findings

The analysis result are summarized as follows:
1. Build an interactive dashboard with slicers, KPIs, and alerts
2. Simulate demand surges (1.5x, 2.0x) for real-world scenario




