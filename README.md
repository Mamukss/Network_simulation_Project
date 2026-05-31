# Cisco Packet Tracer Network Simulation Project

## Overview

This repository contains a Cisco Packet Tracer network simulation project. The project is designed to demonstrate the planning, configuration, and testing of a computer network using Cisco networking devices in a simulated environment.

The main project file is:

```text
Project.pkt
```

This file can be opened using Cisco Packet Tracer.

## Project Objectives

The objectives of this project are:

- To design a computer network topology using Cisco Packet Tracer.
- To configure network devices such as routers, switches, and end devices.
- To apply IP addressing and basic network configuration.
- To test network connectivity between devices.
- To document the network design, configuration, and testing results.

## Tools Used

- Cisco Packet Tracer
- Cisco Router and Switch Devices
- End Devices such as PCs, laptops, or servers
- Command Line Interface \(CLI\) for device configuration

## Repository Structure

```text
.
├── Project.pkt
├── README.md
└── docs/
    ├── topology.png
    ├── ip-addressing-table.md
    └── testing-results.md
```


## Network Topology

The network topology is created inside Cisco Packet Tracer. The topology may include:

- Router devices
- Switch devices
- PC or laptop end devices
- Server devices
- Wired connections using Ethernet cables


![Network](docs/Topology.png)


## IP Addressing Table


| VLAN ID | VLAN Name | Network Address | Subnet Mask | Default Gateway | DHCP Range | DNS Server | Description |
|---|---|---|---|---|---|---|---|
| 10 | MANAGEMENT | 10.10.10.0/24 | 255.255.255.0 | 10.10.10.1 | 10.10.10.21 - 10.10.10.254 | 10.10.70.10 | Management VLAN |
| 20 | FINANCE | 10.10.20.0/24 | 255.255.255.0 | 10.10.20.1 | 10.10.20.21 - 10.10.20.254 | 10.10.70.10 | Finance department |
| 30 | HR | 10.10.30.0/24 | 255.255.255.0 | 10.10.30.1 | 10.10.30.21 - 10.10.30.254 | 10.10.70.10 | Human Resources department |
| 40 | IT | 10.10.40.0/24 | 255.255.255.0 | 10.10.40.1 | 10.10.40.21 - 10.10.40.254 | 10.10.70.10 | IT department |
| 50 | STAFF | 10.10.50.0/24 | 255.255.255.0 | 10.10.50.1 | 10.10.50.21 - 10.10.50.254 | 10.10.70.10 | Staff users |
| 60 | GUEST | 10.10.60.0/24 | 255.255.255.0 | 10.10.60.1 | 10.10.60.21 - 10.10.60.254 | 10.10.70.10 | Guest users |
| 70 | SERVER | 10.10.70.0/24 | 255.255.255.0 | 10.10.70.1 | 10.10.70.21 - 10.10.70.254 | 10.10.70.10 | Server VLAN |
| 99 | NET-MGMT | 10.10.99.0/24 | 255.255.255.0 | 10.10.99.1 | Not configured / not shown | - | Network management VLAN |
| 999 | BLACKHOLE-NATIVE | - | - | - | - | - | Native VLAN for trunk security |



### Router Configuration
for router configuration you can see on the file 

```text
config/router1_config
```
### Switch Configuration

Example configuration:

for router configuration you can see on the file 

```text
config/switch1_config
config/Switch2_config
```

### PC Configuration

Each PC should be configured with:

- IP address
- Subnet mask
- Default gateway
- DNS server, if required

all automaticly implement using dhcp except for the server ip address

## Features Implemented

Update this section based on your actual project configuration.

- Basic LAN configuration
- Router interface configuration
- Switch management configuration
- IP addressing
- End-device connectivity
- Ping testing

## Security Policy and ACL Testing

Access Control Lists (ACLs) were implemented to restrict communication between VLANs. Some VLANs are intentionally blocked from accessing other internal VLANs to improve network security.

For example, the Guest VLAN is not allowed to access internal department VLANs such as Management, Finance, HR, IT, Staff, and Network Management. However, it is still allowed to access the internal web server at 10.10.70.10.

The failed ping results shown in the testing section are expected because the traffic is blocked by ACL rules, not because of a network misconfiguration.
## Testing and Verification

Testing should be performed to ensure the network works correctly.

### Connectivity Test

Use the `ping` command from one device to another.

Example:

```bash
ping 10.10.10.21
ping 10.10.20.22
```

### Verification Commands

Useful Cisco CLI commands:

```bash
show ip interface brief
show running-config
show vlan brief
show ip route
show mac address-table
```

## Testing Results

| Test | Source | Destination | Result | Explanation |
|---|---|---|---|---|
| Ping Guest to Management | VLAN 60 | 10.10.10.21 | Failed | Blocked by ACL |
| Ping Guest to Finance | VLAN 60 | 10.10.20.21 | Failed | Blocked by ACL |
| Ping Guest to HR | VLAN 60 | 10.10.30.21 | Failed | Blocked by ACL |
| Ping Staff to Finance | VLAN 50 | 10.10.20.21 | Failed | Blocked by ACL |
| Ping Staff to HR | VLAN 50 | 10.10.30.22 | Failed | Blocked by ACL |
| Web Access to Server | VLAN 50 / VLAN 60 | 10.10.70.10 | Success | HTTP access is allowed |

## How to Open the Project

1. Install Cisco Packet Tracer.
2. Clone or download this repository.
3. Open Cisco Packet Tracer.
4. Open the file:

```text
Project.pkt
```

5. Review the topology and device configurations.
6. Run connectivity testing using the simulation or realtime mode.

## Troubleshooting Notes

If the network does not work correctly, check the following:

- Make sure all interfaces are enabled using `no shutdown`.
- Check that every device has the correct IP address and subnet mask.
- Check the default gateway configuration on end devices.
- Check cable connections between devices.
- Use `show ip interface brief` to verify interface status.
- Use `ping` to test connectivity step by step.

## Conclusion

This project demonstrates how Cisco Packet Tracer can be used to design, configure, and test a simulated computer network. The documentation helps explain the network topology, addressing scheme, device configuration, and testing process.

## Author

Yohanes Marcel Krisna Mukti Wibowo
Informatics Student

## License

This project is created for educational purposes. You may modify and use it as a learning reference.
