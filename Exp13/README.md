
# Experiment 13: Implementation of DHCP Server Using Cisco Packet Tracer

## Aim

To configure and implement a Dynamic Host Configuration Protocol (DHCP) server using Cisco Packet Tracer and assign IP addresses automatically to client computers.

## Introduction

Dynamic Host Configuration Protocol (DHCP) is a network management protocol used to automatically assign IP addresses and other network configuration parameters to devices connected to a network.

Without DHCP, network administrators would need to manually configure IP addresses on every device.

DHCP simplifies network administration and reduces the chances of IP address conflicts.

It can provide the following configuration information:

- IP address.
- Subnet mask.
- Default gateway.
- DNS server address.
- IP address lease duration.

DHCP uses UDP port 67 on the server and UDP port 68 on the client.

## Working of DHCP

DHCP follows a four-step process known as DORA.

### 1. Discover

The client broadcasts a DHCP Discover message to locate available DHCP servers.

### 2. Offer

The DHCP server responds with a DHCP Offer message containing an available IP address and other configuration information.

### 3. Request

The client sends a DHCP Request message indicating that it wants to use the offered IP address.

### 4. Acknowledgement

The server sends a DHCP ACK message confirming the IP address assignment.

## DHCP DORA Process

| Step | Message | Description |
|---|---|---|
| 1 | Discover | Client searches for a DHCP server |
| 2 | Offer | Server offers an available IP address |
| 3 | Request | Client requests the offered address |
| 4 | Acknowledgement | Server confirms the address assignment |

## Requirements

- Cisco Packet Tracer
- One server
- One switch
- Three PCs
- Copper straight-through cables

## Network Topology

```text
       PC0
        |
        |
       PC1
        |
      Switch -------- Server
        |
        |
       PC2
```

All client PCs and the DHCP server are connected to the same switch.

## IP Addressing Scheme

| Device | IP Address | Configuration |
|---|---|---|
| DHCP Server | 192.168.1.1 | Static |
| PC0 | Automatically assigned | DHCP |
| PC1 | Automatically assigned | DHCP |
| PC2 | Automatically assigned | DHCP |

The DHCP server uses a static IP address so that clients can consistently locate the service.

## Procedure

### Step 1: Create the Network Topology

1. Open Cisco Packet Tracer.
2. Add one server to the workspace.
3. Add one switch.
4. Add three PCs.
5. Connect all PCs to the switch.
6. Connect the server to the switch.
7. Wait for the link indicators to become active.

### Step 2: Configure the Server IP Address

1. Select the server.
2. Open the Desktop tab.
3. Select IP Configuration.
4. Configure the server with:

```text
IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0
```

The server should have a static IP address.

### Step 3: Configure DHCP Service

1. Select the server.
2. Open the Services tab.
3. Select DHCP.
4. Turn the DHCP service ON.
5. Configure the DHCP pool.

Example configuration:

| Parameter | Value |
|---|---|
| Pool Name | LAN_POOL |
| Default Gateway | 0.0.0.0 (if no router is present) |
| DNS Server | 8.8.8.8 |
| Start IP Address | 192.168.1.10 |
| Subnet Mask | 255.255.255.0 |
| Maximum Users | 50 |

6. Save or add the pool.

If a router is present, configure the default gateway field with the router's LAN interface address.

### Step 4: Configure Client PCs

1. Select PC0.
2. Open the Desktop tab.
3. Select IP Configuration.
4. Select DHCP.
5. Wait for the IP address assignment.
6. Repeat the same process for PC1 and PC2.

Each PC should receive a unique IP address from the configured DHCP pool.

### Step 5: Verify DHCP Configuration

Open Command Prompt on each PC.

Execute:

```bash
ipconfig
```

Check whether the IP address, subnet mask, and other network configuration parameters have been assigned automatically.

### Step 6: Test Connectivity

From PC0, execute:

```bash
ping 192.168.1.1
```

This tests communication with the DHCP server.

Repeat the test from other client computers.

## Alternative: Configuring DHCP on a Cisco Router

A Cisco router can also provide DHCP services.

Example configuration:

```text
enable
configure terminal

interface FastEthernet0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

ip dhcp excluded-address 192.168.1.1 192.168.1.9

ip dhcp pool LAN_POOL
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
exit

end
```

The excluded-address command prevents the router from assigning reserved addresses to clients.

## DHCP Verification Commands

For router-based DHCP configuration:

```text
show ip dhcp binding
```

Displays the IP addresses currently leased to clients.

```text
show ip dhcp pool
```

Displays DHCP pool information.

## Advantages of DHCP

- Automatically assigns IP addresses.
- Reduces manual configuration.
- Prevents many accidental IP address conflicts.
- Simplifies network administration.
- Supports efficient address management.
- Makes it easier to connect new devices to a network.

## Result

A DHCP server was configured using Cisco Packet Tracer. Client computers were configured to obtain IP addresses automatically, and the assigned network configuration was verified.

## Conclusion

DHCP simplifies IP address management by automatically assigning network configuration parameters to connected devices. It is widely used in modern networks to reduce administrative effort and ensure efficient address allocation.
