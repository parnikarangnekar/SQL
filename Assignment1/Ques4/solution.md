### Shipped units By Location

#### Description
Identify the number of units that have been shipped, categorized by different locations. Gain insights into the distribution of shipped units across various locations.

```sql
SELECT 
    pa.ADDRESS1, 
    COUNT(s.SHIPMENT_ID) AS Total_shipments
FROM shipment s
JOIN postal_address pa 
    ON s.destination_contact_mech_id = pa.contact_mech_id 
WHERE s.STATUS_ID IN (
    SELECT STATUS_ID 
    FROM shipment_status 
    WHERE STATUS_ID = 'shipment_shipped'
)
GROUP BY pa.ADDRESS1;
```

