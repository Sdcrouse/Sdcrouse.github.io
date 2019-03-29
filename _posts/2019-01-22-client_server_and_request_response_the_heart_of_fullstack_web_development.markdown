---
layout: post
title:      "Client/Server and Request/Response: The Heart of Fullstack Web Development"
date:       2019-01-22 01:59:54 -0500
permalink:  client_server_and_request_response_the_heart_of_fullstack_web_development
---


### **Introduction**

When I started Flatiron's Bootcamp Prep, I found out that I would be learning Fullstack web development, which combines Front-End and Back-End web development. With Front-End, you learn languages like HTML and Javascript; with Back-End, you learn Ruby, SQL, and other languages. But one question has been nagging me in the back of my mind for quite some time: *How exactly do Front-End and Back-End web development WORK together?* The answer, as it turns out, is in the interaction between the client and the server, and in the request/response cycle. This is the very HEART of Fullstack web development! 

### The client/server model and the request/response cycle

Here's what I mean by client/server and request/response. Whenever you want to access a website on the Internet, you just type in the URL (Uniform Resource Locator), press Enter, and **BOOM** you're there (usually). But this didn't happen by magic, anymore than flipping a switch turns on a light by magic. So what DID happen? Let's break it down step by step. 

Here's how this whole process works:

1. You (the user) type in the URL (such as https://computer.howstuffworks.com/internet/basics/internet.htm) into your web browser and press Enter.
2. *Side Note:* The URL (also called the URI) is composed of three main parts: the protocol (usually http or https), the host (which is computer.howstuffworks.com in the example above), and the path (also called the resource, which is /internet/basics/internet.htm in the example above).
2. The client (your web browser, in this case) creates an HTTP request in the form of a String - in this case, a GET request, which asks a server for data. 
2. *Side Note:* The request is made up of two parts: the request line and the request headers. The request line contains the method/request type (usually GET) and the protocol and path parts of the URL. The request headers include the host, language, cookies, and other metadata.
3. The client sends the request to a DNS (Domain Name System) server, which either translates the URL into an IP address - the address of the requested website - and sends it back to the client, or it asks another DNS server to find the URL's IP address if it doesn't know it. This request for the IP address goes from server to server until either the requested web address is found, or an error status (usually 404 Not Found) is returned.
4. *Side Note:* The way that web browsers and web servers communicate with each other is through HTTP (Hyper Text Transfer Protocol). This protocol is used to access and interact with sites on the World Wide Web, an application built on the Internet. Other protocols are FTP for transferring files, SMTP for e-mails, and TCP/IP for the Internet itself.
5. If the IP address is found, the client then sends its HTTP request to the host web server (where the website is located) at that address.
6. The server then receives and interprets the request and creates a response. It often uses Ruby, Python, SQL, and other languages and their frameworks to do this. (How it actually creates the response involves the use of Models, Views, and Controllers, which will be covered in another blog post.)
7. *Side Note:* The response consists of the response headers and the response body. The headers contain the requested URL, status code (200 if successful), content-length, content-type, and other important metadata. The response body contains the HTML, CSS, and Javascript for the specified webpage.
8. The server sends this response back to the client, which then interprets it and renders the body of the response, translating it into text, sound, and images - the part of the website that we're are all familiar with.
9. *Side Note:* This is only true if the client is a web browser. Other clients are unable to render the response body; command lines in particular will only output it as a string of HTML.
9. Depending on the nature of the response received by the client, it may make additional requests to the server and/or other servers. The server, in turn, may also send back additional responses and/or make requests to other servers, depending on the request that it receives. This is the "cycle" portion of the request/response cycle.



### Front-End and Back-End Web Development

So, how does this all tie in to the connection between Front-End and Back-End web development? Simple: it IS that connection! **Front-End** deals with the **client** side of web development, such as the appearance of the webpage (HTML/CSS) and the different ways you can interact with it (Javascript). **Back-End**, on the other hand, deals with the **server** side, such as receiving the request and creating an HTTP response to send back to the client.

The bottom line is that both Front-End and Back-End are needed for web development; they are two sides of the same coin (Fullstack web development). The request/response cycle and the client/server model illustrate how Front-End and Back-End web development relate to each other. For more information, check out the resources below.


### Resources and Further Reading

* https://flatironschool.com/blog/front-end-vs-back-end-development/
* https://learn.co/tracks/full-stack-web-development-v6/rack/rack-and-the-internet/how-the-internet-works
* https://learn.co/tracks/full-stack-web-development-v6/rack/rack-and-the-internet/video-review-how-the-web-works-pt-1
* https://learn.co/tracks/full-stack-web-development-v6/rack/rack-and-the-internet/video-review-how-the-web-works-pt-2
* https://learn.co/tracks/full-stack-web-development-v6/html-and-css-continued/web-fundamentals/how-the-web-works
* https://computer.howstuffworks.com/internet/basics/internet.htm
* https://www.webopedia.com/DidYouKnow/Internet/Web_vs_Internet.asp
* https://www.webopedia.com/TERM/T/TCP_IP.html
* https://en.wikipedia.org/wiki/List_of_HTTP_status_codes
