STEPS: (nmap)

1. Download the nmap from the official website.
2. Use command prompt in your windows and type ipconfig to view your local ip address. (192.168.0.103)
3. Copy the ip address and type "nmap -sS 192.168.0.103/24".
4. The IP addresses and open ports are present in the task report.

STEPS: (wireshark)

1. Download the wireshark from the official website.
2. Use command prompt and run the command 'nmap -sS 192.168.0.103/24' in there.
3. After using wireshark it starts showing the relevant ip addresses and open ports available inside the network we are using.

Tools used: 

1. nmap
2. wireshark