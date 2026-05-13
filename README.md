# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
       ip=c.recv(1024).decode()
       try:
          c.send(address[ip].encode())
       except KeyError:
          c.send("Not Found".encode())

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
## OUPUT - ARP

<img width="1920" height="1080" alt="Screenshot 2026-05-13 103536" src="https://github.com/user-attachments/assets/a996f656-a3de-42e6-b511-69ec69d78fb0" />

<img width="1920" height="1080" alt="Screenshot 2026-05-13 103721" src="https://github.com/user-attachments/assets/a8dae1cd-37e2-4bca-820e-9fb940ce7d27" />

## PROGRAM - RARP
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
ip=c.recv(1024).decode()
try:
c.send(address[ip].encode())
except KeyError:
c.send("Not Found".encode())

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
ip=input("Enter MAC Address : ")
s.send(ip.encode())
print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP

<img width="1920" height="1080" alt="Screenshot 2026-05-13 112724" src="https://github.com/user-attachments/assets/be0c5685-e0b3-41e9-baa3-fa0abdd7e22b" />

<img width="1920" height="1080" alt="Screenshot 2026-05-13 112834" src="https://github.com/user-attachments/assets/94c32598-aac9-4607-8556-596b076dac45" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
