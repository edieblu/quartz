---
tags:
  - ✅
published: 
sr-due: 2027-05-22
sr-interval: 1043
sr-ease: 250
---
⬅️ [[Bash]]

- 🔗 [From this FCC Video](https://www.youtube.com/watch?v=ZtqBQ68cfJc)

![[Pasted image 20220726080611.png]]

## History
- what we know of as Linux is actually a combo of GNU(the OS) and Linux (the Kernel)
- Linux is not Unix, but Unix-like. To be truly Unix you have to pay a lot of 💰 to get registered (also 🙅‍♀️ against the ethos of open and free)

## Shell
- a computer interface to an OS
- the shell takes our commands and gives them to the OS to perform
- it's named shell because it's the outer layer of the OS
- **terminal**: a program that runs a shell
- absolute paths (start with `~`): `~/Documents/...`

## mkdir
- `mkdir -p` create if it doesn't exist yet (used when creating nested dirs)
- `mkdir -p greenhouse/winter/lettuce`

## mv
- move the folder `my_dir` one level up: `mv my_dir/ ../`

## head and tail
- by default output first 10 lines, if you want to change that: `head -n 100`
- `tail -f` to track a log
## cat
- to add line number `cat -n`

## sort
- sort things numerically `sort -n`
- in reverse order `sort -r`
- unique values only `sort -u`

## uniq
- has more options than `sort -u`,  e.g. you can print _only_ duplicate lines, or only the lines that aren't duplicate, `uniq -d`, `uniq -u`
- count the number of occurrences: `uniq -c`

## expansion 
- `echo ~` (`~` expands to your home directory)
- `echo *` a list of every pathway in the current folder
- `echo *.txt` narrows it down!
- `?` matches any single character, `??` for two chars etc
- `{}` for curly brace expansion
- `echo {1..99}`
- the shell intervenes and expands a short thing into a longer thing

## diff
- `diff -y` to see the files side by side for comparison
- `diff -u` to give you some context around each change (it's what `gif diff` uses)

## find
- `find <LOCATION> <FILTER>`
- `-name -type -size -mtime`
- `-iname` for case insensitive
- `find . -type f -mtime 3` search files edited more than 3 days ago
- `-exec` specify the command you want `find` to execute on each item found
- `find . -type f -exec cat {} \;` execute cat, `{}` expands to the found file name `\;` to inform the terminal when the command ends

## grep
- `grep` for searching inside the files
- `greep <text> <filename>`
- `-n` with line numbers
- `-C` with context, `grep -nC 2` two lines before and after
- `-r` for recursive
- `-i` case insensitive
- works with regex

## du
- for file and directory sizes
- `-h` human readable sizes
- find the largest dir on your desktopL `du -h | sort -h`

## df
-  information about the mounted file systems

## history
- run a command from your history from a specific line: `!<line number>`
- find a command you ran a long time ago: `history | grep '<word>'`

## ps
- inspect processes
- `ps` only user initiated process
- `ps ax` all processes
- `ps axww` to enable word wrap
- `ps axww | grep 'Visual Studio Code'`

# top
- show top memory intensive processes
- `top -o mem` sort by memory used

## kill
- `15` shut things down gracefully (default option)
- `9` shut things down forcefully
- `kill -9 <PID>`
- `killall -9 node` to kill all processes that match the name

## xargs
- `command1 | xargs command2` (the output of the first command becomes the input of the 2nd command, aka the command's arguments)
- not all commands accept arguments from standard input (`sort` does)
- so `xargs` solved that, e.g. `rm` expects arguments after, but you can do `| xargs rm`...

## ln
- `ln -s` for creating soft/symbolic links
- `ln -s original.txt symlink.txt`
- the change is propagated both ways, but if you delete the original file the `symlink` file will break
- links are good for running different versions of a program (does `nvm` use that? 🤔)




