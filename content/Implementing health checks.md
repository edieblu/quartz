---
tags:
  - ✅
published: true
sr-due: 2026-01-31
sr-interval: 558
sr-ease: 250
---

⬅️ [[AWS]]
🔗 from [here](https://aws.amazon.com/builders-library/implementing-health-checks/)
- Services can be designed with all kinds of reliability and resiliency built in, but in order to be reliable in practice, they must also deal with predictable failures when they occur.

## Health check tradeoffs 
- Health checks are a way of asking a service on a particular server whether or not it is capable of performing work successfully.
- one of the challenges of building a good health check is to guard carefully against false positive (this means that the automation surrounding health checks should stop directing traffic to a single bad server but keep allowing traffic if the entire fleet appears to be having trouble)

## Ways to measure health 

- **Liveness checks** (test the basic connectivity to a service and the presence of a server process, often performed by LB), for example: Tests that perform a basic HTTP requests and make sure that the server responds with a 200 status code.
- **Local health checks** (check test resources that are not shared with the server’s peers: inability to write to or read from disk, critical processes crashing or breaking)
- **Dependency health checks** (the ability to interact with its adjacent system: bad configuration or stale metadata, inability to communicate with peer servers or dependencies)
- **Anomaly detection** (check if if any server is behaving oddly compared to its peers: clock shew due to server overload, old code due to server running for a long time)

