# DAX Measures Documentation

Complete set of DAX formulas used in the e-commerce Power BI dashboard, categorized by purpose for better readability.

---

1. YTD Sales

YTD Sales = TOTALYTD(SUM(ecommerce_data[sales_per_order]), 'Calendar'[Date])

2. YTD Quantity

YTD Qty = TOTALYTD(SUM(ecommerce_data[order_quantity]), 'Calendar'[Date])
Computes the total number of items sold year-to-date.

3. YTD Profit

YTD profit = TOTALYTD(SUM(ecommerce_data[profit_per_order]), 'Calendar'[Date].[Date])
Returns the cumulative profit from the beginning of the year to the current date.

4. YTD Profit Margin

YTD Profit Margin = TOTALYTD([Profit Margin], 'Calendar'[Date])
Calculates the year-to-date profit margin based on the Profit Margin measure.

Profitability Measures
5. Profit Margin

Profit Margin = DIVIDE(SUM(ecommerce_data[profit_per_order]), SUM(ecommerce_data[sales_per_order]))
Shows the profit margin by dividing total profit by total sales.

Previous Year-To-Date (PYTD) Measures
6. PYTD Sales

PYTD Sales = CALCULATE(SUM(ecommerce_data[sales_per_order]), DATESYTD(SAMEPERIODLASTYEAR('Calendar'[Date])))
Calculates the total sales for the same time period in the previous year.

7. PYTD Quantity

PYTD Qty = CALCULATE(SUM(ecommerce_data[order_quantity]), DATESYTD(SAMEPERIODLASTYEAR('Calendar'[Date])))
Gets the quantity sold for the year-to-date of the previous year.

8. PYTD Profit

PYTD Profit = CALCULATE(SUM(ecommerce_data[profit_per_order]), DATESYTD(SAMEPERIODLASTYEAR('Calendar'[Date])))
Shows profit for the previous year's same date range.

9. PYTD Profit Margin

PYTD Profit Margin = CALCULATE([Profit Margin], DATESYTD(SAMEPERIODLASTYEAR('Calendar'[Date])))
Returns the profit margin for the year-to-date in the previous year.

Year-Over-Year (YoY) Measures
10. YoY Sales

YOY Sales = ([YTD Sales] - [PYTD Sales]) / [PYTD Sales]
Measures the percentage growth or decline in sales compared to the previous year.

11. YoY Quantity

YOY Qty = ([YTD Qty] - [PYTD Qty]) / [PYTD Qty]
Calculates year-over-year change in quantity sold.

12. YoY Profit

YOY Profit = ([YTD profit] - [PYTD Profit]) / [PYTD Profit]
Displays the change in profit compared to the previous year.

13. YoY Profit Margin

YoY Profit Margin = ([YTD Profit Margin] - [PYTD Profit Margin]) / [PYTD Profit Margin]
Indicates the change in profit margin from the previous year.

Visual Indicators
14. Sales Icon

Sales Icon = 
    VAR positive_icon = UNICHAR(9650)
    VAR negetive_icon = UNICHAR(9660)
    VAR result = IF([YOY Sales] > 0, positive_icon, negetive_icon)
    RETURN result
Displays an up (▲) or down (▼) arrow depending on whether YoY sales increased or decreased.

15. Qty Icon

Qty Icon = 
    VAR positive_icon = UNICHAR(9650)
    VAR negetive_icon = UNICHAR(9660)
    VAR result = IF([YOY Qty] > 0, positive_icon, negetive_icon)
    RETURN result
Visual indicator for year-over-year change in quantity sold.

16. Profit Icon

Profit Icon = 
    VAR positive_icon = UNICHAR(9650)
    VAR negetive_icon = UNICHAR(9660)
    VAR result = IF([YOY Profit] > 0, positive_icon, negetive_icon)
    RETURN result
Arrow symbol representing YoY profit performance.

17. Profit Margin Icon

Profit Margin Icon = 
    VAR positive_icon = UNICHAR(9650)
    VAR negetive_icon = UNICHAR(9660)
    VAR result = IF([YoY Profit Margin] > 0, positive_icon, negetive_icon)
    RETURN result
Icon showing visual cue for change in profit margin year-over-year.



You can now copy and paste this into your **DAX.md** file. All the DAX formulas are listed together, along with a brief explanation of each. Let me know if you need any further adjustments!
