*IPv4* and *IPv6* are two versions of the Internet Protocol, which is the underlying protocol that enables communication on the internet. They are used to identify and locate devices on a network.

### How to see IP address on a device?

You can run *ifconfig* on Linux. It is similar to *ipconfig* on Windows. It gives you an output like this:

![[Pasted image 20240805093917.png]]

Here, *inet* is the IP address of your machine(IPv4) and *inet6* is *IPv6*. It uses hexadecimal notation.

Here, *ether* is [[MAC Addresses]].

It runs on **Layer 3** of the [[OSI Model]]. **Layer 3** is the *router level*.

*IPv4* addresses are made of 32 bits of 0s and 1s. 8 in each decimal(so all ip addresses can be from 0.0.0.0 to 255.255.255.255). This is important for understanding [[Subnetting]].

### Why are we using two sets of IP addresses?

We came up with *IPv6* because we were running out of *IPv4* addresses. But still we are not using *IPv6* as the De-facto format. Why?

**NAT**: Network Address Translation

What *NAT* does is, it sets up private IP addresses for the different devices that are on the internet. So if we are in a big company, you would be using a *Class A* private IP address as it has more number of hosts. And if you're just a single person, you use *Class C* private IP addresses. 

Classes of private IP addresses:

![[Pasted image 20240805094548.png]]


