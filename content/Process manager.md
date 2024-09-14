---
tags:
  - ✅
published: true
sr-due: 2025-09-27
sr-interval: 488
sr-ease: 250
---

⬅️ [[FullStack for front end dev (Jem Young)]]
## Process manager
- Keeps your application running
- Handles errors and restarts
- Can handle logging and clustering

![[Pasted image 20211008082047.png]]

```bash

# installs pm2 process manager globally
sudo npm i -g pm2

pm2 start app.js
pm2 save
pm2 startup
```