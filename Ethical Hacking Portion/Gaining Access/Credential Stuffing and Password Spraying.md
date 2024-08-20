Before doing this, see if BurpSuite and/or FoxyProxy is set up. If you haven't done so yet, you can refer [[Information Gathering with Burp Suite]]. 

Now, lets take an example of a sign in page where you have to give your email and password to sign in into the website. 

Turn your intercept on inside BurpSuite and just put some random credentials into the sign in page. 

In the BurpSuite results, it will show a line which mentions the username and password we have given. Right Click that line and click send to intruder. 

Then go to intruder > positions and hit clear. Then highlight the email portion of the line and click add. Do the same for password as well.  

Since we are attacking 2 things, the attack type will be pitchfork. 

Then go to payloads. Since we are giving 2 types of information, we have to set 2 different types of payloads. Set payload 1 with the emails, and set payload 2 with the passwords. 

And then, hit start. What we are looking for is a status change, which usually means a redirect of some sorts. Or we are looking for a change in length. If the length is somewhat similar in all the attempts, what you can do is, you can copy a string which has something like "we could not sign you in", and add it in the grep feature of options next to payloads.

Password spraying is the same thing as credential stuffing but you are doing it for a known username or email ID. You usually do password spraying for active directories. But there might be a lockout period which is you will be locked out of the machine after a certain number of failed login attempts. So check that once before password spraying on active directories. 

Also for password spraying, since we are using only one input, put the attack type as sniper.



