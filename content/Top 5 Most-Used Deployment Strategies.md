---
tags:
  - ✅
published: true
sr-due: 2025-01-22
sr-interval: 285
sr-ease: 250
---
⬅️ [[DevOps]]

🔗 [YT](https://www.youtube.com/watch?v=AWVTKBUnoIg)

## 1. Big Bang Deployment
- like ripping of the band-aid
- we push all of our changes at once which causes a bit of downtime
- needs to have a solid rollback plan
![[Pasted image 20230830085702.png]]

## 2. Rolling Deployment
- update incrementally (aka staged roll-out)
- for example if we have 10 servers running our code, we update a server one at a time
- no downtime
- you can spot and mitigate any issues early during the rollout
- it's generally a slower process
	- doesn't support targeted rollouts
![[Pasted image 20230830085827.png]]

## 3. Blue-Green Deployment
- we maintain two identical production systems (one is active and visible to the users, the other is idle)
- the blue is live and the green is our playground where we can test our new version
- when ready, we switch the users to the green deployment (with a load balancer)
- no downtime
- easy rollback
- there's no targeted rollout, all users switched at once
- resource intensive - doubles our prod environment
![[Pasted image 20230830090157.png]]

## 4. Canary Deployment
- deploy your change to a subset of the servers/users
- easy rollbacks
- targeted rollouts (can be user-specific: geographical area or device type)
- somewhat complex (especially when db migrations or API compatibility are involved)
![[Pasted image 20230830090630.png]]
Often combined with rolling deployment
![[Pasted image 20230830090921.png]]

## 5. Feature Toggle
- manages specific new features within the application
- can be used in combination with any of the other deployment strategies (e.g. turn the feature toggle on for just the canary users)
- great for a/b testing or gradual roll-outs
- but toggles can add complexity and make testing more difficult
- make sure to clean-up to prevent toggle debt!