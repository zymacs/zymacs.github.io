---
thumbnail: "img/router.jpg"
title: 'Why smaller files take longer to download'
date: 2026-05-06
draft: true
tags:
 - tcp
 - why_type
 - research
categories:
 - Networks
---


This article is going to have two children since needs some
prerequisite knowledge that would be too much to cram into
one article. I mean I could have said go read up on X from someone else then
come back but I read up on X and I could as well send you to my articles on X right?
Anyways. Say you have 1000 small files each 1kb in size, why is it that total time taken to transfer these all other factors kept constant is way more than time it takes to download a single file
that is 1000*1kb in size? Or for the other part of the article, if you have copied files between disks before, which I am sure you have, ever noticed how the speed falls when during data transfer, the
system encouters some really small size files? Its counter intutitive. I mean I'd expect smaller files to be copied over faster, and have faster download speeds also than bigger ones. But
when you understand what's going on under the hood , you learn why it ain't as simple as that. In this article we shall have a high
level overview, trust me there's so much to cover we'll have only hthat, for why this is so. Why transfers are slower for smaller files and why downloads take longer for these small files.

Now first, head over to this article for some theory on what happens when you click the download button.

You have downloaded files before. And even if you have never, if
you are reading this , your phone just did. So anyone using the internet has consciously or not downloaded files before. But how
does that work? What happens between when you click the download
button and when the file is fully downloaded?

To demonstrate that we need to first state some word definitions.
Client: Any device that is capable of obtaining data from a server.
Server: Any device that is capable of giving out information to
clients.
Download (action): Data transfer over a network from a server
to a client. 


## Getting an uri to a remote resource

You have been given some link of the form `http://randomsite.com/file.txt to a remote file and you want to some file hosted on randomsite.com. The remote file is file.txt.
The website is 'on the internet' but all that means is it's hosted on some computer beyond your local network.

So you open your browser or , lets say you just click the
link to instantiate the download. Let's assume the handler app is a browser.

## Address translation

The browser then  translates the link you were given , say, randomsite.com
to an IP address, a unique ID for the target site (randomsite.com)on the internet.  

## Connection Initiation

With the IP addres resolved, the process moves on to initiate
a connection with the target host at say port 8000 for https.
The connection is a TCP type connection. And here's how that works. 

### The three way handshake summary

Your client, say the browser, sends a SYN packet with some number `a` to the server to request connection establishment and waits for a response.
Packets are smaller subdivisions of a larger message from a networks perspective. A SYN packet in
the Transmission Control Protocol instantiates communication between two nodes on a network while an ACK packet
acknoledges receipt of sent message. More about TCP packets here. Anyways. 
The server acknowledges this SYN with an ACK packet that's with a number `a+1` (that is, I got a, now send a+1)
It also sends its own SYN that's some random number `b`.  
The browser on receipt confirms it has recieved the server `SYN` with an ACK thats with value `b+1` (I got be, send b+1) if sending
anything next. Now the connection is established.
So we move from the establishment phase of the connection to the transfer phase. 

### Data transfer
The browser sends an HTTP Get to the server requesting for the target
resource (over established TCP connection), in this case `file.txt`. 
The server response with an HTTP response code 200, together with the requested data.

## Connection conclusion
Data transfer has come to completion without error, the server then initiates termination the tcp connection with
a two way handhshake for http (yes, we'll use http for simplicity).
It sends FIN packet (I am done, closing connection) plus an ACK acknowledging the last send SYN.
The client responds with a FIN and ACK too. The FIN says it's done too and the ACK acknoledges it received the FIN.


That's an overview for what's going on behind the scenes for each connection that's made to download a file.



What can we learn from this?

As a layman, outside developer work, there's something to learn about how to have faster data transfers. If you have a folder with 1000 small files that you would like moved over to some other disk (not another folder since that works differently), archive them (archive them, not compress, yes , the two are different) and move the archive over. It will be a whole lot faster.

If you are downloading files over the internet and have means to control in what format information is sent over to you from the server side, opt into having it sent to you as one blob other than as tiny split up files.

As someone making websites, there's a lot to learn as well since for large sites, there's a whole lot of 'smaller files' that have to be downloaded to the User's client to have the site functional. To reduce the overhead and give the user a seamless browser experience, it helps to among other things ... 


What happens when you download a file over a network?




TCP/IP
Bandwidth
Throughput
Network Congestion
MTU
The OSI model and names of data at every level: frame, packet, etc


Live experiment
-


Next article: Why copying small files takes longer than copying one file of same size as total for all
small files'

Refs I consumed for this article:
 - https://with.raidrive.com/t/very-slow-download-speed-with-small-files/3423/4'
 - https://serverfault.com/questions/9742/which-is-faster-and-why-transferring-several-small-files-or-few-large-files
 - https://www.youtube.com/watch?v=4UZIwM7tnVk
 - https://en.wikipedia.org/wiki/Download
 - https://medium.com/@olalekanamoo128/throughput-bandwidth-iops-and-latency-understanding-file-transfer-over-a-network-186392e29b58
 - https://aws.amazon.com/what-is/latency/
 - https://developer.mozilla.org/en-US/docs/Web/Performance/Guides/How_browsers_work
 - https://www.youtube.com/watch?v=F27PLin3TV0
 - https://www.rfc-editor.org/rfc/rfc9293.html
 - https://osqa-ask.wireshark.org/questions/17156/large-rtt-or-packets-lost-factorswhich-affects-tcp-performance-most/