# Execution of Syslog Report

## Overview
This document outlines the steps to:
1. Save a list of device IDs into a file on a remote Ubuntu machine.
2. Run a script to generate a syslog report.
3. Download the generated report to the local machine.

## Prerequisites
- A remote machine accessible via SSH (`ubuntu@10.100.11.212` in this case).
- Necessary permissions to create files and execute scripts on the remote machine.
- `scp` installed on the local machine for file transfer.

---

## Step 1: Save Device List to a File on Remote Machine
To create the `devices` file on the remote machine, execute the following command from your local terminal:

```bash
ssh ubuntu@10.100.11.212 "echo -e '103242401277
103242401298
103242401300
103242401306
103242401320' > /home/ubuntu/Automation/jay/devices"
```

This command:
- Logs into the remote machine via SSH.
- Creates (or overwrites) the file `/home/ubuntu/Automation/jay/devices`.
- Stores the list of device IDs, each on a new line.

---

## Step 2: Execute the Syslog Report Script
Once the `devices` file is saved, run the script `fetch_and_create_syslog_report.sh` on the remote machine by executing:

```bash
ssh ubuntu@10.100.11.212 "bash +x /home/ubuntu/Automation/jay/fetch_and_create_syslog_report.sh"
```

This command:
- Connects to the remote machine.
- Runs the `fetch_and_create_syslog_report.sh` script using Bash.

Ensure that the script exists at `/home/ubuntu/Automation/jay/` and has execution permissions. If needed, make it executable with:

```bash
ssh ubuntu@10.100.11.212 "chmod +x /home/ubuntu/Automation/jay/fetch_and_create_syslog_report.sh"
```

---

## Step 3: Download the Generated Syslog Report
After the script executes, the syslog report will be available at `/home/ubuntu/Automation/jay/syslog_pattern_output.xlsx` on the remote machine. To download it to your local `~/Downloads` directory, use:

```bash
scp ubuntu@10.100.11.212:/home/ubuntu/Automation/jay/syslog_pattern_output.xlsx ~/Downloads/
```

This command:
- Copies the file from the remote machine to the local `~/Downloads` directory.

---

## Optional: Automate the Entire Process in a Single Script
To simplify execution, create a local script `run_syslog_report.sh` with the following content:

```bash
#!/bin/bash

# Step 1: Save device list
ssh ubuntu@10.100.11.212 "echo -e '103242401277
103242401298
103242401300
103242401306
103242401320' > /home/ubuntu/Automation/jay/devices"

# Step 2: Run the script
ssh ubuntu@10.100.11.212 "bash +x /home/ubuntu/Automation/jay/fetch_and_create_syslog_report.sh"

# Step 3: Download the output file
scp ubuntu@10.100.11.212:/home/ubuntu/Automation/jay/syslog_pattern_output.xlsx ~/Downloads/

echo "Syslog report downloaded successfully!"
```

### To Use This Script:
1. Save the above content into a file named `run_syslog_report.sh` on your local machine.
2. Grant execute permission:
   ```bash
   chmod +x run_syslog_report.sh
   ```
3. Run the script:
   ```bash
   ./run_syslog_report.sh
   ```

---

## Conclusion
By following these steps, you can easily automate the process of saving a device list, executing a script, and retrieving the output file from a remote Ubuntu machine. The optional script further simplifies the workflow for repeated executions.

