
# Experiment 5: Establishing a Local Area Network (LAN) Connection

## Aim

To establish a Local Area Network (LAN) connection between two or more computers using a network switch and verify communication between them.

## Introduction

A Local Area Network (LAN) is a computer network that connects devices within a limited geographical area, such as a laboratory, office, school, or home.

LANs allow connected devices to communicate and share resources such as files, printers, applications, and Internet connections.

Ethernet switches are commonly used to connect multiple computers within a LAN.

## Requirements

- Two or more computers
- Ethernet switch
- Ethernet cables (Cat5e/Cat6)
- Network Interface Cards (NICs)
- Windows or Linux operating system

## Network Topology

```text
       PC0
        |
        |
      Switch
      /    \
     /      \
   PC1      PC2
```

All computers are connected to a central switch, which forwards Ethernet frames to the appropriate destination.

## IP Addressing Scheme

For successful communication, all computers must be configured within the same IP subnet.

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC0 | 192.168.1.1 | 255.255.255.0 |
| PC1 | 192.168.1.2 | 255.255.255.0 |
| PC2 | 192.168.1.3 | 255.255.255.0 |

A default gateway is not required for communication within this isolated LAN.

## Procedure

1. Connect the Ethernet switch to its power supply.
2. Connect PC0 to the switch using an Ethernet cable.
3. Connect PC1 and PC2 to other switch ports.
4. Open Network Settings on each computer.
5. Navigate to the IPv4 configuration settings.
6. Assign a unique IP address to each computer.
7. Set the subnet mask to `255.255.255.0`.
8. Ensure that all computers belong to the same subnet.
9. Open Command Prompt on PC0.
10. Execute the following command:

```bash
ping 192.168.1.2
```

11. Check whether PC1 responds to the ping request.
12. Repeat the process from PC1 to PC0.

## Working Principle

When one computer sends data to another computer within the same subnet:

1. The source computer checks whether the destination belongs to its local network.
2. If the destination MAC address is unknown, ARP is used to discover it.
3. The Ethernet frame is transmitted to the switch.
4. The switch examines the destination MAC address.
5. The switch forwards the frame through the appropriate port.
6. The destination computer receives and processes the frame.

## Verification

The following commands can be used:

```bash
ipconfig
```

Displays the IP configuration.

```bash
ping 192.168.1.2
```

Tests connectivity between PC0 and PC1.

A successful ping generally displays reply messages containing the response time and packet information.

## Troubleshooting

- Check whether Ethernet cables are connected properly.
- Ensure that the switch is powered on.
- Verify that the network adapters are enabled.
- Check that each computer has a unique IP address.
- Ensure that all devices use the correct subnet mask.
- Check firewall settings if ICMP traffic is blocked.

## Applications

- File and printer sharing.
- Communication between computers.
- Resource sharing in laboratories and offices.
- Local multiplayer applications.
- Internal business networks.

## Result

A Local Area Network was established by connecting multiple computers through a network switch. IP addresses were configured, and connectivity was verified using the ping command.

## Conclusion

The experiment demonstrates how computers communicate within a Local Area Network. It also explains the role of Ethernet switches, IP addressing, and MAC address-based frame forwarding.
