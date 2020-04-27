#  Load Balancer and High Availability Guide

This guide will help you to understand whats is load balancing and high avaibility, as well to setup a real enviroment, but first we need the boring stuff before we can go with the pratical guide.


## So what is High Availability ?

In our daily life there are some services that cannot stop, such as banks, social services, hospitals, youtube xD. Imagine the day you go to an atm and you cannot withdraw money.
The term High Availability refers to a system that is designed to avoid loss of service. 

To achive this we need to:

- Eliminate single points of failure. we can do this by adding redundancy.

- Network redundancy

- Detect failures. 


## So how about Load balancing ?

Load balancing refers to the process of distributing tasks across a group of servers, also known as a server farm or server pool.

A load balancer acts as the “traffic cop” 👮 sitting in front of our servers ( frontend ) and routing client requests across our pool ( multiple servers ) capable of fulfilling those requests in a manner that maximizes speed and capacity and ensures that no server is overload. 

In this manner, a load balancer allow us to:

- Distributes client requests or network load efficiently across ou pool of servers. 
- Ensures high availability and reliability.
- Provides the flexibility to add or removes servers as demand.


## Load Balancing Algorithms

Different load balancing algorithms provide different benefits; the choice of load balancing method depends on your needs:

- Round Robin – Requests are distributed across the group of servers sequentially. 

- Least Connections – A new request is sent to the server with the fewest current connections to clients. The relative computing capacity of each server is factored into determining which one has the least connections.

- Hash – Distributes requests based on a key you define, such as the client IP address or the request URL.

- IP Hash – The IP address of the client is used to determine which server receives the request.

- Random with Two Choices – Picks two servers at random and sends the request to the one that is selected by then applying the Least Connections algorithm.


## Tools

So what tools do we need to achive all of this, my suggestion ? HAproxy and keepalived, both of these tools are stable, have updates every now and then and are opensource 💰💰💰

- keepalived  - gives you high avaibility.
- haproxy     - gives you high avaibility  and load balancing. 

Hold up, wait a minute, something not right. HAproxy can accomplish both.


<p align="center">
  <img width="460" height="300" src="./imgs/well_yes_but_actually_no.gif">
</p>


In reality, HAproxy only offers load balancing and high availability in our server pool, but the service itself is a single point of failure. We can mitigate this problem using keepalived.

So if just need high availability we can use keepalived.

## Example

Lets assume we have  a website that cannot have downtime.


|       Hostname      |       IPv4          |
| ------------------- | ------------------- |
|  webserver01        |  192.168.1.2        |
|  webserver02        |  192.168.1.3        |

Where webserver's have a website that cannot have downtime, and haproxy 
