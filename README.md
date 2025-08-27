# Net Practice

## 42cursus' project #10
The net_practice project is our first networking related project in the 42 curriculum. It consists of 10 exercises in which you configure different small-scale networks to communicate with each other, using concepts learned about TCP/IP addressing.


Final score: Complete all levels for full credit.

## What is an IP Address?
An IP (Internet Protocol) address is a unique numerical label assigned to each device connected to a computer network that uses the Internet Protocol for communication. It serves two main functions: identifying the host or network interface, and providing the location of the host in the network. IP addresses allow devices to find and communicate with each other across networks, whether local or global.

## Types of Networks
Networks can be classified based on their size, coverage, and purpose:

- **LAN (Local Area Network):**
  - Covers a small geographic area, like a home, office, or building.
  - Used for connecting computers and devices within close proximity.
  - Example: Office network connecting computers and printers.

- **WAN (Wide Area Network):**
  - Covers a large geographic area, often a country or continent.
  - Connects multiple LANs together, often using public networks like the Internet.
  - Example: The Internet itself, or a company network connecting offices in different cities.

- **WLAN (Wireless Local Area Network):**
  - A LAN that uses wireless technology (Wi-Fi) to connect devices.
  - Common in homes, cafes, and offices for mobile device connectivity.


  - Very small network, typically within a range of a few meters.
  - Used for connecting personal devices like smartphones, tablets, and laptops (often via Bluetooth).
  - Example: Connecting a phone to wireless headphones.

## Author
- GitHub: [mtarza13](https://github.com/mtarza13)

## Table of Contents
- [What is a Network?](#what-is-a-network)
- [TCP and IP Address](#tcp-and-ip-address)
- [IPv4 and Subnet Masks](#ipv4-and-subnet-masks)
- [Connecting Multiple Devices](#connecting-multiple-devices)
- [Switch](#switch)
- [Router](#router)
- [Routing Table](#routing-table)
## Table of Contents
- [What is a Network?](#what-is-a-network)
- [TCP and IP Address](#tcp-and-ip-address)
- [Switch](#switch)
- [Router](#router)
- [Routing Table](#routing-table)
- [Levels](#levels)

## What is a Network?
In simple terms, a Network in computing is a group of two or more devices that can communicate amongst each other. By communicating we mean the possibility of sending and receiving data (or packets) between different devices (or nodes).

The Internet is one of many examples of a network. It is probably the biggest network in the world, and connects many different nodes, making the sharing of data available between devices located anywhere in the world.

On the other hand, we also have Private Networks. A Private Network allows for communication between devices that are restricted to a specific location or domain. The data transfer is not allowed for anyone unregistered, making it a much safer and controlled environment. A Home Network is an example of private network. In there, you can connect to your personal printer when no one who isn't connected to your house's Wi-Fi, for example, could.


Transmission Control Protocol (TCP) is a communication standard protocol that enables nodes to communicate with each other. TCP is responsible for breaking data into small pieces (packets), sending them over the network, and then rebuilding them while ensuring there is no data lost in the process.

IP (Internet Protocol) assigns unique addresses to devices for identification and routing. TCP and IP are not the same thing, but rather two separate protocols that work together to ensure data transfer between different devices.
There are two versions of IP Addresses: IPv4 and IPv6. For this project, only IPv4 is needed.

## IPv4 and Subnet Masks

It is fundamental to learn how to visualize each IP Address in its binary form. Every IP Address can be split into two pieces of information: the Network and the Host address.

Masks can be represented as a full IP Mask or by CIDR notation.

### Example 1
- IP Address: 153.172.250.12
- Subnet Mask: 255.255.255.0
- Network Address: 153.172.250.0
- Usable IPs: 153.172.250.1 to 153.172.250.254

### Example 2
- IP Address: 153.172.175.12
  - Subnet Mask: 11111111.11111111.11110000.00000000

When reading a mask from left to right, once a zero appears, the mask will be completed with only zeros. For masks, there are only nine possible 8-bit blocks:

0, 128, 192, 224, 240, 248, 252, 254, 255

When dividing a larger network into subnets, reserve 2 IP addresses:
- The first IP in the range identifies the subnet.
- The last IP is reserved for broadcasting messages across all devices in the subnet.

#### CIDR Table
| CIDR | Subnet Mask | # of IPs | Usable IPs |
|------|-------------|----------|------------|
| /32  | 255.255.255.255 | 1 | 1 |
| /31  | 255.255.255.254 | 2 | 2 |
| /30  | 255.255.255.252 | 4 | 2 |
| /29  | 255.255.255.248 | 8 | 6 |
| /28  | 255.255.255.240 | 16 | 14 |
| /27  | 255.255.255.224 | 32 | 30 |
| /26  | 255.255.255.192 | 64 | 62 |
| /25  | 255.255.255.128 | 128 | 126 |
| /24  | 255.255.255.0   | 256 | 254 |
| ...  | ...             | ... | ... |

## Connecting Multiple Devices
Public Networks like the Internet are established by telecommunication providers to connect devices globally. A Public IP Address is assigned by your Internet Service Provider (ISP) to your router, allowing connectivity to your private network.

Your private network is established by a switch inside your router. The router assigns Private IP Addresses to devices connected to your network, following subnet mask and IP rules.

### Reserved IP Ranges
| Range | Purpose |
|-------|---------|
| 10.0.0.0 - 10.255.255.255 | Private IPs (Class A) |
| 127.0.0.0 - 127.255.255.255 | Loopback and internal testing |
| 172.16.0.0 - 172.31.255.255 | Private IPs (Class B) |
| 192.168.0.0 - 192.168.255.255 | Private IPs (Class C) |
| 224.0.0.0 – 239.255.255.255 | Multicast |
| 240.0.0.0 – 255.255.255.255 | Experimental/research |

## Switch
A network switch is responsible for distributing packets between devices within the same network (usually a LAN). A switch does not have any interface and cannot talk to a network outside of its own.

## Router
A router is responsible for connecting multiple networks together. Every router has an interface for every network it connects to.

Since it connects multiple networks, the range of possible IP addresses on one of its interfaces must never overlap the range of its other interfaces. An overlap would imply the interfaces belong to the same network.

## Routing Table
A Routing Table is a simple data table stored in a router or network host that lists all the routes to a particular network destination.

In Net Practice, a routing table consists of two pieces of information:
- **Destination**: The IP address you want to send a packet to, combined with the CIDR of that network (e.g., 190.3.2.252/30). If you want to make it available for the entire network, set it to default or 0.0.0.0/0.
- **Next Hop**: The IP address of the next router to send the packets to in order to reach the destination network.

## Net Practice Levels
The project includes 10 levels, each with a different network configuration challenge. JSON files (e.g., `level1.json`, `level5.json`) describe the network setup for each level. Each level requires you to:
- Analyze the network topology
- Assign IP addresses and subnet masks
- Configure routing tables
- Ensure connectivity between all required devices

---

### Level Visual Gallery
Place your images in the `img/` folder and use the provided filenames, or update them to match your own. Each image will appear as a sidebar visual for the corresponding level.

| Level | Diagram |
|-------|--------|
| **Level 1**  | ![Level 1 Network](img/level1.png) |
| **Level 2**  | ![Level 2 Network](img/level2.png) |
| **Level 3**  | ![Level 3 Network](img/level3.png) |
| **Level 4**  | ![Level 4 Network](img/level4.png) |
| **Level 5**  | ![Level 5 Network](img/level5.png) |
| **Level 6**  | ![Level 6 Network](img/level6.png) |
| **Level 7**  | ![Level 7 Network](img/level7.png) |
| **Level 8**  | ![Level 8 Network](img/level8.png) |
| **Level 9**  | ![Level 9 Network](img/level9.png) |
| **Level 10** | ![Level 10 Network](img/level10.png) |

---

## Resources
- [mtarza13 GitHub](https://github.com/mtarza13)
- [Subnetting Mastery](https://www.practicalnetworking.net/stand-alone/subnetting-mastery/)
- [Cisco: Can two hosts with different subnet masks be on the same subnet?](https://learningnetwork.cisco.com/s/question/0D56e0000BNp5TwCQJ/can-two-hosts-with-different-subnet-masks-be-on-the-same-subnet)
- [IP Subnet Calculator](https://www.calculator.net/ip-subnet-calculator.html)
- [NetworkChuck's Free CCNA Course](https://www.youtube.com/playlist?list=PLIhvC56v63IJVXv0GJcl9vO5Z6znCVb1P)

---
This README summarizes networking concepts and the Net Practice project structure. For details on each level, refer to the corresponding JSON files.

---
This README summarizes networking concepts and the Net Practice project structure. For details on each level, refer to the corresponding JSON files.
