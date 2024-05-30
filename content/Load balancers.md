---
tags:
  - ✅
published: true
sr-due: 2025-09-21
sr-interval: 489
sr-ease: 250
---
⬅️ [[FullStack for front end dev (Jem Young)]]
⬅️ [[Architecture Notes]]
⬅️ [[AWS]]

- A load balancer routes the traffic to the right cluster

They work on a scheduling algorithm :

- Round Robin* (tends to be the default)
- IP Hashing (based on your IP address)
- Random Choice
- Least Connections
- Least Load

You can use nginx as a load balancer too!

## From 🔗[ Architecture Notes](https://architecturenotes.co/load-balancers/)x
- load balancers usually come into play once we scale beyond one server being able to serve requests reliably.

Load balancers are also responsible for how that load is distributed across the pool.

1. Round Robin - Requests are distributed one at a time to each server.
2. IP Hashing - The IP address of the client is hashed and pinned to a specific server which handles the request. Useful in environments where session persistence or pinning to specific servers is essential.
3. Least load - Requests are distributed to the downstream server with the least concurrent connections.

There are several benefits to introducing load balancers into your system but not limited to the following:

1. Reduced downtime
2. Scalability
3. Redundancy
4. Flexibility
5. Efficiency

Load balancers (LB) are divided into two groups **Layer 4** or **Layer 7.** Layer 4 LBs can only act on data found in the transport and network layers like IP and TCP. While Layer 7 LBs can distribute requests based on data found in the application layer, like HTTP, which can allow you to do fancy things like siphon traffic to your new service.

Certain types of load balancers are aware of server "health" and their current availability status; if they are performing less than ideally, LBs can take action (failover).