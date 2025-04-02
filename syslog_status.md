# Syslog Status

## Description
This SQL query retrieves system log status data from the `nddeviceaction` table, joining it with `ndcommandlineactionpayload` to include command details. The query filters results based on `device_id` and specific `title` values, ordering them by the most recently updated record.

## Query
```sql
SELECT a.device_id, b.title, a.created, a.updated, a.result_location, a.payload,
       CASE  
           WHEN a.action_state = 0 THEN 'AWAITING_CONSUMPTION'
           WHEN a.action_state = 1 THEN 'CONSUMED'  
           WHEN a.action_state = 2 THEN 'EXECUTED'
           WHEN a.action_state = 3 THEN 'CANCELED'
           WHEN a.action_state = 5 THEN 'FORCE_KILLED_BY_MAX_RETRY'    
           ELSE 'unknown'  
       END AS action_status    
FROM nddeviceaction a    
LEFT JOIN ndcommandlineactionpayload b ON a.payload = b.payload
WHERE a.device_id IN ('103402401655')
      AND b.title IN ('Seperated_SysLogs (2018-09-26:15:14:49 GMT)', 'Krait_Syslogs_3 (2021-01-07:15:22:21 GMT)')
ORDER BY a.updated DESC LIMIT 1;
```

## Explanation
- **Columns Selected:**
  - `device_id`: The unique identifier of the device.
  - `title`: The associated command title from `ndcommandlineactionpayload`.
  - `created`: Timestamp when the action was created.
  - `updated`: Timestamp of the last update to the action.
  - `result_location`: The location where the result is stored.
  - `payload`: The payload data.
  - `action_status`: A derived column that translates `action_state` into human-readable status values:
    - `0`: AWAITING_CONSUMPTION
    - `1`: CONSUMED
    - `2`: EXECUTED
    - `3`: CANCELED
    - `5`: FORCE_KILLED_BY_MAX_RETRY
    - Other values default to `unknown`.

- **Filters Applied:**
  - The query filters data where `device_id` is `103402401655`.
  - It retrieves only records where `title` matches one of the specified values.
  - The results are sorted by `updated` in descending order to get the most recent entry.
  - The query limits the result set to only one record.

## Notes
- Ensure that both tables `nddeviceaction` and `ndcommandlineactionpayload` exist and contain the necessary data.
- The `payload` column is used as a join key between the two tables.
- The action states are categorized for easier interpretation of system log status.
- Adjust the filters and limit as needed to expand or refine the result set.

