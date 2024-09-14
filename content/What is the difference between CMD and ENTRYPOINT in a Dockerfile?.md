---
tags:
  - ✅
sr-due: 2024-10-01
sr-interval: 31
sr-ease: 270
---

⬅️ [[Docker]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/21553353/what-is-the-difference-between-cmd-and-entrypoint-in-a-dockerfile)

- Docker has a default entrypoint which is `/bin/sh -c` but does not have a default command.
- When you run docker like this: `docker run -i -t ubuntu bash` the entrypoint is the default `/bin/sh -c`, the image is `ubuntu` and the command is `bash`

- the `ENTRYPOINT` specifies a command that will always be executed when the container starts.
- The `CMD` specifies arguments that will be fed to the `ENTRYPOINT`

