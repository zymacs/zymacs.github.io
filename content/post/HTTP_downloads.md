---
thumbnail: "img/router.jpg"
title: 'The anatomy of a download over TCP'
date: 2026-05-07
tags:
 - http
 - tcp
draft: false
categories:
 - networking
---


Let's look at what happens when from download instantiation by some download client to
when all data is in its completeness transferred from the remote location to the downloader's storage.


## Getting a uri to a remote resource

You have been given some link of the form `http://somesite.com:8000/file.txt` to a remote file.
From the URL we can tell the remote file is located at / and its called `file.txt`.
This website is on the internet. Its hosted somewhere off your system accessible via a network. 

So you open your browser or , lets say, you just click the link to instantiate the download action.
Let's assume the handler app for downloads is a browser.

## Address translation with DNS

![Curl Name Resolution](assets/img/nameresolution.png)

The browser then  translates the link you were given to an IP address. An [IP address](https://en.wikipedia.org/wiki/IP_address) is a unique ID for a node in a network, which in this case is the internet. This resolution is done via [DNS](https://en.wikipedia.org/wiki/Domain_Name_System). 

## Connection Initiation

![Curl establishing connection via port](assets/img/connection_phase.png)
With the IP addres resolved, the process moves on to initiate
a connection with the target host at port 8000. The connection is of a streaming type connection using
the TCP protocol. Its over this TCP session that the download happens.
It's lifecycle has three phases.

### Connection setup phase: The three way handshake summary

![Connection Phase: Wireshark](assets/img/connection_phase.png)

The browser, sends a SYN packet with some random number `a` to the server to request connection establishment and waits for a response.

Packets are smaller subdivisions of a larger message from a networks perspective. A SYN packet in
the Transmission Control Protocol instantiates communication between two nodes on a network while an ACK packet
acknoledges receipt of sent message. Okay, back to the point.  

The server acknowledges this SYN with an ACK packet that's with a number `a+1` (_i.e., I got `a`, now send `a+1`). It also sends its own SYN that's some random number `b`.

The browser on receipt confirms it has recieved the server `SYN` with an ACK thats with value `b+1` (I got be, send b+1) if sending
anything next.

Now the connection is established. So we move from the establishment phase of the connection to the transfer phase. 

### Established phase: Data transfer
![Established phase: Wireshark](assets/img/transfer_phase.png)
The browser sends an http `GET` request to the server requesting for the target
resource, `file.txt`  over the  established TCP connection.
The server response with the http code 200 denoting a successful request
and data is streamed to the client over the TCP connection till its downloaded in totality.


### Tear down phase: Connection conclusion
![Tear down phase: Wireshark](assets/img/3_way_end.png)
Data transfer has come to completion without error. The server then initiates termination of the TCP connection with a two way handhshake for HTTP.

It sends a FIN packet (_I am done, closing connection_) plus an ACK acknowledging the last sent SYN by the client. The client responds with a FIN and ACK too. The FIN says it's done too and the ACK acknoledges it received the FIN. The server finally sends an ACK to end the session. 

And that's it, the transaction is complete. 


In the article I used the application layer protcol `http 1.0` for demonstration but it could be any other application layer protocol say smtp, or ftp or any other.

I am writing this as a means to internalize what what I'm reading about networks and also, to have notes to build upon when I learn more. If you learnt something from reading this, that's a plus for me. I will keep updating it as my knowledge of networks grows.