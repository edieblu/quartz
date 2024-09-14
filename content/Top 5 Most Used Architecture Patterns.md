---
published: true
tags:
  - ✅
sr-due: 2024-11-02
sr-interval: 178
sr-ease: 280
---

 ⬅️[[Architecture]]
🔗 [YT](https://www.youtube.com/watch?v=f6zXyq4VPP8)

## 1. Layered Architecture
- separate the components of a system into distinct layers (presentation layer, business layer, persistence layer, database layer...)
- MVP is an example of that too
![[Pasted image 20230911092206.png]]
- promotes separation of concerns (so changes in one layer don't affect another layer)
- provides abstraction and encapsulation

## 2. Event-Driven Architecture
- loosely coupled software components and services
- components broadcast events when something happens, other components subscribe to the events they are interested in (pub-sub model)
![[Pasted image 20230911092359.png]]
- highly decoupled 
- example:
![[Pasted image 20230911092518.png]]

## 3. Micro-Kernel Architecture
- separates core system functionalities, into small micro kernels (add-ons, plugins)
- e.g. OS components
![[Pasted image 20230911092655.png]]

## 4. Microservices Architecture
- the application is broken down into a collection of small, loosely coupled services
- e.g. Netflix
- services can be developed, deployed and scaled independently
- tradeoff: added complexity in intra-service communication and maintaining data consistency
![[Pasted image 20230911092852.png]]

## 5. Monolithic Architecture
- simplifies development and deployment (go-to for startups and smaller applications)
![[Pasted image 20230911093043.png]] 
- on the rise is the modular monolith
- still single deployable unit but with modular boundaries
![[Pasted image 20230911093153.png]]