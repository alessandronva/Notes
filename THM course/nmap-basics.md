# Nmap basics

| Nmap flag      | Description                                                                          |
| -------------- | ------------------------------------------------------------------------------------ |
| -sV            | Attempts to determine the version of the services running                            |
| -p \<x> or -p- | Port scan for port \<x> or scan all ports                                            |
| -Pn            | Disable host discovery and scan for open ports                                       |
| -A             | Enables OS and version detection, executes in-build scripts for further enumeration  |
| -sC            | Scan with the default Nmap scripts                                                   |
| -v             | Verbose mode                                                                         |
| -sU            | UDP port scan                                                                        |
| -sS            | TCP SYN port scan                                                                    |



sudo nmap -p- --min-rate=1000 -T5 -sV # --min rate could help avoid expend to much time scanning all the usable ports: 65535



