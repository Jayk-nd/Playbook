# Voltage and Ignition Data

## Description
This SQL query retrieves specific device-related data from the `public.nddeduplication` table. It filters the data based on a given `device_id` and a specified time range.

## Query
```sql
SELECT  
    device_id,  
    (data_json->>'udid')::integer AS udid,  
    start_time,  
    end_time,  
    (device_modes->>'voltage')::numeric AS voltage,  
    (device_modes->>'ignition_status')::integer AS ignition_status  
FROM  
    public.nddeduplication  
WHERE  
    device_id IN ('6603049992')  
    AND start_time >= '2025-02-18'  
    AND end_time <= '2025-02-25';
```

## Explanation
- **Columns Selected:**
  - `device_id`: The unique identifier of the device.
  - `udid`: Extracted from `data_json` and cast to an integer.
  - `start_time`: The start timestamp of the record.
  - `end_time`: The end timestamp of the record.
  - `voltage`: Extracted from `device_modes` JSON and cast to numeric.
  - `ignition_status`: Extracted from `device_modes` JSON and cast to integer.

- **Filters Applied:**
  - The query filters data where `device_id` is `6603049992`.
  - The `start_time` should be on or after `2025-02-18`.
  - The `end_time` should be on or before `2025-02-25`.

## Notes
- Ensure that the `data_json` and `device_modes` columns exist and store valid JSON data.
- The `udid`, `voltage`, and `ignition_status` values are extracted using JSON operations.
- The date filters should be adjusted as needed to modify the time range.

