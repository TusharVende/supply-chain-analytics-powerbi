# Custom Columns - Power Query

## Sales Perfomance KPI
```dax
Total Sales = SUM(orders_cleandata[sales])

Total Profit = SUM(orders_cleandata[profit])

Total Orders = DISTINCTCOUNT(orders_cleandata[order_id])

Profit Margin % = DIVIDE ( [Total Profit], [Total Sales] )

Avg Order Value = DIVIDE ( [Total Sales], [Total Orders] )
```
