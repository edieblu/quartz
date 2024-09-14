---
tags:
  - ✅
sr-due: 2024-10-24
sr-interval: 47
sr-ease: 270
---

⬅️ [[Linux]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/4421633/who-is-listening-on-a-given-tcp-port-on-mac-os-x)

```
sudo lsof -i -n -P | grep TCP
```

For a specific port
```
lsof -i :PORT_NUMBER
```