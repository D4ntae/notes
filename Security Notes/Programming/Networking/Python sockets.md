
Simple socket example
```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
```

```
AF_INET - means use IPv4
SOCK_STREAM - use TCP
```

server.py
```python
import socket

HOST = "127.0.0.1"
PORT = 5002

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# Start the server listener by binding to the port
server.bind((HOST, PORT))

# Limit awaiting connections to 5
server.listen(5)

while True:
	# Server accepts the connection and returns a socket
	(communication_client, address) = server.accept()
	print(f"Connected to {address}")
```

client.py
```python
import socket

HOST = "127.0.0.1"
PORT = 5002

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# Client only needs to connect
client.connect((HOST, PORT))
```


#python #sockets #servers #networking 