
# Experiment 7: Establishing Peer-to-Peer Network Connection Using a Switch and Router

## Aim

To establish a peer-to-peer network connection between two systems using a switch and router in a Local Area Network and verify communication between them.

## Introduction

A Peer-to-Peer (P2P) network is a network architecture in which computers communicate and share resources directly with one another without requiring a dedicated central server for every service.

In a peer-to-peer network, each computer can act as both a client and a server depending on the communication taking place.

A router can be used to connect different IP networks, while a switch provides connectivity between devices within the same LAN.

Cisco Packet Tracer is used to simulate the network topology and configure the required devices.

## Requirements

- Cisco Packet Tracer
- One router
- One switch
- Two PCs
- Copper straight-through cables

## Network Topology

```text
PC0
 |
 |
Switch
 |
 |
Router
 |
 |
PC1
```

PC0 is connected to the router through a switch, while PC1 is connected to the router through another interface.

The two PCs are configured in different IP subnets.

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|---|
| PC0 | NIC | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| Router | FastEthernet0/0 | 192.168.1.1 | 255.255.255.0 | — |
| Router | FastEthernet0/1 | 192.168.2.1 | 255.255.255.0 | — |
| PC1 | NIC | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |

## Procedure

### Step 1: Create the Topology

1. Open Cisco Packet Tracer.
2. Add one router to the workspace.
3. Add one switch.
4. Add two PCs.
5. Connect PC0 to the switch.
6. Connect the switch to the router's first Ethernet interface.
7. Connect PC1 directly to the router's second Ethernet interface.

### Step 2: Configure PC0 and PC1

For PC0:

```text
IP Address:      192.168.1.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

For PC1:

```text
IP Address:      192.168.2.10
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.2.1
```

Enter these values through:

Desktop → IP Configuration.

### Step 3: Configure the Router

Open the router CLI and execute:

```text
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface FastEthernet0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
exit

end
```

If the selected router uses GigabitEthernet interfaces, replace the interface names accordingly.

### Step 4: Verify Router Configuration

Execute:

```text
show ip interface brief
```

Check that both interfaces are active.

### Step 5: Test Communication

On PC0, open Command Prompt and execute:

```bash
ping 192.168.2.10
```

On PC1, execute:

```bash
ping 192.168.1.10
```

Successful replies indicate communication between the two systems.

## Working Principle

1. PC0 generates a packet intended for PC1.
2. Since PC1 belongs to a different subnet, PC0 forwards the packet to its default gateway.
3. The router receives the packet.
4. The router examines its routing table and identifies the outgoing interface.
5. The packet is forwarded to PC1.
6. PC1 processes the packet and sends a response through its default gateway.

## Applications

- Direct resource sharing.
- File sharing between computers.
- Communication between systems.
- Small office and home networks.
- Decentralized communication applications.

## Result

A peer-to-peer network connection was established between two computers using a switch and router in Cisco Packet Tracer. Communication was verified using the ping command.

## Conclusion

The experiment demonstrates peer-to-peer communication and the role of switches and routers in establishing connectivity. It also explains how IP addressing and default gateways enable communication between different networks.
