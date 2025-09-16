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
Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter Logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```
Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"172.20.10.2":"68:34:21:81:82:C9"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## OUPUT - ARP

<img width="816" height="882" alt="489461147-3c4f284b-a03c-4518-9f67-a0a423cd6e05" src="https://github.com/user-attachments/assets/ba5f1bea-5cf8-404f-bb6c-e1e9089ced01" />

## PROGRAM - RARP
Server:
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
Client:
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"68:34:21:81:82:C9":"172.20.10.2"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
## OUPUT -RARP

<img width="871" height="880" alt="489461381-174a8609-1bdf-4b47-9642-c5bd4f845889" src="https://github.com/user-attachments/assets/11f0d51e-263b-41c3-b0a6-bb5ae8196432" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
