# Scan\_de\_ports\_(avancé)

### Scan de ports (avancé)

| Example Command                                       | Port Scan Type                 |
| ----------------------------------------------------- | ------------------------------ |
| `sudo nmap -sN MACHINE_IP`                            | TCP Null Scan                  |
| `sudo nmap -sF MACHINE_IP`                            | TCP FIN Scan                   |
| `sudo nmap -sX MACHINE_IP`                            | TCP Xmas Scan                  |
| `sudo nmap -sM MACHINE_IP`                            | TCP Maimon Scan                |
| `sudo nmap -sA MACHINE_IP`                            | TCP ACK Scan                   |
| `sudo nmap -sW MACHINE_IP`                            | TCP Window Scan                |
| `sudo nmap --scanflags URGACKPSHRSTSYNFIN MACHINE_IP` | Custom TCP Scan                |
| `sudo nmap -S SPOOFED_IP MACHINE_IP`                  | Spoofed Source IP              |
| `--spoof-mac SPOOFED_MAC`                             | Spoofed MAC Address            |
| `nmap -D DECOY_IP,ME MACHINE_IP`                      | Decoy Scan                     |
| `sudo nmap -sI ZOMBIE_IP MACHINE_IP`                  | Idle (Zombie) Scan             |
| `-f`                                                  | Fragment IP data into 8 bytes  |
| `-ff`                                                 | Fragment IP data into 16 bytes |

| Option                   | Purpose                                  |
| ------------------------ | ---------------------------------------- |
| `--source-port PORT_NUM` | specify source port number               |
| `--data-length NUM`      | append random data to reach given length |

These scan types rely on setting TCP flags in unexpected ways to prompt ports for a reply. Null, FIN, and Xmas scan provoke a response from closed ports, while Maimon, ACK, and Window scans provoke a response from open and closed ports.

| Option     | Purpose                               |
| ---------- | ------------------------------------- |
| `--reason` | explains how Nmap made its conclusion |
| `-v`       | verbose                               |
| `-vv`      | very verbose                          |
| `-d`       | debugging                             |
| `-dd`      | more details for debugging            |
