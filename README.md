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

