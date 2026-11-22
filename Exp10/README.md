
# Experiment 10: Implementation of Client-Server Applications Using TCP and UDP

## Aim

To study TCP and UDP transport protocols and implement basic client-server communication using Python socket programming.

## Introduction

The Transport Layer is responsible for process-to-process communication between applications running on different devices.

TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are two major transport layer protocols.

They use port numbers to identify applications and deliver data to the appropriate processes.

## 1. TCP (Transmission Control Protocol)

TCP is a connection-oriented transport protocol that provides reliable and ordered data transmission.

Before exchanging application data, TCP establishes a connection between the client and server using a three-way handshake.

### Characteristics

- Connection-oriented protocol.
- Reliable data delivery.
- Maintains the order of transmitted data.
- Uses acknowledgements and retransmission.
- Provides flow control and congestion control.
- Uses a byte-stream communication model.

### TCP Three-Way Handshake

1. SYN: The client sends a connection request.
2. SYN-ACK: The server acknowledges the request.
3. ACK: The client acknowledges the server.

After this process, the TCP connection is established.

## 2. UDP (User Datagram Protocol)

UDP is a connectionless transport protocol that sends data in the form of independent datagrams.

It does not establish a connection before transmitting data.

### Characteristics

- Connectionless protocol.
- Lower protocol overhead than TCP.
- Does not guarantee packet delivery.
- Does not guarantee packet ordering.
- Does not provide retransmission automatically.
- Supports datagram-based communication.

## Difference Between TCP and UDP

| TCP | UDP |
|---|---|
| Connection-oriented | Connectionless |
| Reliable delivery mechanisms | No delivery guarantee |
| Ordered byte stream | Independent datagrams |
| Higher protocol overhead | Lower protocol overhead |
| Uses acknowledgements | No acknowledgements at the UDP transport layer |
| Suitable for reliable data transfer | Suitable for applications prioritizing low latency |

## Requirements

- Python 3
- Computer or laptop
- Command Prompt or terminal
- Two terminal windows

## TCP Server Program

Create a file named `tcp_server.py`.

```python
import socket

HOST = "127.0.0.1"
PORT = 12345

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server.bind((HOST, PORT))
server.listen(1)

print("TCP Server is waiting for connection...")

conn, addr = server.accept()

print("Connected to:", addr)

data = conn.recv(1024)
print("Received:", data.decode())

conn.sendall(b"Hello from Server!")

conn.close()
server.close()
```

## TCP Client Program

Create a file named `tcp_client.py`.

```python
import socket

HOST = "127.0.0.1"
PORT = 12345

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect((HOST, PORT))

client.sendall(b"Hello from Client!")

data = client.recv(1024)

print("Received from server:", data.decode())

client.close()
```

## Execution of TCP Programs

1. Open two terminal windows.
2. Run the TCP server in the first terminal.

```bash
python tcp_server.py
```

3. Run the TCP client in the second terminal.

```bash
python tcp_client.py
```

4. Observe the messages exchanged between the client and server.

## UDP Server Program

Create a file named `udp_server.py`.

```python
import socket

HOST = "127.0.0.1"
PORT = 12345

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

server.bind((HOST, PORT))

print("UDP Server is waiting for data...")

data, addr = server.recvfrom(1024)

print("Received:", data.decode())

server.sendto(b"Hello from Server!", addr)

server.close()
```

## UDP Client Program

Create a file named `udp_client.py`.

```python
import socket

HOST = "127.0.0.1"
PORT = 12345

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

client.sendto(b"Hello from Client!", (HOST, PORT))

data, addr = client.recvfrom(1024)

print("Received from server:", data.decode())

client.close()
```

## Execution of UDP Programs

1. Open two terminal windows.
2. Start the UDP server.

```bash
python udp_server.py
```

3. Execute the UDP client in another terminal.

```bash
python udp_client.py
```

4. Observe the messages received by both programs.

## Important Socket Functions

| Function | Description |
|---|---|
| `socket()` | Creates a socket |
| `bind()` | Assigns an IP address and port to a socket |
| `listen()` | Waits for incoming TCP connections |
| `accept()` | Accepts a client connection |
| `connect()` | Establishes a TCP connection |
| `sendall()` | Sends data through a TCP socket |
| `recv()` | Receives TCP data |
| `sendto()` | Sends a UDP datagram |
| `recvfrom()` | Receives a UDP datagram |
| `close()` | Closes the socket |

## Result

TCP and UDP client-server applications were implemented using Python socket programming. The communication mechanisms and characteristics of both transport protocols were studied.

## Conclusion

TCP and UDP are important transport layer protocols used for process-to-process communication. TCP provides reliable and ordered transmission, whereas UDP provides connectionless communication with lower overhead.
