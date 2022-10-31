# test-commit

REQUEST DATA: 

-Create Socket object using imported Socket package
-Connect to shared HOST and PORT of Server 
-Use 'sendall' as type b (byte) to Server sending parameters of your request


import socket

HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:  (socket object as s)
    s.connect((HOST, PORT))                                 (connects to shared host & port of client)
    s.sendall(b"A message from CS361")                      (use sendall of type b to send data request to client)
    data = s.recv(1024)

print(f"Received {data!r}")




RECEIVE DATA: 

-data request parameters received then sent back using sendall
-client side line 18 (data = s.recv(1024)) receives data back from server where 1024 is max size of object in bytes


import socket

HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:         
            data = conn.recv(1024)                    (receives clients data object request and included params)
            if not data:
                break
            conn.sendall(data)                         (sends back to client data object)
            
            
            
            
  
          
            sockets-tcp-flow:    https://user-images.githubusercontent.com/114425878/199107926-3c72f7d7-93c0-4ac0-935f-593c8db69ac5.gif

            source:    https://commons.wikimedia.org/wiki/File:InternetSocketBasicDiagram_zhtw.png
            
            
