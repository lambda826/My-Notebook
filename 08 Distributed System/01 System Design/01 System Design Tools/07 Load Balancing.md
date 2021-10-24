# Load Balancer
![01 Load Balance](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/01%20System%20Design%20Tools/resource/load%20balance/01%20Load%20Balance.png)

![02 Load Balance](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/01%20System%20Design%20Tools/resource/load%20balance/02%20Load%20Balance.png)


# Load Balancing Algorithms
## Health Checks
- To monitor the health of a backend server, “health checks” regularly attempt to connect to backend servers to ensure that servers are listening.
- If a server fails a health check, it is automatically removed from the pool, and traffic will not be forwarded to it until it responds to the health checks again.

## Balancing Algorithms
- Round Robin
	- This method cycles through a list of servers and sends each new request to the next server.
	- When it reaches the end of the list, it starts over at the beginning.
	- It is most useful when the servers are of equal specification and there are not many persistent connections.
- **Weighted Round Robin**
	- The weighted round-robin scheduling is designed to better handle servers with different processing capacities.
	- Each server is assigned a weight (an integer value that indicates the processing capacity).
	- Servers with higher weights receive new connections before those with less weights and servers with higher weights get more connections than those with less weights.
- Least Connection
	- This method directs traffic to the server with the fewest active connections.
	- This approach is quite useful when there are a large number of persistent client connections which are unevenly distributed between the servers.
- Least Response Time
	- This algorithm directs traffic to the server with the fewest active connections and the lowest average response time.
- Least Bandwidth
	- This method selects the server that is currently serving the least amount of traffic measured in megabits per second (Mbps).
- IP Hash
	- Under this method, a hash of the IP address of the client is calculated to redirect the request to a server.

## Session Persistence
Refers to directing a client’s requests to the same backend web or application server for the duration of a “session” or the time it takes to complete a task or transaction.


# Redundant Load Balancers
![03 Redundant Load Balancer](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/01%20System%20Design%20Tools/resource/load%20balance/03%20Redundant%20Load%20Balancer.png)
- The load balancer can be a single point of failure; to overcome this, a second load balancer can be connected to the first to form a cluster.
- Each LB monitors the health of the other and, since both of them are equally capable of serving traffic and failure detection, in the event the main load balancer fails, the second load balancer takes over.


# Load Balancing and SSL
Secure Sockets Layer (SSL) is the standard security technology for establishing an encrypted link between a web server and a browser.
- SSL traffic is often decrypted at the load balancer.
	- When a load balancer decrypts traffic before passing the request on, it is called SSL termination.
	- The load balancer saves the web servers from having to expend the extra CPU cycles required for decryption.
	- This improves application performance.
- However, SSL termination comes with a security concern.
	- The traffic between the load balancers and the web servers is no longer encrypted.
	- This can expose the application to possible attack.
	- However, the risk is lessened when the load balancer is within the same data center as the web servers.
- Another solution is the SSL pass-through.
	- The load balancer merely passes an encrypted request to the web server.
	- Then the web server does the decryption.
	- This uses more CPU power on the web server.
	- But organizations that require extra security may find the extra overhead worthwhile.


# Software Load Balancers vs. Hardware Load Balancers
## Software vs. Hardware

![04 Software Load Balancers vs. Hardware Load Balancers](https://raw.githubusercontent.com/lambda826/My-Notebook/master/08%20Distributed%20System/01%20System%20Design/01%20System%20Design%20Tools/resource/load%20balance/04%20Software%20Load%20Balancers%20vs.%20Hardware%20Load%20Balancers.png)

## DNS Load Balancing vs Hardware Load Balancing
- DNS load balancing is a software-defined approach to load balancing where client requests to a domain within the Domain Name System (DNS) are distributed across different server machines.
	- The DNS system sends a different version of the list of IP addresses each time it responds to a new client request using the round-robin method, therefore distributing the DNS requests evenly to different servers to handle the overall load.
	- This in turn provides DNS load balancing failover protection through automatic removal of non-responsive servers.
- DNS load balancing differs from hardware load balancing in a few instances, although both can be a very effective solution for distributing traffic.
	- One main advantage of DNS level load balancing is the scalability and price.
	- A DNS load balancer distributes traffic to several different IP addresses, whereas the hardware solution uses a single IP address and splits traffic leading to it on multiple servers.
	- As for pricing, hardware load balancers require a large upfront cost whereas DNS load balancers can be scaled as needed.


## Types of Load Balancing

- SDN — Load balancing using [SDN (software-defined networking)](https://avinetworks.com/glossary/sdn-load-balancing/) separates the control plane from the data plane for application delivery.
- This allows the control of multiple load balancing. It also helps the network to function like the virtualized versions of compute and storage.
- With the centralized control, networking policies and parameters can be programmed directly for more responsive and efficient application services.
- This is how networks can become more agile.

- UDP — A UDP load balancer utilizes User Datagram Protocol (UDP).

- [UDP load balancing](https://avinetworks.com/glossary/udp-load-balancer/#:~:text=A%20UDP%20load%20balancer%20is,the%20internet%20protocol%20(IP).) is often used for live broadcasts and online games when speed is important and there is little need for error correction.
- UDP has low latency because it does not provide time-consuming health checks.

- TCP — A TCP load balancer uses transmission control protocol (TCP).

- [TCP load balancing](https://avinetworks.com/glossary/tcp-load-balancing/) provides a reliable and error-checked stream of packets to IP addresses, which can otherwise easily be lost or corrupted.

- SLB— Server Load Balancing (SLB) provides network services and content delivery using a series of load balancing algorithms.

- It prioritizes responses to the specific requests from clients over the network.
- [Server load balancing](https://avinetworks.com/glossary/server-load-balancer/) distributes client traffic to servers to ensure consistent, high-performance application delivery.

- Virtual

- Virtual load balancing aims to mimic software-driven infrastructure through virtualization.
- It runs the software of a physical load balancing appliance on a virtual machine.
- [Virtual load balancers](https://avinetworks.com/glossary/virtual-load-balancer/), however, do not avoid the architectural challenges of traditional hardware appliances which include limited scalability and automation, and lack of central management.

- Elastic

- [Elastic Load Balancing](https://avinetworks.com/glossary/elastic-load-balancer/) scales traffic to an application as demand changes over time.
- It uses system health checks to learn the status of application pool members (application servers) and routes traffic appropriately to available servers, manages fail-over to high availability targets, or automatically spins-up additional capacity.

- Geographic

- Geographic load balancing redistributes application traffic across data centers in different locations for maximum efficiency and security.
- While local load balancing happens within a single data center, [geographic load balancing](https://avinetworks.com/glossary/geographic-load-balancing/) uses multiple data centers in many locations.

- Multi-site

- Multi-site load balancing, also known as global server load balancing (GSLB), distributes traffic across servers located in multiple sites or locations around the world.
- The servers can be on-premises or hosted in a public or private cloud.
- [Multi-site load balancing](https://avinetworks.com/glossary/multi-site-load-balancing/) is important for quick disaster recovery and business continuity after a disaster in one location renders a server inoperable.

- Load Balancer as a Service (LBaaS)

- Load Balancer as a Service (LBaaS) uses advances in load balancing technology to meet the agility and application traffic demands of organizations implementing private cloud infrastructure.
- Using an as-a-service model, [LBaaS](https://avinetworks.com/glossary/load-balancing-as-a-service/) creates a simple model for application teams to spin up load balancers.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNzk4NDkwOF19
-->