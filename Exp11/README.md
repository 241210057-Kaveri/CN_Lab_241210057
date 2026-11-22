
# Experiment 11: Implementation of Socket Programming

## Aim

To study socket programming and implement client-server communication using TCP and UDP sockets in Python.

## Introduction

Socket programming is a method of establishing communication between two devices or applications over a network.

A socket acts as an endpoint for sending and receiving data.

Sockets allow applications to communicate using transport protocols such as TCP and UDP.

The client-server model is commonly used in socket programming. A client initiates communication, while a server waits for requests and responds to them.

## Client-Server Architecture

### Client

A client is an application or device that initiates communication with a server.

Its main functions include:
- Establishing communication with the server.
- Sending requests.
- Receiving responses.
- Processing the received information.

### Server

A server is an application or device that provides services to clients.

Its main functions include:
- Waiting for incoming connections or requests.
- Receiving client data.
- Processing requests.
- Sending responses.

## Types of Sockets

### 1. Stream Socket

Stream sockets use TCP for communication.

Characteristics:
- Connection-oriented.
- Reliable transmission.
- Ordered data delivery.
- Continuous byte-stream communication.

### 2. Datagram Socket

Datagram sockets use UDP for communication.

Characteristics:
- Connectionless communication.
- Independent data packets.
- Lower communication overhead.
- No guaranteed delivery or ordering.

## Important Python Socket Functions

| Function | Purpose |
|---|---|
| `socket()` | Creates a socket |
| `bind()` | Assigns an address and port |
| `listen()` | Waits for incoming TCP connections |
| `accept()` | Accepts a client connection |
| `connect()` | Connects to a server |
| `send()` | Sends data |
| `sendall()` | Sends all supplied bytes through TCP |
| `recv()` | Receives data |
| `sendto()` | Sends a UDP datagram |
| `recvfrom()` | Receives a UDP datagram |
| `close()` | Closes the socket |

## Requirements

- Python 3
- Computer or laptop
- Command Prompt or terminal
- Basic understanding of TCP and UDP

## TCP Server Program

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("127.0.0.1", 12345))

server.listen(1)

print("Server waiting for connection...")

conn, addr = server.accept()

print("Connected with:", addr)

data = conn.recv(1024)

print("Received from client:", data.decode())

conn.sendall(b"Hello from Server")

conn.close()
server.close()
```

## TCP Client Program

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("127.0.0.1", 12345))

client.sendall(b"Hello from Client")

data = client.recv(1024)

print("Received from server:", data.decode())

client.close()
```

## UDP Server Program

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

server.bind(("127.0.0.1", 12345))

print("UDP Server is ready...")

data, addr = server.recvfrom(1024)

print("Received:", data.decode())

server.sendto(b"Hello from Server", addr)

server.close()
```

## UDP Client Program

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

client.sendto(b"Hello from Client", ("127.0.0.1", 12345))

data, addr = client.recvfrom(1024)

print("Received from server:", data.decode())

client.close()
```

## Procedure

1. Install Python 3 on the computer.
2. Create separate Python files for the server and client programs.
3. Execute the server program first.
4. Execute the client program in another terminal.
5. Observe the messages received by the server.
6. Observe the response received by the client.
7. Repeat the process using UDP.
8. Compare the working of TCP and UDP sockets.

## Working Principle

### TCP Communication

1. The server creates a TCP socket.
2. The server binds the socket to an IP address and port.
3. The server listens for incoming connections.
4. The client creates a socket and connects to the server.
5. The server accepts the connection.
6. Both sides exchange data.
7. The connection is closed after communication.

### UDP Communication

1. The server creates a UDP socket.
2. The server binds the socket to a port.
3. The client sends a datagram to the server.
4. The server receives the datagram.
5. The server sends a response to the client's address.
6. Both sockets are closed.

## Important Notes

The programs use `127.0.0.1`, which is the loopback address. This allows both programs to communicate on the same computer.

For communication between two different computers, use the server computer's LAN IP address and configure the firewall to allow the selected port.

## Result

TCP and UDP socket programs were implemented successfully to demonstrate communication between a client and server.

## Conclusion

Socket programming provides a practical method for implementing network applications. It allows developers to establish communication using transport layer protocols such as TCP and UDP.
