#  Load Balancer and High Availability Guide

This guide will help you to understand whats is load balancing and high avaibility is as well to setup a real envirement, but first we need the boring stuff before we go with the pratical guide

## So what is High Availability ?

## So what is Load balancing ?

Load balancing refers to efficiently distributing incoming network traffic across a group of backend servers, also known as a server farm or server pool 

A load balancer acts as the “traffic cop” 👮 sitting in front of your servers ( also know as frontend ) and routing client requests across our pool ( multiple servers ) capable of fulfilling those requests in a manner that maximizes speed and capacity and ensures that no server enter in overload. 

In this manner, a load balancer allow us to:

- Distributes client requests or network load efficiently across ou pool of servers 
- Ensures high availability and reliability
- Provides the flexibility to add or removes servers as demand  


## Load Balancing Algorithms

Different load balancing algorithms provide different benefits; the choice of load balancing method depends on your needs:

- Round Robin – Requests are distributed across the group of servers sequentially. 

- Least Connections – A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.

- Hash – Distributes requests based on a key you define, such as the client IP address or the request URL.

- IP Hash – The IP address of the client is used to determine which server receives the request.

- Random with Two Choices – Picks two servers at random and sends the request to the one that is selected by then applying the Least Connections algorithm.



For this you will need at least 4 server's, where

- haproxy01
- haproxy02
- webserver01
- webser02

The first two will guarantee that your service can run smootly, 
