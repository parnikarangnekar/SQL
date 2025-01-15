
# Payment Captured But Not Shipped Order Items

## Description

Identify orders where payment has been captured, but the items have not been shipped yet or shipment has not yet been created/initiated.

## SQL Query

```sql
SELECT
    s.SHIPMENT_ID, s.STATUS_ID, opp.STATUS_ID, opp.ORDER_ID
FROM
    shipment s
JOIN order_payment_preference opp
    ON s.PRIMARY_ORDER_ID = opp.ORDER_ID
WHERE
    opp.STATUS_ID = 'PAYMENT_SETTLED'
    AND s.STATUS_ID != 'SHIPMENT_SHIPPED';
