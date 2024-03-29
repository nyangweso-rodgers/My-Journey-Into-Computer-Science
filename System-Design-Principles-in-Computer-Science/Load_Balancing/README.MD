# Load Balancing

## Table Of Contents
- [Introduction to Load Balancing](#Introduction-to-Load-Balancing)
- [Benefits of a load balancer](#Benefits-of-a-load-balancer)
- [How Do Load Balancer Works?](#How-Do-Load-Balancer-Works?)

# Introduction to Load Balancing
* A __load balancer__ sits in front of various servers and acts as a traffic cop to direct traffic to the right server. It makes sure that no server is overloaded, and provides high availability and reliability by ensuring all requests are served. If a server goes down, it starts redirecting the requests to different servers that are online.

# Benefits of a load balancer
* Faster user experience
* Less downtime and high thorughput. If a particular server is down, LB takes care of routing the traffic to the ones which are up.
* Reduces individual server load and prevents any one application server from becoming a single point of failure.
* Improves response time
* Improves overall system availability.

# How Do Load Balancer Works?
A __load balancer__ can use any of the below __algorithms__ to decide where to route the next incoming request. The __algorithms__ used depend on the use case:

* __Least Connection Method__: Route traffic to the server with the fewest active connections.
* __Least Response Time Method__: Route traffic to the server with the fewest active connections and the lowest average response time.
* __Least Bandwidth Method__: Route traffic to the server that is currently serving the least amount of traffic measured in megabits per second (Mbps)
* __Round Robin__: Routes through a list of servers and sends each new requst to the next server. When it reaches the end of the list, it starts over at the beginning.
* __Weighted Rounded Robin Method__: The weighted round robin scheduling is designed to better handle servers with different processing capacities. Each server is assigned a weight (an integer that indicates the processing capacity). Servers with higher weights receive new connections before those with less weight and servers with higher weights get more connections than those with less weights.
* __IP Hash__: Under this method, a hash of the IP address of the client is calculated to redirect the request.