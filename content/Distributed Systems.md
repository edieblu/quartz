---
tags:
  - ✅
sr-due: 2025-07-03
sr-interval: 431
sr-ease: 250
---

⬅️ [[Everything programming]]
➡️ [[What are Microservices?]]
➡️ [[What is a CDN?]]
➡️ [[What is Infrastructure as Code]]

- from [Arc Notes](https://architecturenotes.co/fallacies-of-distributed-systems/)

# Fallacies of Distributed Systems

Fallacies of distributed systems are a set of assertions made by L Peter Deutsch and others at Sun Microsystems describing false assumptions that programmers new to distributed applications invariably make.

![[Pasted image 20230718082338.png]]

## 1. The Network is reliable

- To build a reliable system, you have to understand and come to terms with the fact that any particular communication can fail; Therefore, we need to provide a way for systems to deal with this potential miscommunication (e.g. store and forward with RabbitMQ and ActiveMQ)

## 2. Latency is zero
- There is overhead to get any request done. Message can be large, or it can be small, and latency is unchanged. Unlike bandwidth, latency usually has to do with the speed of light and the communication distance (or path). So the distance between the two systems plays a significant role here.
- Content delivery networks and edge computing are essentially trying to make the distance between the fridge and trunk as close as possible. By duplicating the data closer to where it is needed we significantly reduce latency.

## 3. Bandwidth is infinite
- Assuming that you continue to increase data size on a channel without limit; can be quite the mistake. This problem only turns its head when scale difficulties enter the conversation, and specific communication channels hit their limits.

## 4. The network is secure
- Taking a security-first stance when designing your systems will reap dividends in the future.

## 5. Topology doesn't change
- Building systems that can react to these change in topology can be tricky, but ultimately result in much more resilient system (Docker and Kubernetes help!)

## 6. There is one administrator
- As your systems grow, they will rely on other systems outside your control.
- It's essential to have a clear way of managing your systems and their respective configurations. As the number of systems with various configuration increases it becomes hard to manage and track. Infrastructure as Code (IaC) can help codify those variations in your systems.

## 7. Transport cost is zero
- as systems grow, that cost may be worth optimizing message formats like JSON can be a bit heavy (pun intended) compared to transfer optimized formats like gRPC or MessagePack.

## 8. The network is homogeneous
- We like everything to be clean and tidy, but the real world is far from it. Being interoperable is essential.