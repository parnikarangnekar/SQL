### Last week's imported orders & items count

#### Description
Identify and count the orders and items that were imported in the system during the last week.

```sql
SELECT 
    DATE(oh.order_date) AS Order_date, 
    COUNT(oh.ORDER_ID) AS Order_count, 
    COUNT(oi.ORDER_ITEM_SEQ_ID) AS Iter_count
FROM order_header oh 
JOIN order_item oi 
    ON oh.ORDER_ID = oi.ORDER_ID
WHERE oh.order_date >= CURDATE() - INTERVAL 7 DAY
GROUP BY DATE(oh.order_date);
```
