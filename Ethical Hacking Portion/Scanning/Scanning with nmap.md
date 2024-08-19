nmap is a terminal tool which is used to tell what all devices are connected to a particular network. There are various settings that you can run nmap in and you can read through them using either the man pages(which lets be honest, no one does) or use the following command:

```
$ nmap --help
```

Lets take the [[How to download and setup Challs from VulnHub |Kioptrix]] chall for example, if we set up everything correctly, we should be able to run nmap on it successfully and get a list of outputs. The nmap command that we will run for this example(or for the other capstone challs in general) will be:

```
$ nmap -T4 -p- -A
```

What this command means is a couple of things. -T4 means the scan is a TCP scan and the speed of the scan where 1 is the slowest and 5 is the fastest. Normally nmap scans are really slow so we want a faster scan time so we choose 4. -p- means we want to scan all ports on the network whether they are open or not. -A means we want all the information out of the scan as possible. So it will output the services, their versions, operating systems as well etc. 

Once you run this command and if you wait long enough you will get an output similar to this:

![[Pasted image 20240813142033.png]]

And then we can use this information to exploit the system if it has any vulnerabilities.

In certifications like OSCP, the important game is to know how to enumerate. Because you never know what information that you can gather and what information you can use to complete a challenge.

Remember: *enumeration, enumeration, enumeration*.
