## System Design Concepts

### Network Protocols

Network protocols are the rules that govern communications between computers on a given network. 

The **Internet Protocol(IP)** is the base protocol of the internet. It specifies how communications across the internet is implemented. IP messages are communicated in _packets_(small bundles of information) which contain a _header_ and _data_. The header contains metadata(source, destination, size, etc.) about the packet and it's data. An IP address is assigned every computer connected to a network that uses the Internet Protocol for communication.

The **Transmission Control Protocol(TCP)** is higher level utility protocol built on top of `IP`. Among other things, it guarantees that packets are delivered in the same order as they were sent.

The **Hypertext Transfer Protocol** is built on top of TCP. It uses a request-response pattern for client-server communication. A client requests information and a server provides it. Clients can be browsers(and other user agents) or another web server. 

_TODO: Read more on TCP/IP, HTTP, WebSockets, RPC_

### Latency and Throughput

**Latency** is the measure of delay. It is the time that between an action and a response. Good systems have low latency. Factors that affect network latency include: The time it takes the server to process the request, and distant between client and server.

**Throughput** is the number of items that can be processed per unit of time. E.g., if a web server receives 10k requests a second, and it can only process 5k. Then it's throughput is 5k requests per second.
Good systems have high throughput.

**Caching** involves using an in-memory data store to hold data that is read frequently but doesn't change often. Cached data is faster to retrieve than data stored on disk. This helps to reduce latency.

_TODO: Read more about web performance, and system availability_

### Proxies and Load Balancers

A **proxy(or forward proxy)** is server that makes requests on behalf of a client. It may hide the IP address of the client from the server. This is the principle on which VPNs operate.

A **reverse proxy** acts on behalf of the server. It intercepts all incoming requests before they can be dispatched to the server itself. The client usually do not know they are interacting with a proxy. If configured properly, reverse proxies can be useful for security and monitoring among other things.

Using a cluster of servers to handle client requests reduces latency, increases throughput and improves reliability of the whole system. This strategy is called _horizontal scaling_. A **load balancer** efficiently distributes network traffic across all the servers in a cluster. This ensures no server is overworked. Strategies for load balancing include: 

- _Round Robin_: Loop through available servers in a fixed sequence.
- _IP Hashing_:  Select server based on hash of IP address of client.
- _Path or Service_: The server selected depends on the URL path or web service requested.

### How To Approach Design Questions

1. Understand the problem, gather requirements and constraints
    - What the system does and how it will be used.
    - Estimated number of requests per second.
    - Expected read to write ratio.
    - Input and output data.
    - Etc.

2. Create a high level design
    - Decide on the major components that are needed.

3. Design each major components
    - Schema for relational databases.
    - API endpoints for services.
    - Etc.

4. Scale the design
    - Caches.
    - Database indexes.
    - Load balancers.
    - Server clusters.
    - Etc.

IMPORTANT: Study sample designs: [SYSTEMS DESIGN](https://github.com/donnemartin/system-design-primer#how-to-approach-a-system-design-interview-question)
