# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program:

```
Server.py
import socket
from pythonping import ping
s = socket.socket()
# Bind to localhost and port
s.bind(('localhost', 8000))
# Listen for connections
s.listen(5)
print("Ping Server started... Waiting for connection")
# Accept connection
c, addr = s.accept()
print("Connected to:", addr)
while True:
    hostname = c.recv(1024).decode()
    if not hostname:
        break
    try:
        result = ping(hostname, count=4, verbose=False)
        c.send(str(result).encode())
    except:
        c.send("Host Not Found".encode())
c.close()

Client.py
import socket
# Create socket
s = socket.socket()
# Connect to server
s.connect(('localhost', 8000))
while True:
    website = input("Enter the website you want to ping: ")
    if website.lower() == "exit":
        break
    s.send(website.encode())
    result = s.recv(1024).decode()
    print("\nPing Result:\n", result)
s.close()

Traceroute.py
import os
print("Running Traceroute...\n")
os.system("C:\\Windows\\System32\\tracert.exe google.com")

```
## Output
<img width="1048" height="436" alt="Screenshot 2026-05-23 205852" src="https://github.com/user-attachments/assets/0a68ac60-07b9-4312-8758-714dafc961f7" />
<img width="1031" height="551" alt="Screenshot 2026-05-23 205902" src="https://github.com/user-attachments/assets/19ea4ed4-b7f5-4185-9184-9de8e2578c44" />
<img width="1041" height="748" alt="Screenshot 2026-05-23 205922" src="https://github.com/user-attachments/assets/1901fb6c-1446-4a8b-8173-eb54571f4481" />

## Result
Thus Execution of Network commands Performed 
