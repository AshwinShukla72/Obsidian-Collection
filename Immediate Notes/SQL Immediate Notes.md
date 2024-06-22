
```SQL
-- Write a query to calculate the average daily 
-- price change in Apple stock, grouped by year

SELECT
   AVG(close - open) AS average_daily_price_change
 FROM
   tutorial.aapl_historical_stock_price
GROUP BY year
```

```ad-question
Write a query that calculates the lowest and highest prices that Apple stock achieved each month.
```
```SQL
SELECT
  MONTH,
  MIN(low) AS lowest,
  MAX(high) AS highest
FROM
  tutorial.aapl_historical_stock_price
GROUP BY
  month
ORDER BY month
```

```ad-question
Write a query that includes a column that is flagged "yes" when a player is from California, and sort the results with those players first.
```
```SQL
SELECT
  player_name,
  state,
  CASE
    WHEN state = 'CA' THEN 'yes'
    ELSE 'no'
  END AS from_california
FROM
  benn.college_football_players
ORDER BY
  from_california DESC
```

```ad-question
Write a query that includes players' names and a column 
that classifies them into four categories based on height. 
Keep in mind that the answer we provide is only one of many possible answers,
since you could divide players' heights in many ways.

```SQL
SELECT
  player_name,
  height,
  weight,
CASE
    WHEN height < 65 THEN 'under 65'
    WHEN height > 65 THEN 'over 65'
    WHEN height > 65
    AND height <= 75 THEN '65-75'
    WHEN height > 75
    AND height <= 85 THEN '75-85'
    ELSE 'Over 85'
  END AS height_group
FROM
  benn.college_football_players
```
