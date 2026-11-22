
# Experiment 2: Study of Basic Network Commands

## Aim

To study and execute various networking commands used for network configuration, connectivity testing, troubleshooting, and monitoring.

## Introduction

Network commands are command-line utilities used to obtain information about network configurations and diagnose communication problems.

These commands help administrators identify IP addresses, test connectivity, examine routing information, resolve domain names, and monitor active network connections.

## Important Network Commands

### 1. ipconfig

The `ipconfig` command displays the IP configuration of a computer in Windows.

```bash
ipconfig
```

To display detailed network configuration:

```bash
ipconfig /all
```

It displays information such as:
- IPv4 and IPv6 addresses.
- Subnet mask.
- Default gateway.
- DNS servers.
- Physical MAC address.

### 2. ping

The `ping` command checks whether a destination device is reachable over an IP network.

```bash
ping 192.168.1.1
```

It sends ICMP Echo Request messages and waits for Echo Replies.

It is useful for checking network connectivity and estimating round-trip time.

### 3. tracert

The `tracert` command in Windows identifies the route taken by packets to reach a destination.

```bash
tracert google.com
```

It displays intermediate routers, also known as hops, between the source and destination.

The Linux equivalent is:

```bash
traceroute google.com
```

### 4. nslookup

The `nslookup` command is used to query DNS servers and obtain information about domain names.

```bash
nslookup google.com
```

It helps determine whether a domain name is being resolved into an IP address correctly.

### 5. netstat

The `netstat` command displays active network connections, listening ports, and network statistics.

```bash
netstat -ano
```

It can be used to examine TCP connections and identify applications associated with network activity.

### 6. arp

The Address Resolution Protocol (ARP) maps IPv4 addresses to MAC addresses within a local network.

```bash
arp -a
```

This command displays the ARP cache maintained by the system.

### 7. hostname

The `hostname` command displays the name assigned to the computer.

```bash
hostname
```

### 8. route

The `route` command displays or modifies the system routing table.

```bash
route print
```

The routing table contains information used by the operating system to determine where packets should be forwarded.

## Procedure

1. Open Command Prompt in Windows.
2. Execute the `ipconfig` command to display the network configuration.
3. Use `ipconfig /all` to view detailed information.
4. Execute the `ping` command to test connectivity with another device.
5. Use `tracert` to examine the route to a destination.
6. Execute `nslookup` to obtain DNS information.
7. Use `netstat -ano` to display active connections.
8. Execute `arp -a` to examine the ARP cache.
9. Use `route print` to display the routing table.
10. Observe and analyse the outputs.

## Applications

- Network troubleshooting.
- Checking IP configuration.
- Testing connectivity between devices.
- DNS troubleshooting.
- Monitoring active connections.
- Examining routing information.

## Result

Various networking commands were executed and their outputs were studied to understand network configuration, connectivity testing, DNS resolution, and troubleshooting.

## Conclusion

Network commands provide essential information about the configuration and operation of a computer network. They are useful tools for identifying connectivity issues and monitoring network communication.
