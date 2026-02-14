Title: Git and GitHub for Beginners
Author: [[freeCodeCamp.org]]
Tags: #git

[[git]]
# Notes

Add to git:
1. git status
2. git add - give a command to git to track the file - git add name_of_the_file or .(add all)
3. git commit - pass changes - git commit -m "meaningful description of the changes"

SSH keys
1. Generate SSH key locally on Mac or Linux - ssh-keygen -t rsa -b 4096 -C "email"
2.  cd /Users/name_user/.ssh
3. copy the content of key.pub
4. add to ssh key in GitHub
5. adding ssh key to the ssh-agent 


Add to GitHub
1. to add existing files to GitHub we could use `git remote add origin git@link_to_created_git_rep`
2. git push - send to GitHub `- git push -u origin master`
3. git pull - take from GitHub

Branching
1. `git branch`- in what branch you are now
2. `git checkout -b "new_branch"` - to create
3. `git checkout main` - to move between branches
4. `git diff` - check what changes have been committed 
5. `git merge new_branch`
6. `git branch -d test` - to delete test branch

Merge conflict 
- git diff
- git merge 
- chose what you want to leave 
- git commit 

Undo commits
- git reset name_file - undo git add
-  git reset HEAD~1 - undo last one commit
-  git log - to see all commits  
> Write good commit is essential
- git reset "log"
- git reset "log" --hard - not just onstage but completely remove
# Links
https://youtu.be/RGOj5yH7evk?si=LetI-C_v7jy3fSYb