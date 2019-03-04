# Firewall-Evasion (Bypass strict firewalls on restricted networks)

As you can see, more and more pulic wireless hostspots are available with a subscription, 
accessible throught a web login form. The thing is, most of the tiem ,theses hospots will have
a reduced connectivity. Only some ports and protocols will be allowed. For instance, you may be restricted 
to HTTP, HTTPS, POP and SMTP. And this also applies to protected networks, such as libraries, schools and office 
enviromnets, where your access to internet is limited, and some ports and protocols are blocked. 

But with SSH tunneling, we can bypass this restricted firewalls.

## What we need?

> * HTTPS access through the firewalls. Most hotspots will leave HTTPS open, port 443, so that people can 
browse Internet and go to secure sites.
> * A server somewhere on Internet, even a Raspberry pi, with root access.
