
# Experiment 4: Study and Configuration of Network IP Addressing

## Aim

To study IP addressing, understand IPv4 and IPv6 addressing schemes, and configure IP addresses on network devices.

## Introduction

An Internet Protocol (IP) address is a logical address assigned to a device connected to a network. It is used to identify devices and enable communication between them.

Every device communicating over an IP network requires an appropriate IP configuration.

IP addresses are primarily classified into IPv4 and IPv6.

## 1. IPv4 Addressing

IPv4 is a 32-bit addressing scheme represented using four decimal numbers separated by dots.

Example:

```text
192.168.1.10
```

Each section is called an octet and contains 8 bits.

The range of each octet is 0 to 255.

## 2. IPv6 Addressing

IPv6 is a 128-bit addressing scheme developed to overcome the limitations of IPv4 address availability.

Example:

```text
2001:db8:abcd:0012::1
```

IPv6 uses hexadecimal notation and provides a significantly larger address space.

## 3. Types of IP Addresses

### Static IP Address

A static IP address is manually configured and generally remains unchanged until an administrator modifies it.

It is commonly used for:
- Servers.
- Network printers.
- Routers.
- Network infrastructure devices.

### Dynamic IP Address

A dynamic IP address is automatically assigned to a device, generally using DHCP.

It can change when the device's lease expires or is renewed with a different address.

## 4. IPv4 Address Classes

Traditionally, IPv4 addresses were divided into five classes.

| Class | First Octet Range | Default Subnet Mask |
|---|---|---|
| A | 1–126 | 255.0.0.0 |
| B | 128–191 | 255.255.0.0 |
| C | 192–223 | 255.255.255.0 |
| D | 224–239 | Not applicable |
| E | 240–255 | Not applicable |

Class D is used for multicast addressing, while Class E is reserved for experimental purposes.

Modern networks primarily use Classless Inter-Domain Routing (CIDR).

## 5. Subnet Mask

A subnet mask identifies the network portion and host portion of an IPv4 address.

Example:

```text
IP Address:     192.168.1.10
Subnet Mask:    255.255.255.0
Prefix Length:  /24
```

For a `/24` network:

- Network address: 192.168.1.0
- First usable address: 192.168.1.1
- Last usable address: 192.168.1.254
- Broadcast address: 192.168.1.255

The number of usable host addresses in a conventional IPv4 subnet is:

\[
2^h - 2
\]

where `h` is the number of host bits.

For a `/24` subnet:

\[
2^8 - 2 = 254
\]

## 6. Private IP Address Ranges

Private IPv4 addresses are used within local networks and are not directly routed over the public Internet.

| Range | Address Block |
|---|---|
| Class A private range | 10.0.0.0 – 10.255.255.255 |
| Class B private range | 172.16.0.0 – 172.31.255.255 |
| Class C private range | 192.168.0.0 – 192.168.255.255 |

## Requirements

- Computer or laptop
- Windows or Linux operating system
- Network interface card
- Ethernet connection
- Administrative access to network settings

## Procedure for Windows

1. Open Control Panel.
2. Navigate to Network and Sharing Center.
3. Select Change Adapter Settings.
4. Right-click the active network connection.
5. Select Properties.
6. Select Internet Protocol Version 4 (TCP/IPv4).
7. Click Properties.
8. Select Use the Following IP Address.
9. Enter the required IP address, subnet mask, and default gateway.
10. Enter DNS server information if required.
11. Save the configuration.
12. Open Command Prompt and execute:

```bash
ipconfig
```

13. Verify the assigned IP configuration.

## Example Configuration

| Parameter | Value |
|---|---|
| IP Address | 192.168.1.10 |
| Subnet Mask | 255.255.255.0 |
| Default Gateway | 192.168.1.1 |
| DNS Server | 8.8.8.8 |

The example gateway and DNS server should be changed according to the actual network configuration.

## Verification

Use the following commands:

```bash
ipconfig
ping 192.168.1.1
```

The first command displays the IP configuration, while the second tests connectivity with the default gateway.

## Applications

- Identifying devices in a network.
- Communication between computers.
- Routing packets between networks.
- Network administration.
- Subnetting and network management.

## Result

IPv4 and IPv6 addressing concepts were studied, and the procedure for configuring a static IP address was performed.

## Conclusion

IP addressing is an essential part of computer networking. It provides logical identification to network devices and enables communication within local and interconnected networks.
