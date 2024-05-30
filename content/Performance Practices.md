---
tags:
  - ✅
published: true
sr-due: 2024-08-28
sr-interval: 97
sr-ease: 280
---
⬅️ [[NodeJS Best Practice]]
🔗 [GH](https://github.com/goldbergyoni/nodebestpractices?tab=readme-ov-file#7-draft-performance-best-practices)

- Don't block the event loop: Avoid CPU intensive tasks as they will block the mostly single-threaded Event Loop and offload those to a dedicated thread, process or even a different technology based on the context.
- Prefer native JS methods over user-land utils like Lodash


> [!NOTE] 
>
> "Here's a good rule of thumb for keeping your Node server speedy: Node is fast when the work associated with each client at any given time is 'small'."

Checkout [Node Clinic](https://clinicjs.org/documentation/).