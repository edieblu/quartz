---
published: true
tags:
  - ✅
sr-due: 2025-09-30
sr-interval: 495
sr-ease: 250
---
⬅️ [[FullStack for front end dev (Jem Young)]]
## Nginx Config

**Redirects (instead of using express)**

```bash
# 301 is permanent redirect
# 302 is temp redirect
location /help {
return 301 https://developer.mozilla.org/en-US/;
}
```

**Adding a subdomain**

```bash
server {
        listen 80;    
listen [::]80; # IPV6 notation

       server_name test.jemisthe.best;

        location / {
           proxy_pass http://localhost:3000;
          }
}
```

**File compression**
![[Pasted image 20211009130643.png]]