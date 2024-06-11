~~~ SQL

A. Average Market Capitalization

SELECT 
AVG(`Mar Cap - Crore`) AS avg_market_cap
FROM `financial analytics data`


B. Top Companies by Market Capitalization

SELECT `Name`, sum(`Mar Cap - Crore`)
FROM `financial analytics data`
group by 1
ORDER BY 2 DESC
LIMIT 10;


C. Top Companies by Quarterly Sales

SELECT `Name`, `Sales Qtr - Crore`
FROM `financial analytics data`
ORDER BY 2 DESC
LIMIT 10;


D. Correlation between market capitalization and quarterly sales

SELECT 
    (SUM((`Mar Cap - Crore` - avg_x) * (`Sales Qtr - Crore` - avg_y)) / COUNT(*)) /
    (STDDEV(`Mar Cap - Crore`) * STDDEV(`Sales Qtr - Crore`)) AS correlation
FROM 
    (
        SELECT 
            `Mar Cap - Crore`,
            `Sales Qtr - Crore`,
            (SELECT AVG(`Mar Cap - Crore`) FROM `financial analytics data`) AS avg_x,
            (SELECT AVG(`Sales Qtr - Crore`) FROM `financial analytics data`) AS avg_y
        FROM 
            `financial analytics data`
    ) AS subquery;


E. Average Sales Quater

SELECT AVG(`Sales Qtr - Crore`) AS avg_Sales_Qtr
FROM `financial analytics data`



