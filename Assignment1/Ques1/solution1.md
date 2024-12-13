# 1. Total number of shipments in January 2022 first quarter

**Question:**  
Determine the total count of shipments made during the first quarter of 2022, specifically in the month of January.

**Solution Query:**
```sql
select
    sum(case
        when STATUS_DATE >= '2022-01-01' and STATUS_DATE <= '2022-01-31' then 1
        else 0
    end) as shipment_in_jan,
    count(SHIPMENT_ID) as shipment_in_quarter
from
    shipment_status ss
where
    status_id = 'shipment_shipped'
    and (STATUS_DATE >= '2022-01-01'
    and STATUS_DATE <= '2022-03-31');