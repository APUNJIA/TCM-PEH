```
#!/bin/bash
if ["$1" == ""]
then 
echo "You forgot an IP address!"
echo "Syntax: ./ipsweep.sh 192.168.1"

else
for ip in `seq 1 254`; do
ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d ":" &
done 
fi
```

Make sure to save this in a file called **ipsweep.sh** and make sure to give execute permissions to this file by:

```
$ sudo chmod +x ipsweep.sh
```

Run the following shell script by: 

```
$ ./ipsweep.sh <ip_address>
```

*$1* basically is used as a placeholder for the initial IP ip address. \

*$ip* is the placeholder for the rest of the IP addresses in the subnet

*ping -c* is the number of ICMP pings you want to send to the IP address

*grep* is to find the line which has a particular string

*cut -d* basically deletes the thing you want to delete in a specific string and *-f* will output the nth word after the deleted string

*tr* is for translate and *tr -d* will delete a specific character in a word(not the exact def but, deal with it)
