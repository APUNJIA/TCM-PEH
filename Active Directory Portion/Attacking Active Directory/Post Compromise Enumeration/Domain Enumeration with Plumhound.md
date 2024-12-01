This is a fork of the original [[Domain Enumeration with Bloodhound |Bloodhound]] and it can be found on github.

In order to download it, first, go to your opt directory and then clone the repo there. Im not gonna mention how, you should know how to git clone and do that stuff. If not... RTFM.

Then cd into the plumhound folder and run this:

```bash
sudo pip3 install -r requirements.txt
```

Before running this tool, lets test this tool out first by using this command:

```bash
sudo python3 PlumHound.py --easy -p <neo4j_password>
```

Note: Before running the above plumhound command, your neo4j and your bloodhound should be running.

Then we can run plumhound by using this command:

```bash
sudo python3 PlumHound.py -x tasks/default.tasks -p <neo4j_password>
```

This makes a report of the thing and moves it to the Reports folder. Go to that folder and unzip the zip file.