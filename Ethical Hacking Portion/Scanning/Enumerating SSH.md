So SSH responds to port 22. Now, there's not much enumeration you can do for SSH as you can only connect to a certain device using an SSH connection. You do that by:

```
$ ssh <ip_address>
```

Now one of the reasons why we try to connect with SSH is to see if there is a banner which tells us what company has made this and other information which might be important. Lets say if you cannot connect to a device because of a key-exchange algorithm, you can run the following:

```
$ ssh <ip_address> -oKexAlgorithms=+<algorithm_you_want_to_add>
```

After which if it asks you for a cipher, you can simply add this to the previous command:

```
-c <cipher_you_want_to_add>
```

