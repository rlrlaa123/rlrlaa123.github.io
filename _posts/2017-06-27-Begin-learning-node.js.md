---
layout: post
title: Begin Learning Node.js
subtitle: What is Node.js?
image: https://upload.wikimedia.org/wikipedia/commons/thumb/d/d9/Node.js_logo.svg/1200px-Node.js_logo.svg.png
---

###### It's been such a long time I posted on my blog. Recently, I started studying Node.js, trying to build a web server with it. Even though I was more interested in learning django-rest-framework, my friend suggested me to learn functional languages so that I can write codes more efficiently. I'm not fully understood about why it is more efficient, it looked simpler than object-oriented languages. And it looked interesting!

I referenced this [blog](https://velopert.com/133) to learn *node.js*, it seemed like the blogger beautifully arranged essential parts very simply with small example codes.

### What is Node.js?
NodeJS is a server-side platform based on Google Chrome's *javascript* engine (V8 Engine). It was developed by Ryan Dahl in 2009.
One thing we need to remember is that *Node* is not a web server. It is more like a method to run *javascript* codes. *Node* itself do not have any functions to build web server, we need to build all the server with *javascript* and then run it with *Node*.

### Feature of Node.js
* Asynchronous I/O Handling / Event-Driven: All the API of *Node.js*'s library is asynchronous. It means it does not stop(Non-blocking). When *Node.js*-based API runs, it does not wait until the data is returned, it runs the next API. And if the previous API returns the result, it will receive result using *NodeJS*'s event listenter mechnaism.
* Fast Speed: It supports fast code run using Google Chrome's V8 *javascript* engine.
* Single Thread / Outstanding Scalability: *Node.js* uses single thread model with event loop. Event mechanism increases scalability by not letting the server stop. Meanwhile, usual webserver(*Apache*) creates limited number of thread in order to handle response. *Node.js* uses only one thread,but handle more responses than web server like *Apache*.
* No Buffering: *Node.js* application does not have data buffering, it prints data in a chunk.
* License: *Node.js* has MIT License.

### Where to use Node.js
* Frequent I/O Application
* Data Streaming Application
* Real-time Data Handling Application
* JSON API based Application
* Single Page Application

### Where to **not** use Node.js
* High CPU usage application
