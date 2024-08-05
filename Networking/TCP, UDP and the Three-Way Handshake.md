**TCP**: Transmission Control Protocol
**UDP**: User Datagram Protocol

**TCP** is a *connection-oriented protocol* that provides reliable, ordered and error-checked delivery of data packets over an IP network. It guarantees that data sent from one device is received correctly by the destination device. It does this with the use of a *Three-Way Handshake*. **TCP** is widely used for applications that require guaranteed delivery, such as web browsing, email, file transfer and remote login. 

**UDP** is a *connectionless protocol* that does not provide the same level of reliability as **TCP**. It is simpler and more lightweight, making it suitable for applications that can tolerate some data loss or delay. It **does not** guarantee the delivery of packets. **UDP** is commonly used for real-time applications like streaming media, online gaming, **DNS**(Domain Name System) and **VoIP**(Voice over IP).

### Three Way Handshake

*Three Way Handshake* is a process used by **TCP** to establish a connection between two devices. It is a sequence of three steps that takes place before data transmission can begin. Here's how it works:

**SYN** > **SYN ACK** > **ACK** 

Once the *three-way handshake* is complete, the connection is established and both devices are ready to exchange data. 