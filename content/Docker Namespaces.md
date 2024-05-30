---
tags:
  - ✅
published: true
sr-due: 2025-09-28
sr-interval: 493
sr-ease: 250
---

⬅️ [[FEM Docker]]
#✅ 
- Namespaces allow you to hide processes from other processes (with `chroot` you only protect the file system)
- `deboostrap` helps you create new `chroot` environments faster (without manually copying each binary) (`apt-get install debootstrap -y`)
- `debootstrap --variant=minbase bionic /better-root`
- `unshare` creates a new isolated namespace from its parent: `unshare --mount --uts --ipc --net --pid --fork --user --map-root-user chroot /better-root bash`
- so the host will be able to see the child's processes, but the child won't be able to see outside of itself