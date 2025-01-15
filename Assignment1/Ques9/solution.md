# Orders with Multiple Items Grouped and Shipped Together in a Single Shipment

## SQL Query

```sql
SELECT oi.ORDER_ID, oisg.SHIP_GROUP_SEQ_ID, COUNT(oi.ORDER_ITEM_SEQ_ID) AS item_count
FROM order_item oi
JOIN order_item_ship_group oisg ON oi.ORDER_ID = oisg.ORDER_ID
GROUP BY oisg.SHIP_GROUP_SEQ_ID, oi.ORDER_ID
HAVING COUNT(oi.ORDER_ITEM_SEQ_ID) > 1
ORDER BY oi.ORDER_ID;
