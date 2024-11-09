# Analyzing Sale of a Motor Part Store

## Description

Working on behalf of a company that sells motorcycle parts, you'll dig into their data to help them understand their revenue streams. You'll build up a query to find out how much net revenue they are generating across their product lines, segregating by date and warehouse.

## Instructions

Find out how much `Wholesale` net revenue each `product_line` generated per month per `warehouse` in the dataset.

- The query should be saved as

   

  ```
  revenue_by_product_line
  ```

   

  using the SQL cell provided, and contain the following:

  - `product_line`,
  - `month`: displayed as `'June'`, `'July'`, and `'August'`,
  - `warehouse`, and
  - `net_revenue`: the sum of `total` minus the sum of `payment_fee`.

- The results should be sorted by `product_line` and `month`, followed by `net_revenue` in descending order.