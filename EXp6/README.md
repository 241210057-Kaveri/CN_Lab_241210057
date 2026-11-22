
# Experiment 6: Router Configuration Using Cisco Packet Tracer

## Aim

To configure a router using Cisco Packet Tracer and establish communication between two different networks.

## Introduction

A router is a networking device that connects multiple networks and forwards data packets between them using IP addresses.

Routers operate at the Network Layer (Layer 3) of the OSI model. They maintain routing tables that contain information about available networks and the paths used to reach them.

Cisco Packet Tracer is a network simulation tool that allows users to create virtual network topologies and configure networking devices.

## Requirements

- Cisco Packet Tracer
- One router
- Two switches
- Four PCs
- Copper straight-through cables

## Network Topology

```text
PC0 ----\
         \
          Switch0 ---- Router ---- Switch1 ---- PC2
         /                                  \
PC1 ----/                                    PC3

      Network 1                         Network 2
```

The router connects two separate IP networks.

## IP Addressing Scheme

| Device | IP Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| PC0 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 |
| PC1 | 192.168.1.11 | 255.255.255.0 | 192.168.1.1 |
| Router Interface 1 | 192.168.1.1 | 255.255.255.0 | — |
| Router Interface 2 | 192.168.2.1 | 255.255.255.0 | — |
| PC2 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 |
| PC3 | 192.168.2.11 | 255.255.255.0 | 192.168.2.1 |

## Procedure

### Step 1: Create the Network Topology

1. Open Cisco Packet Tracer.
2. Add one router to the workspace.
3. Add two switches.
4. Add four PCs.
5. Connect PC0 and PC1 to Switch0.
6. Connect PC2 and PC3 to Switch1.
7. Connect Switch0 to the first router interface.
8. Connect Switch1 to the second router interface.

Use copper straight-through cables for these connections.

### Step 2: Configure the PCs

1. Select PC0.
2. Open the Desktop tab.
3. Select IP Configuration.
4. Enter the IP address, subnet mask, and default gateway.
5. Repeat the same process for the remaining PCs using the addressing table.

### Step 3: Configure the Router

Open the router CLI and enter the following commands.

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

**Note:** Interface names may differ depending on the router model. Use the actual interface names displayed by the device.

## Explanation of Commands

| Command | Function |
|---|---|
| `enable` | Enters privileged EXEC mode |
| `configure terminal` | Enters global configuration mode |
| `interface FastEthernet0/0` | Selects the router interface |
| `ip address` | Assigns an IP address and subnet mask |
| `no shutdown` | Enables the interface |
| `exit` | Exits the current configuration mode |
| `end` | Returns to privileged EXEC mode |

## Step 4: Verify Router Interfaces

Execute:

```text
show ip interface brief
```

This command displays the status and IP addresses of router interfaces.

Both interfaces should ideally show:

```text
Status: up
Protocol: up
```

## Step 5: Test Connectivity

From PC0, open Command Prompt and execute:

```bash
ping 192.168.2.10
```

This tests communication between PC0 and PC2.

Also test the reverse connection:

```bash
ping 192.168.1.10
```

## Working Principle

1. The source PC checks whether the destination IP belongs to the local network.
2. Since the destination belongs to another network, the packet is sent to the default gateway.
3. The router receives the packet through its incoming interface.
4. It examines the destination IP address and routing table.
5. It forwards the packet through the appropriate outgoing interface.
6. The destination PC receives the packet.

## Result

A router was configured using Cisco Packet Tracer. Two different networks were connected, and communication between the PCs was tested successfully using the ping command.

## Conclusion

The experiment demonstrates the working and configuration of a router. It shows how routers enable communication between different IP networks by forwarding packets based on destination IP addresses.
