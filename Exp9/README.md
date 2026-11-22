
# Experiment 9: Simulation of Routing Protocols

## Aim

To study and simulate different routing techniques, including Static Routing, RIP, EIGRP, and OSPF, using Cisco Packet Tracer.

## Introduction

Routing is the process of selecting a suitable path for forwarding data packets from a source network to a destination network.

Routers maintain routing tables that contain information about available networks and the paths used to reach them.

Routing can be classified into:

1. Static Routing
2. Dynamic Routing

Static routing requires manual configuration of routes, whereas dynamic routing protocols allow routers to exchange routing information automatically.

## 1. Static Routing

Static routing is a routing method in which network routes are manually configured by the network administrator.

The administrator specifies the destination network, subnet mask, and next-hop address or outgoing interface.

### Advantages

- Simple configuration in small networks.
- No routing update traffic.
- Provides predictable routing behavior.
- Gives administrators direct control over routes.

### Disadvantages

- Requires manual configuration.
- Difficult to maintain in large networks.
- Does not automatically adapt to topology changes.

### Configuration Example

```text
ip route 192.168.2.0 255.255.255.0 10.0.0.2
```

This command adds a route to network `192.168.2.0/24` through next-hop address `10.0.0.2`.

## 2. RIP (Routing Information Protocol)

RIP is a distance-vector routing protocol that uses hop count as its routing metric.

Each router shares routing information with its neighboring routers at regular intervals.

The maximum usable hop count in RIP is 15. A distance of 16 represents an unreachable destination.

### Characteristics

- Uses hop count as its metric.
- Maximum usable hop count is 15.
- Uses periodic routing updates.
- Suitable for relatively small networks.
- RIP version 2 supports classless routing and authentication.

### Configuration Example

```text
router rip
version 2
no auto-summary
network 192.168.1.0
network 10.0.0.0
```

The network statements must correspond to the networks connected to the router.

## 3. EIGRP (Enhanced Interior Gateway Routing Protocol)

EIGRP is an advanced distance-vector routing protocol associated with Cisco networking equipment.

It uses the Diffusing Update Algorithm (DUAL) to calculate loop-free paths and support rapid convergence.

Its metric can consider bandwidth and delay, with other factors available through configuration.

### Characteristics

- Uses DUAL for route calculation.
- Supports rapid convergence.
- Uses bandwidth and delay in its default metric.
- Supports unequal-cost load balancing.
- Sends partial and triggered updates rather than periodic full-table updates.

### Configuration Example

```text
router eigrp 1
no auto-summary
network 192.168.1.0 0.0.0.255
network 10.0.0.0 0.0.0.255
```

The autonomous system number must match on routers participating in the same EIGRP routing domain.

## 4. OSPF (Open Shortest Path First)

OSPF is a link-state routing protocol used to determine the shortest path between networks.

It uses Dijkstra's Shortest Path First (SPF) algorithm to calculate the best routes.

Routers exchange link-state information and maintain a link-state database representing the network topology.

### Characteristics

- Uses link-state routing.
- Uses cost as its routing metric.
- Supports hierarchical network design using areas.
- Provides fast convergence.
- Suitable for medium and large networks.

### Configuration Example

```text
router ospf 1
network 192.168.1.0 0.0.0.255 area 0
network 10.0.0.0 0.0.0.255 area 0
```

The wildcard masks specify the addresses covered by each network statement.

## Comparison of Routing Protocols

| Feature | Static | RIP | EIGRP | OSPF |
|---|---|---|---|---|
| Routing type | Manual | Distance Vector | Advanced Distance Vector | Link State |
| Metric | Configured route | Hop Count | Bandwidth and Delay by default | Cost |
| Route updates | None | Periodic | Triggered/partial | Link-state advertisements |
| Convergence | Manual adjustment | Relatively slow | Fast | Fast |
| Scalability | Small networks | Small networks | Medium/large networks | Medium/large networks |

## Requirements

- Cisco Packet Tracer
- Three routers
- Three switches
- Three PCs
- Ethernet cables
- Serial or Ethernet connections between routers, depending on the selected topology

## Network Topology

```text
PC0 ---- R0 -------- R1 -------- R2 ---- PC2
                    |
                    |
                   PC1
```

Each router connects to a local network. The routers are interconnected to allow communication between different LANs.

## Example IP Addressing Scheme

| Network | Address |
|---|---|
| LAN 1 | 192.168.1.0/24 |
| LAN 2 | 192.168.2.0/24 |
| LAN 3 | 192.168.3.0/24 |
| R0-R1 Link | 10.0.0.0/24 |
| R1-R2 Link | 20.0.0.0/24 |

Each router interface must be assigned an appropriate IP address within its connected network.

## General Procedure

1. Open Cisco Packet Tracer.
2. Place three routers in the workspace.
3. Add switches and PCs to create separate LANs.
4. Connect the routers using appropriate Ethernet or serial links.
5. Assign IP addresses to all router interfaces.
6. Configure the PCs with their IP addresses and default gateways.
7. Enable router interfaces using `no shutdown`.
8. Configure one routing method at a time.
9. Verify routing tables.
10. Test communication between PCs belonging to different LANs.

## Verification Commands

```text
show ip route
```

Displays the routing table.

```text
show ip protocols
```

Displays information about active routing protocols.

```text
show ip interface brief
```

Displays interface addresses and status.

Use `ping` to test communication between devices in different networks.

## Result

Static routing, RIP, EIGRP, and OSPF were studied and configured in a simulated network environment. Routing tables and connectivity tests were used to examine packet forwarding.

## Conclusion

Routing protocols allow routers to determine suitable paths for packet transmission. Static routing provides manual control, while dynamic protocols such as RIP, EIGRP, and OSPF allow routers to exchange routing information and adapt to network changes.
