
# Experiment 8: Examination and Implementation of Network Address Translation (NAT)

## Aim

To study Network Address Translation (NAT) and implement NAT configuration using Cisco Packet Tracer to enable communication between private and external networks.

## Introduction

Network Address Translation (NAT) is a networking technique used to translate IP addresses between different networks.

It is commonly used to allow devices having private IP addresses to communicate with external networks using public IP addresses.

NAT is generally implemented on routers or firewalls.

It helps conserve public IPv4 addresses and provides an additional layer of address separation between internal and external networks.

## Types of NAT

### 1. Static NAT

Static NAT establishes a permanent one-to-one mapping between a private IP address and a public IP address.

It is commonly used when an internal server needs to be accessible using a fixed public address.

### 2. Dynamic NAT

Dynamic NAT maps private IP addresses to public IP addresses selected from a predefined pool.

The mapping is created dynamically when communication is initiated.

### 3. Port Address Translation (PAT)

PAT is also known as NAT Overload.

It allows multiple devices with private IP addresses to share a single public IP address.

It distinguishes individual connections using port numbers.

## Requirements

- Cisco Packet Tracer
- One router
- One switch
- Two PCs
- One server
- Copper straight-through cables

## Network Topology

```text
PC0 ----\
         \
          Switch ---- Router ---- Server
         /
PC1 ----/

     Private LAN        External Network
```

The router acts as the NAT device between the private LAN and the external network.

## IP Addressing Scheme

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | NIC | 192.168.1.2 | 255.255.255.0 |
| PC1 | NIC | 192.168.1.3 | 255.255.255.0 |
| Router | FastEthernet0/0 | 192.168.1.1 | 255.255.255.0 |
| Router | FastEthernet0/1 | 200.1.1.1 | 255.255.255.0 |
| Server | NIC | 200.1.1.2 | 255.255.255.0 |

## Procedure

### Step 1: Create the Network Topology

1. Open Cisco Packet Tracer.
2. Add one router, one switch, two PCs, and one server.
3. Connect PC0 and PC1 to the switch.
4. Connect the switch to the router's LAN interface.
5. Connect the router's external interface to the server.

### Step 2: Configure IP Addresses

Configure the PCs with the following details:

PC0:

```text
IP Address:      192.168.1.2
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

PC1:

```text
IP Address:      192.168.1.3
Subnet Mask:     255.255.255.0
Default Gateway: 192.168.1.1
```

Configure the server:

```text
IP Address:  200.1.1.2
Subnet Mask: 255.255.255.0
```

### Step 3: Configure Router Interfaces

Open the router CLI.

```text
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
ip nat inside
no shutdown
exit

interface FastEthernet0/1
ip address 200.1.1.1 255.255.255.0
ip nat outside
no shutdown
exit
```

### Step 4: Configure NAT Overload

Enter the following commands:

```text
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface FastEthernet0/1 overload
```

The access list identifies the internal addresses eligible for translation.

The `overload` keyword enables Port Address Translation.

### Step 5: Verify NAT Configuration

Execute:

```text
show ip nat translations
```

This command displays the current NAT translation entries.

Also execute:

```text
show ip nat statistics
```

This displays NAT statistics.

### Step 6: Test Connectivity

From PC0:

```bash
ping 200.1.1.2
```

Repeat the test from PC1.

Generate traffic before checking the NAT translation table because translation entries are created when matching traffic passes through the router.

## Working Principle

1. A computer in the private network sends a packet to an external destination.
2. The packet reaches the router's inside interface.
3. The router checks its NAT configuration.
4. The private source IP address is translated into the router's outside IP address.
5. PAT uses port numbers to distinguish different connections.
6. The translated packet is forwarded to the external network.
7. Return traffic is translated back to the corresponding private device.

## Applications of NAT

- Sharing one public IPv4 address among multiple devices.
- Connecting private LANs to the Internet.
- Conserving public IPv4 addresses.
- Providing address separation between internal and external networks.
- Supporting access to internal services through static mappings.

## Result

Network Address Translation was studied and PAT was configured using Cisco Packet Tracer. Communication between the private network and the external server was tested, and NAT translations were examined.

## Conclusion

NAT allows devices using private IP addresses to communicate with external networks. PAT further improves address utilization by allowing multiple internal devices to share a single public IP address using port numbers.
