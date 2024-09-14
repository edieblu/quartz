---
tags:
  - ✅
sr-due: 2026-04-25
sr-interval: 611
sr-ease: 250
---

⬅️ [[FEM Docker]]
### Why [[Containers]]?
- Managing your own servers is hard and requires a whole team to do it.

### Virtual Machines
- Virtual machines add a layer of abstraction between you and the metal (instead of having one instance of Linux running on your computer, you'll have multiple guest instances of Linux running inside of a host instance of Linux)
- The host operating system offers the VM a certain amount resources and if that VM runs out, they run out and they don't affect other guest operating systems running on the server. 
- If they crash their server, they crash their guest OS and yours hums along unaffected. 
- And since they're in a guest OS, they can't peek into your files because their VM has no concept of any sibling VMs on the machine so it's much more secure.
- All these above features come at the cost of a bit of performance.

#### In the cloud
- You can get a VM from a public cloud (it will come with a pre-allocated amount of memory and computing power)
- the hard part is they're still just giving you machines, you have to manage all the software, networking, provisioning, updating, etc. for all these servers (tools like: Terraform, Chef, Puppet, Salt would help with that)

🤔 What does **provisioning** mean?
Provisioning is the process of setting up IT infrastructure. It can also refer to the steps required to manage access to data and resources, and make them available to users and systems. 

Provisioning is not the same thing as configuration, but they are both steps in the deployment process. Once something has been provisioned, the next step is configuration. 

When the term "provisioning" is used, it can mean many different types of provisioning, such as server provisioning, network provisioning, user provisioning, service provisioning, and more.

### In conclusion
- Containers give us many of the security and resource-management features of VMs but without the cost of having to run a whole other operating system.
- A container instead uses **chroot**, **namespace**, and **cgroup** to separate a group of processes from each other.