**ip a**: Displays the network interfaces and their associated IP addresses

**ifconfig**: Displays the configuration and status of network interfaces(very similar to ip a)

**iwconfig**: same as ifconfig but for wireless networks

**ip n**: Displays neighbour table, which contains the IP-to-MAC address mapping for devices in the local network

**Note**: the protocol responsible for giving [[IP addresses]] to [[MAC addresses]] is **ARP**(Address Resolution Protocol) 

**arp -a**: Displays the ARP cache which maps IP addresses to MAC addresses

**ip r**: Displays the routing table, which contains information about network routes

**route**: same as **ip r**

**ping**: sends an *ICMP* echo request to a specified IP address to check network connectivity and measure round trip time

**nmap**: scans the network to tell you what all devices are connected to a network and scans the ports as well.