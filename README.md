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
Program

server.py
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")
c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    try:
        hostname = c.recv(1024).decode('utf-8')
        if not hostname or hostname.lower() == 'exit':
            print("Client disconnected.")
            break
        response = ping(hostname, verbose=False, count=4)
        c.send(str(response).encode('utf-8'))
    except Exception as e:
        c.send(f"Ping failed: {e}".encode('utf-8'))

c.close()
```
client.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter the website you want to ping (or type 'exit' to quit): ")
    s.send(ip.encode('utf-8'))
    if ip.lower() == 'exit':
        break
    print(s.recv(4096).decode('utf-8'))

s.close()
```
## Output
CLIENT
<img width="830" height="266" alt="image" src="https://github.com/user-attachments/assets/401ef3eb-1720-4564-b80c-5926b32b0748" />
server
<img width="850" height="205" alt="image" src="https://github.com/user-attachments/assets/62e87391-554c-428a-837b-2a506ec98710" />
netstat
<img width="514" height="573" alt="image" src="https://github.com/user-attachments/assets/4a50431a-4c7e-4ceb-9e96-44d28774a892" />
ipconfig
<img width="517" height="394" alt="image" src="https://github.com/user-attachments/assets/a3b84054-bedb-4802-9234-367ed34443f0" />
<img width="433" height="324" alt="image" src="https://github.com/user-attachments/assets/fa470607-d463-42a4-a5df-91ff8dea4acc" />
nslookup
traceroute
<img width="816" height="348" alt="image" src="https://github.com/user-attachments/assets/c06821f6-632e-4b63-8cd6-ed6b628a2847" />
tcpdump
<img width="833" height="515" alt="image" src="https://github.com/user-attachments/assets/145fbe42-26a4-4d69-9238-9a30379e2fde" />






## Result
Thus Execution of Network commands Performed 
