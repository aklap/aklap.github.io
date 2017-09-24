---
comments: true
date: 2016-09-06T00:00:00Z
tags:
- IPv6
- networking
title: Why and how to become a certified IPv6 technician.
type: '/blog/post'
layout: 'single'
---
I recently finished a certification for IPv6 through Hurricane Electric. But IPv6—what is it and what is it good for?

**What is IPv6?**

In order to send and receive data over the internet, we need to know both the sender and receiver and have a means for standardizing the way we handle sending and receiving data using the internet. Think of it like sending a letter. In the US, if I wanted to send a letter to my penpal in California, I would need to follow some rules about how to package my letter (in a letter with certain dimensions and weight, plus a stamp) and with a particular address format on the outside (street number, street name, city, state and zipcode).

<iframe width="560" height="315" src="https://www.youtube.com/embed/iKBo_YPdFgI" frameborder="0" allowfullscreen></iframe>*'That's not protocol'*<br>

Everyone agrees to these rules ([unlike in Iceland](https://twitter.com/tinybop/status/771769801962315776)), so we can standardize how we send letters—that rules governing how we should be sending and receiving letters is a protocol. We can refer to rules governing certain behaviors or actions as ‘protocol,’ and you’ll see that word in terms like TCP/IP (Transmission Control Protocol/Internet Protocol) and FTP (File Transfer Protocol). Maybe you’ve heard, the cliched phrase, “That's not protocol” in a movie or TV show like this Staples commercial.

IPv6 stands for “Internet Protocol 6.” What we mostly use when we communicate over the Internet is a protocol known as IPv4 (“Internet Protocol 4”). IPv6 then is the next generation or version of Internet Protocol.

**Address Exhaustion**

You might ask yourself, why bother changing when the Internet seems to be just fine. I can browse the sites I want and get my email; what’s the problem?

The main one is that there are an ever growing number of users and devices (think the Internet of Things) that requires more and more IP addresses. With IPv4, we create addresses for devices in a certain format with decimal numbers and periods, but using that format we can only create 232 (4,294,967,296) addresses. That’s just not enough.

Think about how many devices you owned in 1999 that connected to the internet vs 2016. How many devices at work connected to the Internet at work in 1999 vs 2016. Now multiply that by the population just in the US. That’s a large increase in IP address demand just here in the US.

IPv6’ solution replaces the 32-bit IPv4 addresses with 128-bit ones. That means 2^128 possible addresses vs. IPv4’s 2^32.

**Relevance to Security**

Since IPv6 is the future, it’s important to understand what IPv6 is, how it works, and familiarize yourself with how to setup your own computers and servers to use IPv6, most likely through tunneling services, like Hurricane Electric or SixXs.

Most of the concern about IPv6 comes from a documented IP leak problem. When using VPNs that didn’t support IPv6, it was possible that they did not route through the tunnel and thus, your traffic and IP were visible, rendering useless the privacy capability of a VPN service. There are a number of sites you can use to check for IP leak, but at this point, (the paper that detailed this vulnerability is from 2015), a reputable VPN should’ve addressed this, (pun intended). In the case of the VPN I use, it simply forces IPv4, (not sustainable long-term but an easy fix). The other fix is just to disable IPv6 on your computer/server.

**Learning about IPv6**

There’s a lot of material out there to learn about IPv6, most of it from several years ago, when in 2011 we had World IPv6 Day and in 2012 we had World IPv6 Launch day (both organized by the Internet Society). Since then, ISPs like Time-Warner Cable have rolled out IPv6 service to large portions of their customer service base, though Verizon notably is dragging its feet and their customers still do not have IPv6 service nor has Verizon given any timeframe as to when they will be implementing it.

So, if you do not have access to IPv6, then you will need to access it via tunneling.

Fortunately, the largest IPv6 transit network is operated by Hurricane Electric and they have a certification program in addition to tunneling services, both of which are free. If you’d like to play with IPv6 there are some projects on Sam Bowne’s site that help you set up IPv6 and use it for a simple AWS EC2 server.

**Learn from my mistakes!**

I made some silly mistakes while learning about IPv6, so I offer them here for you to learn from.

- __Do not use Firefox when testing your IPv6 setup.__ Firefox disables IPv6 lookups which is something I didn’t realize earlier and lead to me being puzzled for some time as to why I was able to ping6 IPv6 sites successfully, yet not view the site in a Firefox browser. Instructions online suggest altering your about:config file in the browser and changing the very confusingly worded settings with Boolean values for enabling/disabling IPv6. I tried it and it seemed to have no effect. I ended up going back to Chrome which worked just fine.

- __Use your local IP and not your public IP when setting up IPv6 config on your computer/server.__ Because I like to just do things rather than read about them, I sometimes miss the fine print. If you are using Hurricane Electric as your tunnel broker, you’ll see that in the example config files they give you for different OS, under the examples they say to slightly alter the commands to replace the public IP address you have with the local IP address assigned by your router in your WLAN.

On a Mac, you can find it in System Preferences > Network, where it says:

     “Wi-Fi is connected to {network name} and has the IP 
     address {your local IP address here!}.”

So remember, Hurricane Electric needs both your public IP address to connect to your router, and then you add your local IP address to then have your router connect with your device.

- __If you’re using a VPN, beware leaks.__ Either disable IPv6, which on a Mac is as easy as changing your network settings with a drop down menu, or use online IP leaks checker websites.

- __If you’re using a container service like Docker or VM, then there are additional steps to configuring it.__

- __To gain certification from Hurricane Electric, you’ll need access to a router to finish all the steps.__ This doesn’t hold true for Windows, which can bypass the router in the later portion of the challenges because it utilizes Microsoft’s IIS. (Sidenote: This slightly worries me for security reasons that your Windows computer can bypass the router and access the Internet. I don’t know what exactly is on Windows IIS side or how it works, but if it’s bypassing the router and directly Internet-facing, I would just say no to that. Apple used to enable Internet-facing web servers under a ‘personal web sharing’ option for creating personal websites, but that was gone with Mountain Lion.)

- __Gogo IPv6 tunnel services are dead.__ Use Hurricane Electric (or another service). If you follow the IPv6 track or the Hurricane Electric certification guide on Sam Bowne’s site, you’ll see he tells you to use Gogo. Ignore any of the instructions having to do with Gogo.

- __If you need help, find the most recent source of information.__ A lot of the IPv6 tutorials recommend using Gogo which is no longer around, or recommend setup instructions that are outdated.

**What’s good about learning about IPv6**

There are some great benefits to learning about IPv6. Some of the things I learned by following tutorials and doing the Hurricane Electric certification:

- How my local network interacts with the Internet
- How to set up an EC2 instance on AWS
- How email servers work/creating a basic email server
- What IPv6 is
- Enabling IPv6 on Mac OS/X and Linux & networking interfaces
- Apache servers
- Setting up an IPv6 tunnel
- IPv6 vulnerabilities
- Port forwarding
- Debugging network problems

If you’re curious about any of the above, I would encourage you to start playing with IPv6!

___
**Resources:**

- [Hurricane Electric Certification](https://ipv6.he.net/certification/)
- [Hurricane Electric Tunnel Broker](https://tunnelbroker.net/)
- [Sam Bowne's IPv6 projects](https://samsclass.info/ipv6/ipv6.php) 
-*Note that many of these links are outdated and some are broken. It's a good reference for ideas for projects.*
- [IPv6 IP Leak via VPNs](https://www.eecs.qmul.ac.uk/~hamed/papers/PETS2015VPN.pdf)

