# Firewall-Evasion (Bypass strict firewalls on restricted networks)

As you can see, more and more pulic wireless hostspots are available with a subscription, 
accessible throught a web login form. The thing is, most of the tiem ,theses hospots will have
a reduced connectivity. Only some ports and protocols will be allowed. For instance, you may be restricted 
to HTTP, HTTPS, POP and SMTP. And this also applies to protected networks, such as libraries, schools and office 
enviromnets, where your access to internet is limited, and some ports and protocols are blocked. 

But with SSH tunneling, we can bypass this restricted firewalls.

## How it works?

What we do is create a SSH tunnel, which connects from your machine, to your server, through port 443 (HTTPS port). 
This tunnel listens on a given port on your machine, and redirects everything to Internet, through another 
given port on the server. So you can for instance create an IMAP connection from your machine to any mail server 
out there, even if the firewall disallows IMAP.

## What we need?

* HTTPS access through the firewalls. Most hotspots will leave HTTPS open, port 443, so that people can 
browse Internet and go to secure sites.
* A server somewhere on Internet, even a Raspberry pi, with root access.

## Setting up the Server

You need to access your server at least onece via regular SSH, port 22. If you are already behind the 
restricted firewall, you will not be able to log in the server using port 22.

> * Set the Server to be listening on the port 443 (HTTPS port). Simply Log into server, and edit the file /etc/ssh/sshd_config and add the line: Port 443.
> * After setting up, reboot the server with following command: sudo reboot.

Now you can access the server using port 443. Command: ssh -p 443 $user@my server address$, Since I am using Raspberry pi, 
I access with pi with 
```ssh -p 443 root@192.168.2.2```
in local enviroment.

## SSH tunneling

If you want to access to email account via IMAP (basically port 143) when the firewall forbids it. You can create 
a ssh tunnel with the following command: 
```ssh -L localhost:10143:$imap.qq.com:143$ -p 443 $user@my server address$```

Here is an example: 
```ssh -L localhost:10143:imap.qq.com:993 -p 443 root@192.168.2.2``` 

Then type in my passwords of server. 

Now I can bypass the firewall that forbids the Port 993. This would forward any IMAP requests received on localhost port 
10143 to imap.qq.com port 993, all through a ssh tunnel. After that we can set up our mail application using 
```localhost:10143```
as incoming server and port, then we are able to receive our emails on restricted filewall.
