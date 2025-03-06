# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
CLIENT:

import socket, time
client = socket.socket()
client.connect(("localhost", 9999))
frames = ["Frame1", "Frame2", "Frame3"]
for frame in frames:
    print(f"Sending: {frame}")
    client.send(frame.encode())
    time.sleep(1)
    print(f"Acknowledgment: {client.recv(1024).decode()}")
client.send("END".encode())
client.close()

SERVER:

import socket
server = socket.socket()
server.bind(("localhost", 9999))
server.listen(1)
conn, _ = server.accept()
while True:
    frame = conn.recv(1024).decode()
    if frame == "END":
        break
    print(f"Received: {frame}")
    conn.send("ACK".encode())
conn.close()
server.close()
```
## OUTPUT
**CLIENT:**

![Screenshot 2025-03-06 112227](https://github.com/user-attachments/assets/cf095b55-4de3-4a1a-bae1-45f84bfec5c4)

**SERVER:**

![Screenshot 2025-03-06 112348](https://github.com/user-attachments/assets/6b59769a-b6b2-46d3-81db-24ab82af59b2)


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
