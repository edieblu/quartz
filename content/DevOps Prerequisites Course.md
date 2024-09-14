---
tags:
  - ✅
published: true
sr-due: 2025-11-21
sr-interval: 693
sr-ease: 250
---
⬅️ [[DevOps]]
 
- 🔗 [this YT tutorial](https://www.youtube.com/watch?v=Wvf0mBNGjXY)
- 🔗 [kodekloud](https://kodekloud.com/courses/labs-devops-pre-requisite-course/)GBP 17.10GBP/m

Where to get pre-configured images for Virtual box: [osboxes](https://www.osboxes.org/) 

## Guest vs host?
- host is your host machine, your laptop
- guest is the VM (e.g. virtualbox)

## What does Vagrant do (compared to Virtual Box)
- download
- create VM
- create networks (NAT, NAT-network, host-only, bridged)
- configure networking 
- configure port forwarding (aka making your computers a server so that the VM box can for example access the internet through it)
- boot up VM

Vagrant is useful for more complex systems involving multiple VMs
Browse existing Vagrant boxes on Vagrant cloud

## DNS
- local solution: inside `/etc/hosts` you can give IP addresses specific names (aka name resolution)
- remote solution: the DNS server manages this for all - resolving hostname to an ip address (inside `/etc/resolv.conf`)

### Record types
- A: IP to name
- AAAA: IPv6 to name
- CNAME: alias to name

![[Pasted image 20220917165953.png]]

🤔 What is a router?
- A device that connects different networks

🤔 What is the loopback address (aka home)
- Every host has this built-in virtual interface available
- aka `127.0.0.1`
- aka `localhost`

## YAML
![[Pasted image 20220918162250.png]]
- for dictionaries you have to always have the same number of spaces
- lists are ordered
- hash for comments