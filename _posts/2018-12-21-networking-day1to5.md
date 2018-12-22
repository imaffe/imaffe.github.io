---
layout:     post
title:      "Learn Networking Top Down in Ten days"
subtitle:   "Day 1 ~ Day 5"
date:       2018-12-21 12:49:00
author:     "affe"
header-style : text
header-img: "img/post-bg-2015.jpg"
tags:
    - networking
    - 10day
---

> 拖延是焦虑之源

# Computer Networking : Top Down Approach

I got  stuck in socket programming these days, and I found that I know nothing about the nature of computer networking. All my knowledge come from experiences rather than systemactical practice. Then I decide to learn a computer networking book in the rest of my vacation. I choose *Computer Networking : A Top-Down Approach 6 edition*. People all say this is a really good book. My title is in 10 days but not true exactly. Giving myself a ten day constraint doesn't mean I have to look at my screen all day long but suggest that I must concentrate myself in computer networking. That is put myself into 'computer networking' context ! I believe this will help me a lot. Specific notes can be seen in github repo [MarkdownTransfer](https://github.com/imaffe/MarkDownTransfer), and find Networking.md in root directory. This blog noted what skills I got from my questions during reading  and manuals for these problems.

## Day 1 : application layer

- **Difference between router , switch and modem !**

  a simple explanation : modem connect LAN to Internet, router connects LANS, and switch compose a LAN.

- **How to trace a route ?**

  Most linux distributions (I'm not sure if all) has a tool called *traceroute*. If we don't I assume we can easily install using apt or yum or rpm or curl or anything from Stackoverflow. traceroute command used like `traceroute www.google.com`. The underlying implementation has something to do with IP protocol. I will cover this when I get to that part.

- **what is *telnet* and what we can do with it ?**

  telnet itself is a protocal, and the related wiki is here : [telnet](https://en.wikipedia.org/wiki/Telnet). My personal explanation : telnet is a lower version of SSH without security. 

- **Since a server has only one 80 port, why multiple http request won't conflict on that port ?**

  This question is super good and helped me a lot understanding what ports are when I know nothing about TCP details. I'll explain in more detail and thanks to great answers from Stackoverflow. 

  First, we worry about what if two request comes to the port at the exact same time. This is answerd in [Quora Answer](https://www.quora.com/What-happens-if-literally-two-requests-exactly-at-the-same-time-reach-a-server). It says this situation is handled by Network Interface Card hardware and can be guaranteed there will always be an order, even if you have two NICs, the CPU will choose one packet to process. So in this level, there is always an order of occurence.

  Second ,  Some unexpected gain : A connection is specified by  ( or has a primary key of ) { SRC-IP, SRC-PORT, DEST-IP, DEST-PORT, Protocol}, so basically we have source port and destination port. For example, a web browser request for a usually high numbered port from OS  like (32313) and connect to server port 80. This is a unique connection compared with other sockets with different source IP address or same IP address but different source port number. For server, once the socket is different, it can distinguish which packet belongs to which connection even though they all come from port 80.  Bonus question is , cam two different processes listen to same port like port 80 if all using TCP? Answer is not because a single client send request to the port but don't know which process should take this request. But once we allow use of different protocols (which should be so), two process can listen to the same port. [Stackoverflow Answer](https://stackoverflow.com/questions/3329641/how-do-multiple-clients-connect-simultaneously-to-one-port-say-80-on-a-server), [Another example of source port](https://stackoverflow.com/questions/2957757/how-can-an-application-use-port-80-http-without-conflicting-with-browsers)

- **what is welcome socket and connection socket in socket programming ?**
- **Not yet covered, maybe tomorrow !** 

- **what is carriage return and line feed ? CR and LF ?**

  [Stackoverflow : ask me anything](https://stackoverflow.com/questions/3091524/what-are-carriage-return-linefeed-and-form-feed) basically CR is return to the start of the line but not moving to next line, LF is moving downwards to the next line.

- **How do I know if I'm behind a proxy or not ?**
  [Stackexchange](https://askubuntu.com/questions/276811/how-can-i-find-out-the-proxy-address-i-am-behind/276813) using command line in linux `env | grep -i proxy`, or go to   <https://www.whatismyip.com/proxy-check/?iref=home> to find proxy check ! But what if I want to know the mechanism of detecting a proxy ? 

- **What is the underlying mechanism of detecting a proxy ? (How the link above works)**
  Not yet covered ! Maybe tomorrow or when I want to know how the Great Firewall works ! 

- **How does the Great Firewall in China works ?**

  I will cover this when I learned DNS tomorrow !

- **Is there any proxy service software like Apache for web server?** 

- **Can I use telnet to communicate with the SFU mail server?**

- **How do I explain Apache to a guy know nothing about computer networking ?** 