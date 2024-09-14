---
published: true
tags:
  - ✅
sr-due: 2025-07-27
sr-interval: 446
sr-ease: 250
---
⬅️ [[FEM Docker]]

- if I have two containers running at the same time  how do they talk to each other?
- run `docker network ls` to checkout the default networks

```bash
docker network create --driver=bridge app-net

# then start a mongodb server
docker run -d --network=app-net -p 27017:27017 --name=db --rm mongo:3
```