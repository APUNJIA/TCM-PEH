First see if you have the latest version of bloodhound.

```bash
sudo pip install bloodhound
```

Then you run something called neo4j

```bash
sudo neo4j console
```

This is required for us to run bloodhound. Open the link that you get after running the command and log in using neo4j:neo4j. Then change your password.

Then run bloodhound and then log in to the creds you set up for neo4j. Then make a new directory for bloodhound.

```bash
mkdir bloodhound
cd bloohound
bloodhound
```

then run the following command:

```bash
sudo bloodhound-python -d <name_of_domain> -u <name_of_user> -p <Password> -ns <ip_of_DC> -c all
```

-d is domain name, -u is user, -p is password, -ns is nameserver,which is going to be our domain controller, -c is the the list of things that we're collecting.

Then you can go to bloodhound tool, and then go to import data and then we can import data from our bloodhound directory which is at:

```bash
/otherlocations/computer/home/root/kali 
```

