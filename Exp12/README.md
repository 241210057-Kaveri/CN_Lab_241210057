
# Experiment 12: Study of Network Simulation and Analysis Tools

## Aim

To study different network simulation, emulation, monitoring, and analysis tools such as NS-3, OMNeT++, GNS3, pfSense, Wireshark, and Software Defined Networking.

## Introduction

Network simulation and analysis tools are used to design, test, monitor, and evaluate computer networks.

They allow network administrators, researchers, and students to study network behavior without always requiring physical networking equipment.

Different tools provide different functionalities, including packet analysis, topology simulation, network emulation, routing, and security management.

## 1. NS-3

NS-3 is a discrete-event network simulator used for research and educational purposes.

It allows users to simulate network protocols, communication between nodes, packet transmission, and network performance.

### Features

- Supports simulation of wired and wireless networks.
- Provides protocol models.
- Supports network performance analysis.
- Uses C++ and Python for simulation development.
- Supports packet tracing and statistical analysis.

### Basic Execution

After installing and configuring NS-3, an example simulation can be executed using:

```bash
./ns3 run scratch/first
```

## 2. OMNeT++

OMNeT++ is a modular simulation framework used to model communication networks and distributed systems.

It provides a graphical environment for developing and executing simulation models.

### Features

- Modular simulation architecture.
- Graphical simulation environment.
- Supports network modeling.
- Provides visualization of message exchanges.
- Can be extended using frameworks such as INET.

### Basic Procedure

1. Install OMNeT++.
2. Open the OMNeT++ IDE.
3. Import a sample simulation project.
4. Build the project.
5. Execute the simulation.
6. Observe communication between modules.

## 3. GNS3

GNS3 (Graphical Network Simulator 3) is a network emulation tool used to create and test virtual network topologies.

It allows users to connect virtual routers, switches, and other network devices.

### Features

- Creates virtual network topologies.
- Supports network device emulation.
- Provides graphical topology design.
- Allows configuration through device consoles.
- Useful for networking practice and certification preparation.

### Basic Procedure

1. Install GNS3.
2. Create a new project.
3. Add the required network devices.
4. Connect the devices using virtual links.
5. Start the devices.
6. Configure IP addresses and routing.
7. Test connectivity using ping.

## 4. pfSense

pfSense is an open-source firewall and router platform based on FreeBSD.

It provides network security and traffic management functionalities.

### Features

- Firewall configuration.
- Network Address Translation.
- DHCP services.
- VPN support.
- Routing and traffic management.
- Web-based configuration interface.

### Basic Procedure

1. Install pfSense in a virtual machine or supported hardware.
2. Configure WAN and LAN interfaces.
3. Assign IP addresses.
4. Access the web configuration interface from the LAN.
5. Configure firewall rules.
6. Explore DHCP, NAT, and routing settings.

## 5. Wireshark

Wireshark is a network protocol analyzer used to capture and inspect packets transmitted over a network.

It provides detailed information about network protocols and communication between devices.

### Features

- Captures live network traffic.
- Displays packet details.
- Supports multiple networking protocols.
- Provides display filters.
- Helps identify communication and troubleshooting issues.

### Basic Procedure

1. Install Wireshark.
2. Open the application.
3. Select the active network interface.
4. Start packet capture.
5. Generate network traffic using ping or another application.
6. Stop the capture.
7. Examine the captured packets.
8. Apply filters to display specific protocols.

### Useful Display Filters

```text
icmp
```

Displays ICMP packets.

```text
tcp
```

Displays TCP packets.

```text
udp
```

Displays UDP packets.

```text
dns
```

Displays DNS packets.

```text
arp
```

Displays ARP packets.

## 6. Software Defined Networking (SDN)

Software Defined Networking is a networking architecture that separates the control plane from the data plane.

The control plane determines how traffic should be forwarded, while the data plane performs packet forwarding.

### Components

1. Application Layer: Contains applications that communicate network requirements.
2. Control Layer: Contains the SDN controller responsible for network decisions.
3. Infrastructure Layer: Contains switches and other forwarding devices.

### Advantages

- Centralized network management.
- Programmable network configuration.
- Flexible traffic management.
- Easier network automation.
- Improved network monitoring.

## 7. Mininet

Mininet is a network emulator used to create virtual hosts, switches, controllers, and links on a single Linux system.

It is commonly used for experimenting with Software Defined Networking.

### Basic Execution

```bash
sudo mn --topo single,3
```

This creates a simple topology containing one switch and three hosts.

At the Mininet prompt, execute:

```text
nodes
net
pingall
exit
```

The `pingall` command tests connectivity between all hosts in the topology.

## Comparison of Tools

| Tool | Main Purpose |
|---|---|
| NS-3 | Network simulation |
| OMNeT++ | Modular network simulation |
| GNS3 | Network emulation |
| pfSense | Firewall and routing |
| Wireshark | Packet analysis |
| Mininet | SDN and network emulation |

## Result

Different network simulation, emulation, monitoring, and analysis tools were studied. Their features, applications, and basic working procedures were understood.

## Conclusion

Network simulation and analysis tools play an important role in designing, testing, monitoring, and troubleshooting computer networks. They provide practical environments for understanding networking concepts and evaluating network performance.
