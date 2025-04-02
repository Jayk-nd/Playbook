# Automation Process Documentation

## Working Directory
```
/home/ubuntu/Automation/jay/
```

## Steps

### 1. Save Device List
Save the following device list in a file named `devices` at location:
```
/home/ubuntu/Automation/jay/devices
```
#### Device List:
```
103242401277
103242401298
103242401300
103242401306
103242401320
```

### 2. Run Script
Execute the script with the following command:
```
bash +x fetch_and_create_syslog_report.sh
```
**Note:** The script should be located in the same directory.

### 3. Result File
The output will be saved at:
```
/home/ubuntu/Automation/jay/syslog_pattern_output.xlsx
```

