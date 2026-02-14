Title: Learn Git - The Full Course
Author: [[Boot dev]]
Tags: #youtube #git 


# Notes
Files in the repo may be in one of the three states:
- untracked - not being tracked by git
- staged -  in line to commit
- committed -  saved to the repository's history. 

A commit is a snapshot of the repository at the given point in time. 

``git log`` is a history of commits.

git compresses and deduplicates files to snapshot commits. 

`git switch` and `git checkout` are more or less the same; git switch is an easier way to change branches. 

`git log --oneline` gives you the ability to check your history with just commit messages. 
```bash
git log --oneline
```
The best and the cutest way to see your changes. 
```bash
git log --oneline --graph
```
In order to merge:
1. First, determine the "merge base", usually it is the main. `git switch main`
2. Replace the changes in the other branch with the main. `git merge name_branch`
3. Record the merge with a commit. `git commit -m "merge commit information"`

fast forward mergie

git rebase

Reset
- soft `git reset --soft comithash` - rebase but don't change anything
	- `git reset --soft HEAD~1` - rebase one step back
- hard `git reset --soft comithash` - rebase and change 

gitignore
add inside file that you wish not to track
```bash
*.txt #ignore all txt file
!example.txt # exept example file
```


# Links
https://youtu.be/rH3zE7VlIMs?si=yEYML-vjVtftsmSs