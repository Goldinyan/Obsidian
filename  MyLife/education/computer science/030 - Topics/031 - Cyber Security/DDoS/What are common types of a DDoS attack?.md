---
id: What are common types of a DDoS attack?
aliases:
Topic:
Related:
Tags:
  - w
Date:
Updated:
Source: https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/
---
# What are common types of a DDoS attack?

There are different types of DDoS attacks, which target different components of a network connection. In order to understand how these different DDoS, it is necessary to know how a [[Network Connection]] is made.

In short: 
A network connection on the Internet is composed of many different components or "layers". Like building a house from the ground up, each layer in the model has a different purpose.

##### 7. APPLICATION LAYER: 
Human-computer interaction layer, where applications can access the network services.
##### 6. PRESENTATION LAYER:  
Ensures that data is in a usable format and is where date encryption occurs. 

##### 5. SESSION LAYER:
Maintains connections and is responsible for controlling ports and sessions.

##### 4. TRANSPORT LAYER: 
Transmits data using transmission [[Protocol]] including [[TCP]] and [[UDP]].

##### 3. NETWORK LAYER: 
Decides which physical path the data will take.

##### 2. DATA LINK LAYER:
Defines the format of data on the network.

##### 1: PHYSICAL LAYER:
Transmits raw bit streams over the physical medium.

While nearly all DDoS attacks involve overwhelming a target device or network with traffic, attacks can be divided into three categories. An attacker may use one or more different attack vectors, or cycle attack vectors in response to counter measures taken by the target.

## Application layer attacks

The goal of the attack consist of exhausting the target's resources to create a denial-of-service. This is sometimes referred to as a **layer 7** DDoS attack.

The attacks target the layer where web pages are generated on the server and delivered in response to HTTP request. A single HTTP request is computationally cheap to execute on the client side, but it can be expensive for the target server to respond to, as the server often loads multiple files and runs database queries in order to create a web page.

Layer 7 attacks are difficult to defend against, since it can be hard to differentiate malicious traffic from legitimate traffic.

#### HTTP flood

This attack has many similiarities to refreshing in a web browser over and over on many different computers at once, large numbers of HHTP request flood the server.

This type of attack can range from very simple to being  complex.

Simpler implementations may access one URL with the same range of attacking IP addresses, referrers and user agents. Complex versions may use a large number of attacking IP addresses, and target random urls using random referrers and user agents.


