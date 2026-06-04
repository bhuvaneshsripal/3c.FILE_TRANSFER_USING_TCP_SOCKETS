# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello Server".encode())
file = open("received_file.txt", "wb")
print("Receiving file...")
while True:
    data = s.recv(1024)
    if not data:
        break
    file.write(data)
print("File received successfully")
file.close()
s.close()
```
SERVER:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.bind((host, port))
s.listen(1)
print("Server listening...")
c, addr = s.accept()
print("Connected with", addr)
msg = c.recv(1024).decode()
print("Client says:", msg)
filename = "C:/Users/acer/Desktop/New folder (2)/sample.txt"
file = open(filename, "rb")
data = file.read(1024)
while data:
    c.send(data)
    data = file.read(1024)
print("File sent successfully")
file.close()
c.close()
s.close()
```

## OUPUT
CLIENT:
<img width="1919" height="1021" alt="Screenshot 2026-05-28 214025" src="https://github.com/user-attachments/assets/d3b2f44e-cf0f-441d-8075-d4e4b6522b8a" />

SERVER:
<img width="1919" height="1011" alt="Screenshot 2026-05-28 213956" src="https://github.com/user-attachments/assets/32d47fb5-82c9-45d4-a89b-380337ffd702" />

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
