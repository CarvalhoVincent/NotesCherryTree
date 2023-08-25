# Live\_host

### Live host

| Example Command                             | Scan Type              |
| ------------------------------------------- | ---------------------- |
| `sudo nmap -PR -sn MACHINE_IP/24`           | ARP Scan               |
| `sudo nmap -PE -sn MACHINE_IP/24`           | ICMP Echo Scan         |
| `sudo nmap -PP -sn MACHINE_IP/24`           | ICMP Timestamp Scan    |
| `sudo nmap -PM -sn MACHINE_IP/24`           | ICMP Address Mask Scan |
| `sudo nmap -PS22,80,443 -sn MACHINE_IP/30`  | TCP SYN Ping Scan      |
| `sudo nmap -PA22,80,443 -sn MACHINE_IP/30`  | TCP ACK Ping Scan      |
| `sudo nmap -PU53,161,162 -sn MACHINE_IP/30` | UDP Ping Scan          |

Remember to add `-sn` if you are only interested in host discovery without port-scanning. Omitting `-sn` will let Nmap default to port-scanning the live hosts.

| Option | Purpose                          |
| ------ | -------------------------------- |
| `-n`   | no DNS lookup                    |
| `-R`   | reverse-DNS lookup for all hosts |
| `-sn`  | host discovery only              |
