# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.

## ALGORITHM:
### Client:
Start the program
Using socket connection is established between client and server.
Get the IP address to be converted into MAC address.
Send this IP address to server.
Server returns the MAC address to client.
### Server:
Start the program
Accept the socket which is created by the client.
Server maintains the table in which IP and corresponding MAC addresses are stored.
Read the IP address which is send by the client.
Map the IP address with its MAC address and return the MAC address to client.
## PROGRAM:
### CLIENT:
```
import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8000)) 
s.listen(5)
c,addr=s.accept()
print("Client Address : ",addr) 
now = datetime.now() 
c.send(now.strftime("%d/%m/%Y %H:%M:%S").encode())
ack=c.recv(1024).decode() 
if ack:
    print(ack)
c.close()
```
### SERVER:
```
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
print(s.getsockname()) 
print(s.recv(1024).decode()) 
s.send("acknowledgement recived from the server".encode())
```
### OUTPUT :
CLIENT AND SERVER :
![image](https://github.com/user-attachments/assets/e36064ad-854b-4843-8fcd-0711dcbb423f)


## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully executed.

