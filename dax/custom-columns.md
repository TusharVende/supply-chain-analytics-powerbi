# Remove Duplicates

```m-code
>sort shipping_date descending
>Right-click the header of the order_item_id column
>Select Remove Duplicates
```


# Custom Columns

```m-code
delivery_days = List.Max({[shipping_date] - [order_date], #duration(0, 0, 0, 0)})

is_late = if [days_ship_real] > [days_ship_shed] then true else false

profit_margin = if [order_item_total] > 0 then Number.Round([profit]/[order_item_total], 4) else 0

customer_zipcode1 = Text.PadStart([customer_zipcode], 5, "0")
```

