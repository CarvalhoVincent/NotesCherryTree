# Scan\_de\_ports\_(avancé)

### Scan de ports (avancé)

| Port Scan Type                 | Example Command                                      |
| ------------------------------ | ---------------------------------------------------- |
| TCP Null Scan                  | sudo nmap -sN MACHINE\_IP                            |
| TCP FIN Scan                   | sudo nmap -sF MACHINE\_IP                            |
| TCP Xmas Scan                  | sudo nmap -sX MACHINE\_IP                            |
| TCP Maimon Scan                | sudo nmap -sM MACHINE\_IP                            |
| TCP ACK Scan                   | sudo nmap -sA MACHINE\_IP                            |
| TCP Window Scan                | sudo nmap -sW MACHINE\_IP                            |
| Custom TCP Scan                | sudo nmap --scanflags URGACKPSHRSTSYNFIN MACHINE\_IP |
| Spoofed Source IP              | sudo nmap -S SPOOFED\_IP MACHINE\_IP                 |
| Spoofed MAC Address            | --spoof-mac SPOOFED\_MAC                             |
| Decoy Scan                     | nmap -D DECOY\_IP,ME MACHINE\_IP                     |
| Idle (Zombie) Scan             | sudo nmap -sI ZOMBIE\_IP MACHINE\_IP                 |
| Fragment IP data into 8 bytes  | -f                                                   |
| Fragment IP data into 16 bytes | -ff                                                  |

| Option                  | Purpose                                  |
| ----------------------- | ---------------------------------------- |
| --source-port PORT\_NUM | specify source port number               |
| --data-length NUM       | append random data to reach given length |

These scan types rely on setting TCP flags in unexpected ways to prompt ports for a reply. Null, FIN, and Xmas scan provoke a response from closed ports, while Maimon, ACK, and Window scans provoke a response from open and closed ports.

| Option   | Purpose                               |
| -------- | ------------------------------------- |
| --reason | explains how Nmap made its conclusion |
| -v       | verbose                               |
| -vv      | very verbose                          |
| -d       | debugging                             |
| -dd      | more details for debugging            |
