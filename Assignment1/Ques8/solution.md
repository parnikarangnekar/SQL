# Orders with More Than One Item in a Single Ship Group

## Description

Identify orders that contain more than one item within a single shipment group.

## SQL Query

```sql
SELECT oi.ORDER_ID, oi.SHIP_GROUP_SEQ_ID, COUNT(oi.ORDER_ITEM_SEQ_ID) AS itemsInShipGrp
FROM order_item oi
GROUP BY oi.ORDER_ID, oi.SHIP_GROUP_SEQ_ID
HAVING COUNT(oi.ORDER_ITEM_SEQ_ID) > 1;



