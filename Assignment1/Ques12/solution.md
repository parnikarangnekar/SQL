# Maximum Units Fulfilled by Location

## Description

Identify the location that has fulfilled the maximum number of units. This provides insights into the efficiency of different fulfillment centers.

## SQL Query

```sql
SELECT 
    pa.ADDRESS1,
    COUNT(s.SHIPMENT_ID) AS Total_shipments
FROM 
    shipment s
JOIN 
    postal_address pa ON s.destination_contact_mech_id = pa.contact_mech_id
WHERE 
    s.STATUS_ID = 'SHIPMENT_SHIPPED'
GROUP BY 
    pa.ADDRESS1
ORDER BY 
    Total_shipments DESC;
