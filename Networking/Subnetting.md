**Subnetting** is the process of dividing a network into smaller subnetworks called **subnets**. It allows for more efficient use of IP addresses and facilitates network management and routing. It is common in *IPv4* networks.

It involves borrowing bits from the host portion of an IP address to create a **subnet identifier**. By doing this, a network can be divided into multiple subnets, each with its own range of IP addresses.

**CIDR** (Classless Inter-Domain Routing) notation is a method used to represent IP addresses and their corresponding subnet masks. It specifies the network prefix length, which indicates the number of bits used for the network portion of the IP address. **CIDR** notation is expressed by appending a forward slash (/) followed by the prefix length to the IP address. 

For eg: 192.168.1.0/24. Here, */24* represents the **prefix length** indicating that the first 24 bits represent the network portion of the IP address while the remaining 8 bits represent the **host portion**.

### How to do it practically

If we do *ifconfig* like we did in [[IP Addresses]], we will see *netmask* next to *inet* which shows us the **IPv4**. This netmask is also called subnet mask which, just like IP addresses, comprise of 4 parts of 8 bit numbers separated by a period. 

![[Pasted image 20240805122104.png]]

Here, our *netmask* is 255.255.255.0. This means we are using a */24* network. A */24* network means that we have 2<sup>8</sup> hosts available. And if we increase the network to something like */25*, we will have lesser number of hosts.

![[Pasted image 20240805122359.png]]

So if we look at the reference table up there, if we have a */25* network, our subnet mask is going to end with *128*, so in this case it will be 255.255.255.128. And the number of hosts will be 2<sup>7</sup>. 

**Note**: As we go down the network number, the number of hosts go up and vice-versa.

Similarly if we had a */17* network, we would have a subnet mask of 255.255.128.0

**Important**: Always subtract 2 from host total. This is because usually .0 becomes your network ID and .255 becomes your broadcasting IP.

So... lets have some examples:

| IP              | Subnet          | Hosts | Network      | Broadcast     |
| --------------- | --------------- | ----- | ------------ | ------------- |
| 192.168.1.0/24  | 255.255.255.0   | 254   | 192.168.1.0  | 192.168.1.255 |
| 192.162.1.0/28  | 255.255.255.240 | 14    | 192.168.1.0  | 192.168.1.15  |
| 192.168.1.16/28 | 255.255.255.240 | 14    | 192.168.1.16 | 192.168.1.31  |
| 192.168.0.0/23  | 255.255.254.0   | 510   | 192.168.0.0  | 192.168.1.255 |
| 192.168.2.0/23  | 255.255.254.0   | 510   | 192.168.2.0  | 192.168.3.255 |
| 192.168.0.0/22  | 255.255.252.0   | 1022  | 192.168.0.0  | 192.168.4.255 |
| 192.168.1.0/26  | 255.255.255.192 | 62    | 192.168.1.0  | 192.168.1.63  |
| 192.168.1.0/27  | 255.255.255.224 | 30    | 192.169.1.0  | 192.168.1.31  |

**Note**: We cannot have an address like 192.168.1.0/23 because we do not have the ability to lock in .1 as the number of hosts would not be fulfilled as there are a total 512 hosts and locking in the .1 would mean that there would only be 255. The subnet mask of this is going to be 255.255.254.0

One website that can help you make subnets of all this is https://www.ipaddressguide.com/cidr

