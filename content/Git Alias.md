---
tags:
  - ✅
published: true
sr-due: 2025-10-04
sr-interval: 494
sr-ease: 250
---
⬅️ [[Git]]
## From `.gitconfig`
```bash
[alias]
	diffc = diff --cached
	ff = merge --ff-only
	pushn = push --no-verify
	

	# ⬇️
	lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --branches
	
	hist = log --all --graph --decorate
	
	# ⬇️
	# show last ten local branches
	recent = !git reflog show --pretty=format:'%gs ~ %gd' --date=relative | grep 'checkout:' | grep -oE '[^ ]+ ~ .*' | awk -F~ '!seen[$1]++' | head -n 10 | awk -F' ~ HEAD@{' '{printf(\"  \\033[33m%s: \\033[37m %s\\033[0m\\n\", substr($2, 1, length($2)-1), $1)}'
	
	# Show the diff between the latest commit and the current state.
	d = !"git diff-index --quiet HEAD -- || clear; git --no-pager diff --patch-with-stat"


	# ⬇️
	# Remove branches that have already been merged with main.
	# a.k.a. ‘delete merged’
	dm = "!git branch --merged | grep -v '\\*' | xargs -n 1 git branch -d"
```

## From `.zsh`
```bash
# misc git alias
alias g=git


alias gc='git commit -a -m'
alias gs='git status -sb'
alias gstats='git shortlog -sn --all --no-merges'

alias gfix='git commit --amend --no-edit'
alias go='git checkout'
alias get='git fetch && git pull'

# ⬇️
alias repo='gh repo view -w'

alias gfirst='git log --pretty=format:"%ad" --date=short --diff-filter=A --'
```