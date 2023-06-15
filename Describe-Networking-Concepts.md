# Chapter 11: Describe Networking Concepts:

## TCP/IP Network Model:
- Describes how data communications are **packetized, addressed, transmitted, routed, and received** between computers over a network.
- 4 Layers:
- 1. Application: For Representaion of data. Protocols: SSH, HTTPS (secure web), FTP (file sharing), and SMTP (electronic mail delivery).
- 2. Transport: For virtual-circuit connection between applications (Ports & Protocols) Protocols: TCP/UDP
> A list of well-known and registered ports is in the `/etc/services file`
- 3. Internet: carries data from the source host to the destination host. Protocols: IPv4 and IPv6
- 4. Link: provides the connection to physical media. Protocols: wired Ethernet (802.3) and wireless Wi-Fi (802.11).
- **Summary**:
- ![image](https://github.com/cybersome/Linux-octo/assets/40174034/7a7794f7-9908-4a8b-9d7f-b7494f322696)

## Network Interface: 
- eth0, eth1, and eth2 (interface name was the first network port that the operating system detected)
- Ethernet interfaces begin with **en**
- WLAN interfaces begin with **wl**
- WWAN interfaces begin with **ww**
- <img width="500" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/8ce91e1e-6a1a-4542-9c2f-3a17e5435b4d">
- <img width="500" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/318e5b48-223f-4342-bd85-5b9bf1251491">

## Example Network Calculations:
- <img width="448" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/ff6e80c1-80ac-40a9-ba72-9f5a1baac52d">
- <img width="451" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/9ed73510-df68-4b5b-9cba-806959948fc2">
- <img width="453" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/db661a13-e393-43c9-b54f-94e29c5a1832">
- <img width="885" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/1b66efc1-de60-4ba5-8af1-56f5078b182b">
> To create static entries for each hostname in each system's `/etc/hosts` file
> A nameserver configuration is typically obtained through DHCP or by creating static address settings in the `/etc/resolv.conf`

## Gather Network Interface Information:
- To lists all available network interfaces on the system: `ip link show`
- To view device and address information: `ip addr show eth0`
- Verify Connectivity Between Hosts: `ping -c3 192.0.2.254`
 

## IP Subnetting, Subnet mask, Host & Broadcast Address:
> eg. 192.168.5.85/24
- Step 1: Calculate the **Subnet Mask** (Depends on CIDR Notation ie /24, /30, /8 >> Rep. the Network Bits) or Classful addressing
- Step 2: Lining up the **Given IP address and the subnet mask** together, the network and host portions of the address can be separated.
- Once get the network and host portions, Calculate the **Host Range** other parts.
- To Calculate Usuable Hosts: `2^n - 2` where n = Host bit
- Last Host Address is **Broadcast Address**

## Labs:
- Display the current IP address and netmask for all interfaces: `ip -br addr`
- Display the statistics for the enX interface: `ip -s link show enX`
- Display the route information: `ip route`
- Show all the hops between the local system and the classroom.example.com system: `tracepath hostname/ip_address`
- Display the listening TCP sockets on the local system: `ss -lt`

## The NetworkManager Service:
- The `NetworkManager` service monitors and manages a system's network settings.
- Service configuration files are stored & can be managed in the `/etc/NetworkManager/system-connections/` directory.
- To displays the status of all network devices: `nmcli dev status`
- To displays a list of all connections: `nmcli connection show`
- To disconnects the network device and brings down the connection: `nmcli dev disconnect Network_Connection`
- The next example loads only the eno2 connection profile: `nmcli con reload eth0`
- To delete a Network Connection: `nmcli con del Network_Connection`
- To view your current permissions: `nmcli gen permissions`
- <img width="500" alt="image" src="https://github.com/cybersome/Linux-octo/assets/40174034/2dcc2306-5e8d-40ef-983e-0b8c1d4cdc42">
- Show the device status: `nmcli dev status` & reload `nmcli con reload`

## Lab:
### Edit the Network Configuration Files:
- Locate network interface names: `ip link`
- Show active connection: `nmcli con show`
- Edit the Network Configuration File: `vim /etc/NetworkManager/system-connections/"Wired connection 1.nmconnection"`
- Reload the configuration changes: `nmcli con reload`
- Activate the connection with the changes: `nmcli con up "Wired connection 1"`
- 

