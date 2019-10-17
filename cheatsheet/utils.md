# Utils
### Get Interface by command
```bash
interface=$(netstat -nr | grep -E 'UG|UGSc' | grep -E '^0.0.0|default' | grep -E '[0-9.]{7,15}' | awk -F' ' '{print $NF}')
# or get the route to github
interface=$(ip route get $(nslookup github.com | grep Server | awk -F' ' '{print $NF}') | sed -rn 's|.*dev\s+(\S+)\s+src.*$|\1|p')
```

### get ipv4 address
```bash
ipAddr=$(ip a s "${interface}" | sed -rn 's|.*inet ([0-9\.]{7,15})/[0-9]{2} brd.*$|\1|p')
```

