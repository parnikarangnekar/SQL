### 2. Shipment by Tracking Number

**Description:**
View or analyze shipments based on their unique tracking numbers. Each shipment is identified and tracked using a specific tracking number.

---

**SQL Query:**

```sql
SELECT 
    s.SHIPMENT_ID, 
    s.STATUS_ID, 
    srs.TRACKING_ID_NUMBER
FROM 
    shipment_route_segment srs
JOIN 
    shipment s 
ON 
    srs.SHIPMENT_ID = s.SHIPMENT_ID 
WHERE 
    srs.TRACKING_ID_NUMBER IS NOT NULL
    AND srs.TRACKING_ID_NUMBER IN (
        SELECT 
            TRACKING_ID_NUMBER 
        FROM 
            shipment_route_segment 
        GROUP BY 
            TRACKING_ID_NUMBER
        HAVING 
            COUNT(TRACKING_ID_NUMBER) = 1
    );
