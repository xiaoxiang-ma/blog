---
title: Interview Prep
date: 2020-07-13 22:00:31
tags: 
- 笔记
- SQL
categories: Data Science

---

A updating collection of notes/resources for interview prep:
- SQL
- Programming
- Stats
- Behavioural
<!-- more -->

# SQL

### Basics
```sql
SELECT a,
        b AS "field b",
        c AS field_b,
        (c + d)/2 AS c_d_avg -- Can do arithmetic operations
    FROM tablename
    WHERE g = 1  
        AND h NOT IN (2,3,4)
        AND i IS NULL
        AND (a ILIKE '%caseinsensitive%' OR "b" LIKE '%CaseSensitive%')

    LIMIT 100 -- Limits how many results
    OFFSET 1 -- Skip the first x results
```

### Logical operators
`LIKE`
- match similar values, case-sensitive
- % : wildcard, any set of characters
- _ : any individual character
`IN` 
- specify a list of values you'd like to include
- WHERE year_rank IN (1, 2, 3)
`BETWEEN`
- select only rows within a certain range
- WHERE year_rank BETWEEN 5 AND 10
`IS`
`AND`
`OR`
`NOT`

### Aggregate functions

```sql
SELECT COUNT(a),
        AVG(b),
        MIN(c),
        MAX(d) AS "MAX of d",
        SUM(e)
    FROM tutorial.aapl_historical_stock_price
```
`COUNT` counts total number of **non-null** rows in a particular column.
`SUM` adds together all the values in a particular column.
`MIN` and `MAX` return the lowest and highest values in a particular column, respectively.
`AVG` calculates the average of a group of selected values.

### Others
`ORDER BY`
- sorts data, if multiple column names given, sort in order
- automatically ascending, use DESC to show descending

`GROUP BY` 
- separate data into groups, which can be aggregated independently of one another.

`WHERE`
- for filtering results

`HAVING`
- for filtering on aggregate columns
```sql 
select Email from Person group by Email having count(Email) > 1;
```

Query clause order:
1. SELECT
2. FROM
3. WHERE
4. GROUP BY
5. HAVING
6. ORDER BY

`CASE`
- SQL's way of handling if/then logic.
- Goes in the SELECT clause
- at lease on pair of WHEN and THEN
- ELSE is optional
- must end with END


`INNER JOIN`
`LEFT JOIN`
`RIGHT JOIN`
`FULL JOIN / FULL OUTER JOIN` Combination of left and right.
`UNION`
- Combines tables by stacking/appending. e.g. `SELECT * from T1 UNION SELECT * from T2`
- Repeated/duplicate rows will not be copied. 

`UNION ALL` 
- Repeated/duplicate rows will be copied. 


Self Join
- When a table joins itself to perforom some kind of magic.
```sql
SELECT DISTINCT japan_investments.company_name,
       japan_investments.company_permalink
  FROM tutorial.crunchbase_investments_part1 japan_investments
  JOIN tutorial.crunchbase_investments_part1 gb_investments
    ON japan_investments.company_name = gb_investments.company_name
   AND gb_investments.investor_country_code = 'GBR'
   AND gb_investments.funded_at > japan_investments.funded_at
 WHERE japan_investments.investor_country_code = 'JPN'
 ORDER BY 1
```
### Examples

```sql
-- Write a SQL query to get the nth highest salary from the Employee table.
CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
BEGIN
DECLARE M INT;
SET M=N-1;
  RETURN (
      SELECT DISTINCT Salary FROM Employee ORDER BY Salary DESC LIMIT M, 1
  );
END
```
# Coding

# Stats

# Behavioural

# Resources

<!-- SQL: https://mode.com/sql-tutorial/intro-to-advanced-sql/ -->

