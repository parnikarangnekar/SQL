### Average number of shipments per month

#### Description
Calculate the average number of shipments made per month by dividing the total number of shipments by the number of months.

```sql
SELECT
    COUNT(s.SHIPMENT_ID) AS Total_shipment,
    MAX(ss.STATUS_DATE) AS Maximum_date,
    MIN(ss.STATUS_DATE) AS Min_date,
    TIMESTAMPDIFF(MONTH, MIN(ss.STATUS_DATE), MAX(ss.STATUS_DATE)) + 1 AS Difference_in_months,
    COUNT(s.SHIPMENT_ID) / (TIMESTAMPDIFF(MONTH, MIN(ss.STATUS_DATE), MAX(ss.STATUS_DATE)) + 1) AS Avg_shipments_per_month
FROM shipment s
JOIN shipment_status ss 
    ON s.SHIPMENT_ID = ss.SHIPMENT_ID
WHERE ss.STATUS_ID = 'shipment_shipped';
