# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
CLIENT
```

import socket

# Create client socket
c = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to server
c.connect(('localhost', 12345))

print("Connected to server")

while True:
    # Send message to server
    msg = input("Client: ")
    c.send(msg.encode())

    if msg.lower() == "exit":
        break

    # Receive message from server
    reply = c.recv(1024).decode()
    print("Server:", reply)

    if reply.lower() == "exit":
        break

c.close()
```
SERVER
```

import socket

# Create server socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind IP address and port
s.bind(('localhost', 12345))

# Listen for client connection
s.listen(1)
print("Server waiting for connection...")

# Accept client connection
conn, addr = s.accept()
print("Client connected:", addr)

while True:
    # Receive message from client
    msg = conn.recv(1024).decode()
    print("Client:", msg)

    if msg.lower() == "exit":
        break

    # Send message to client
    reply = input("Server: ")
    conn.send(reply.encode())

    if reply.lower() == "exit":
        break

conn.close()
s.close()
```
## OUPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b6df9712-4d21-439e-8ded-edfb94eb2e82" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
