Title: key git commands
tags: #atomic_note #git 


# Notes
Add to git:
- git status
- git add - give a command to git to track the file - git add name_of_the_file or .(add all)
-  git commit - pass changes - git commit -m "meaningful description of the changes"
-  git log - to see all commits  


Add to GitHub
1. To add existing files to GitHub, we could use `git remote add origin git@link_to_created_git_rep`
2. git push - send to GitHub `- git push -u origin master`
3. git pull - take from GitHub

Branching
1. `git branch`- in what branch are you now
2. `git checkout -b "new_branch"` - to create
3. `git checkout main` - to move between branches
4. `git diff` - check what changes have been committed 
5. `git merge new_branch`
6. `git branch -d test` - to delete test branch

Merge conflict 
- git diff
- git merge 
- Choose what you want to leave 
- git commit 

Undo commits
- git reset name_file - undo git add
-  git reset HEAD~1 - undo last commit
- soft `git reset --soft comithash` - rebase but don't change anything
- hard `git reset --hard comithash` - rebase and change 

> Writing good commit is essential
- git reset "log"
- git reset "log" --hard - not just onstage but completely remove

In order to start tracking a remote branch that you have created on another machine. 
```shell
git checkout -b necroptosis_ogd origin/necroptosis_ogd
```

To find what changes have been made previously
```shell
git --no-pager diff HEAD~1
```

The best and the cutest way to see your changes. 
```bash
git log --oneline --graph
```

To find out a specific commit with a certain commit message:
``` shell 
git log --oneline --grep=test
```
The full change history of a file:
``` shell
git log --follow --patch -- name-of-file
```
The best way to change the history of a file:
``` shell
brew install tig

tig [filename]
```

Git commit history filter
``` shell
# by date
git log --before/--after="2017-7-1"
# by message
git log --grep="refactor"
# by filename
git log -- <filename>
# by brance
<branch>
```


[[git nvim]]
SSH keys
1. Generate SSH key locally on Mac or Linux - ssh-keygen -t rsa -b 4096 -C "email"
2.  cd /Users/name_user/.ssh
3. Copy the content of key.pub
4. Add to ssh key in GitHub
5. Adding SSH key to the ssh-agent 
# Links
[[Git and GitHub for Beginners]]
[[Git for Professionals Tutorial]]
[[Git & GitHub Crash Course 2025]]
[[Learn Git - The Full Course]]