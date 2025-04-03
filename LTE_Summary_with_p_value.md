# LTE Summary with P-value

## Execution Steps

Navigate to the following directory:
```
cd /home/ubuntu/Automation/scripts/gps_info/independent_scripts
```

Run the command:
```
python3 generate_lte_summary_2.py -sd "2025-03-25" -ed "2025-03-31" -e "stage"
```

## Inputs
- **start_date**: Start date of the report
- **end_date**: End date of the report
- **env**: Environment - either `'stage'` or `'prod'` (default is `'prod'`)

## Output Summary Location
```
/home/ubuntu/Automation/scripts/gps_info/independent_scripts/lte_raw_data_summary.xlsx
```

## Data Sources
- **HEALTH Data**: `/home/ubuntu/Automation/scripts/gps_info/independent_scripts/DEVICE_LOGS`
- **drive_minutes_raw_data**: `/home/ubuntu/Automation/scripts/gps_info/independent_scripts/drive_minutes`
- **LTE raw data**: `/home/ubuntu/Automation/scripts/gps_info/independent_scripts/lte_raw_data`

