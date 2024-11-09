# Analyzing Sale of Motor Parts

You're working for a company that sells motorcycle parts, and they've asked for some help in analyzing their sales data!

They operate three warehouses in the area, selling both retail and wholesale. They offer a variety of parts and accept credit cards, cash, and bank transfer as payment methods. However, each payment type incurs a different fee.

The board of directors wants to gain a better understanding of wholesale revenue by product line, and how this varies month-to-month and across warehouses. You have been tasked with calculating net revenue for each product line and grouping results by month and warehouse. The results should be filtered so that only `"Wholesale"` orders are included.

They have provided you with access to their database, which contains the following table called `sales`.

| Column         | Data type | Description                                                  |
| -------------- | --------- | ------------------------------------------------------------ |
| `order_number` | `VARCHAR` | Unique order number.                                         |
| `date`         | `DATE`    | Date of the order, from June to August 2021.                 |
| `warehouse`    | `VARCHAR` | The warehouse that the order was made from— `North`, `Central`, or `West`. |
| `client_type`  | `VARCHAR` | Whether the order was `Retail` or `Wholesale`.               |
| `product_line` | `VARCHAR` | Type of product ordered.                                     |
| `quantity`     | `INT`     | Number of products ordered.                                  |
| `unit_price`   | `FLOAT`   | Price per product (dollars).                                 |
| `total`        | `FLOAT`   | Total price of the order (dollars).                          |
| `payment`      | `VARCHAR` | Payment method—`Credit card`, `Transfer`, or `Cash`.         |
| `payment_fee`  | `FLOAT`   | Percentage of `total` charged as a result of the `payment` method. |

## Solution

**SQL Query**

```sql
SELECT product_line,
    CASE WHEN EXTRACT('month' from date) = 6 THEN 'June'
        WHEN EXTRACT('month' from date) = 7 THEN 'July'
        WHEN EXTRACT('month' from date) = 8 THEN 'August'
    END as month,
    warehouse,
	SUM(total) - SUM(payment_fee) AS net_revenue
FROM sales
WHERE client_type = 'Wholesale'
GROUP BY product_line, warehouse, month
ORDER BY product_line, month, net_revenue DESC
```

**Result of the Query**

| 0    | Braking system | August | Central | 3039.41 |
| ---- | -------------- | ------ | ------- | ------- |
| 1    | Braking system | August | West    | 2500.67 |
| 2    | Braking system | August | North   | 1770.84 |
| 3    | Braking system | July   | Central | 3778.65 |
| 4    | Braking system | July   | West    | 3060.93 |