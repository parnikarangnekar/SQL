# Orders Completed Hourly

## Description

Analyze and present the distribution of completed orders on an hourly basis.

## SQL Query

```sql
SELECT 
    COUNT(ORDER_ID), 
    HOUR(STATUS_DATETIME) AS hr
FROM 
    order_status os
WHERE 
    os.STATUS_ID = 'Order_completed'
GROUP BY 
    hr;
