# Syslog Report


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

### 4. Sample Output Format
The resulting Excel file will have the following structure:

| deviceId         | action_status | OTA_Version                                      | syslogs_status | Power-off reason: Triggered from GP_FAULT1 | PXL_SOF syncpt timeout! err | CsimuxFrameError_Regular | tegra-i2c 3180000.i2c: no acknowledge from address 0x24 | tegra-i2c 3180000.i2c: no acknowledge from address 0x3d | tegra-i2c c250000.i2c: no acknowledge from address 0x3d | tegra-i2c c250000.i2c: no acknowledge from address 0x3c | run_out_cam_version:red | DIAG_SPI: SPI Flash not detected - ff:ff:ff | ISP port 0 timed out! | bcpu-throttle-alert cooling state: 0 -> 1 | mcpu-throttle-alert cooling state: 0 -> 1 |
|-----------------|--------------|------------------------------------------------|---------------|-----------------------------------------|-----------------------------|---------------------------|-------------------------------------------------|-------------------------------------------------|-------------------------------------------------|-------------------------------------------------|-------------------------|----------------------------------------------|------------------------|--------------------------------------------|--------------------------------------------|
| 103242401306    | EXECUTED     | 85.3.40.sp.5.6.6.rc.4_Denver_cores             | yes           | 0                                       | 0                           | 0                         | 0                                               | 0                                               | 0                                               | 0                                               | 0                       | 0                                            | 0                      | 0                                          | 0                                          |
| 103242401277    | EXECUTED     | 85.3.40.sp.5.6.6.rc.4_Denver_cores             | yes           | 0                                       | 0                           | 0                         | 0                                               | 0                                               | 0                                               | 0                                               | 0                       | 1                                            | 0                      | 0                                          | 0                                          |
| 103242401300    | EXECUTED     | 85.3.40.sp.5.6.6.rc.4_Denver_cores             | yes           | 0                                       | 0                           | 0                         | 0                                               | 0                                               | 0                                               | 0                                               | 0                       | 0                                            | 0                      | 0                                          | 0                                          |
| 103242401298    | EXECUTED     | 85.3.40.sp.5.6.6.rc.4_Denver_cores             | yes           | 0                                       | 0                           | 0                         | 0                                               | 0                                               | 0                                               | 0                                               | 0                       | 0                                            | 0                      | 0                                          | 0                                          |
| 103242401320    | EXECUTED     | 85.3.40.sp.5.6.6.rc.4_Denver_cores             | yes           | 0                                       | 0                           | 0                         | 0                                               | 0                                               | 0                                               | 0                                               | 0                       | 0                                            | 0                      | 0                                          | 0                                          |

