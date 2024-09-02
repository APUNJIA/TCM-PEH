**Important**: We use sockets to make connections between ports and [[IP Addresses]]

**Also Important**: Don't name your python file "Socket.py" as socket is a library that is inbuilt into python and it will cause an issue with the thing.

This is the implementation of sockets in python:
```Python
#!/bin/python3

import socket

HOST = '127.0.0.1'
PORT = 7777

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  #af_intet is ipv4, sock_stream is a port

s.connect((HOST, PORT))
```

This is the port scanner project:

```Python
#!/bin/python3

import sys
import socket
from datetime import datetime

#define target

if len(sys.argv) == 2:
	target = socket.gethostbyname(sys.argv[1]) #translate hostname to IPv4
else:
	print("Invalid amount of arguments")
	print("Syntax: python3 scanner.py <ip>")

#Add a pretty banner

print("-" * 50) 
print("Scanning target "+target) 
print("Time started: "+str(datetime.now())) 
print("-" * 50)

try: 
	for port in range(50,85): 
		s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
		socket.setdefaulttimeout(1) 
		result = s.connect_ex((target,port)) #returns an error indicator - if 
		port is open it throws a 0, otherwise 1
		if result == 0: 
			print("Port {} is open".format(port)) 
		s.close() 

except KeyboardInterrupt: 
	print("\nExiting program.") 
	sys.exit() 

except socket.gaierror: 
	print("Hostname could not be resolved.") 
	sys.exit() 

except socket.error: 
	print("Could not connect to server.") 
	sys.exit()
```