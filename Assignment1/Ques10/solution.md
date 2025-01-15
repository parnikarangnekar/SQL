# Orders Brokered But Not Shipped

## Description

Identify orders that have been brokered (arranged or negotiated) but have not been shipped yet or shipment has not yet been created/initiated.

## SQL Query

```sql
SELECT 
    oh.ORDER_ID,
    oh.ORDER_DATE
FROM 
    order_header oh
LEFT JOIN 
    shipment s ON oh.ORDER_ID = s.SHIPMENT_ID
WHERE 
    oh.STATUS_ID = 'ORDER_APPROVED'
    AND s.STATUS_ID IS NULL;
