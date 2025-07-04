This ```bash``` script will ping ip address ranges based on your desire.

```
#!/bin/bash

# Define the range of IP addresses and their descriptions
declare -A IP_DESCRIPTIONS=(
  ["10.172.1.1"]="<DEVICE HOSTNAME>"
  ["10.172.1.2"]="<DEVICE HOSTNAME>"



# Add more IP addresses and descriptions as needed
)

# Function to convert IP address to a number
ip_to_num() {
  echo $1 | awk -F. '{print ($1 * 256 ** 3) + ($2 * 256 ** 2) + ($3 * 256) + $4}'
}

# Function to convert a number to an IP address
num_to_ip() {
  local ip num=$1
  for e in {3..0}; do
    ((octet = num / (256 ** e)))
    ((num -= octet * 256 ** e))
    ip+=$octet.
  done
  echo ${ip%.}
}

# Convert start and end IP addresses to numbers
START_IP=<START OF THE IP ADDRESS THAT YOU WANT TO PING>
END_IP=< LAST IP ADDRESS THAT YOU WANT TO PING>
start_num=$(ip_to_num $START_IP)
end_num=$(ip_to_num $END_IP)

# Loop through the range of IP addresses
for ((i=start_num; i<=end_num; i++)); do
  IP=$(num_to_ip $i)
  # Ping the IP address with a timeout of 1 second
  ping -c 1 -W 1 $IP > /dev/null 2>&1
  # Check if the ping was successful
  if [ $? -ne 0 ]; then
    DESCRIPTION=${IP_DESCRIPTIONS[$IP]:-"No description available"}
    echo "IP address $IP ($DESCRIPTION) is unreachable"
  fi
done
```
<br>
