This script will perform system check on your linux's machine CPU, Memory, and Disk Usage.
<br>

```
#!/bin/bash
echo "System Health Report - $(date)"
echo "-------------------------------"
echo "CPU Load: $(uptime)"
echo "Memory Usage:"
free -h
echo "Disk Usage:"
df -h /
```
<br>

