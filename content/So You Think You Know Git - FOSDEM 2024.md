---
tags:
  - ✅
published: true
sr-due: 2024-06-16
sr-interval: 20
sr-ease: 250
---
⬅️ [[Git]]

🔗 YT from [here](https://www.youtube.com/watch?v=aolI_Rz0ZqY)

- Scott Chacon: co-found of GitHub, wrote Pro Git book
- there are about 145 git commands in total (some are useless)

![[Pasted image 20240512132800.png]]

## Some helpful config stuff
- `git config --global alias.staash 'stash --all'`
stash --all will stash both tracked/untracked files
## Oldies but goodies
- `git config --global rerere.enabled true`
teach `git` how you resolved a merge conflict last time and it will do it automatically the next time
## Some new stuff you may not have noticed
- `git config --global alias.fpush push --force-with-lease`
it will check that what you last pushed is still what's on the server before it will force the new branch update. If someone has updated the remote ref (pushed in the meantime), then push now fails with a "stale info" error.

- `gc`: disabled.
- `commit-graph`: hourly.
- `prefetch`: hourly.
- `loose-objects`: daily.
- `incremental-repack`: daily.

- `git maintenance start`
It essentially provides a way to add cronjobs that run daily, hourly and weekly maintenance tasks on your Git repositories.

Basically it will just make lots of things faster in the background all the time automatically.
## Some big repo / monorepo stuff
- not relevant

## Some new GitHub stuff
- `git ls-remote`
Gives you refs to git branches