# DAX Measures

## Sales Summary
```dax
Total Sales = SUM(orders_cleandata[sales])

Total Profit = SUM(orders_cleandata[profit])

Total Orders = DISTINCTCOUNT(orders_cleandata[order_id])

Total Customers = DISTINCTCOUNT(orders_cleandata[customer_id])

Profit Margin % = DIVIDE ( [Total Profit], [Total Sales] )

Avg Order Value = DIVIDE ( [Total Sales], [Total Orders] )
```

## Distribution Performance
```dax
On-Time Orders = 
CALCULATE ( COUNTROWS (orders_cleandata), orders_cleandata[is_late] = FALSE )

Late Orders = 
CALCULATE ( COUNTROWS ( orders_cleandata ), orders_cleandata[is_late]= TRUE )

On-Time Delivery % = 
DIVIDE( [On-Time Orders] , COUNTROWS(orders_cleandata))

Late Delivery % = 1 - [On-Time Delivery %]

Late Delivery Risk % = 
AVERAGE ( orders_cleandata[late_delivery_risk] )

Avg Delivery Days = 
AVERAGE(orders_cleandata[delivery_days])
```

## Time Intelligence
```dax
Sales YTD = 
TOTALYTD( [Total Sales], dim_date[Date] )

Sales Last Month = 
CALCULATE([Total Sales], DATEADD(dim_date[Date], -1, MONTH))

Sales MOM % = 
VAR CurrentSales = [Total Sales]
VAR PrevSales = [Sales Last Month]
RETURN DIVIDE (CurrentSales - PrevSales, PrevSales)
```

## Conditional Formating for Bar Chart
```dax
Bar Color Category Profit = 
VAR CurrentValue = [Total Profit]
VAR MaxValue = MAXX(ALLSELECTED(orders_cleandata[category_name]), [Total Profit])
RETURN
IF(CurrentValue = MaxValue, "#F2994A", "118DFF")
```

