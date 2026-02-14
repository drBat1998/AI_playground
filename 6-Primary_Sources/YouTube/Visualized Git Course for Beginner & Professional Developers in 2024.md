Title: Visualized Git Course for Beginner & Professional Developers in 2024
Author: [[JavaScript Mastery]]
Tags: #youtube #git 


# Notes

```
git --version
```
git version 2.39.2 (Apple Git-143)

`git add` is a git command that tracks the file.
When you use `git commit`, you tell git to make a copy of the folder and information about the date. 

## git history
`git log` is a history of git changes

`git checkout log_name` gives you the ability to return to a previous version of the file. Moreover, git checkout only moves "HEAD" to the previous log, without deleting new ones. 

## branching 
```bash
git branch branch_name
```
to create the branch and to switch to it, use:
``` shell
git checkout branch_name
```
To instantly move to a newly created branch, use ``git checkout -b new_branch``
If you want to create a branch from a specific branch use: `git branch new_branch old_branch`

If applied to the coebase, this commit will ___ .

To publish the branch that you had created, use: 
```bash
git push --set-upstream origin git_lab

# or

git push -u origin new_branch
```
## merge
A pull request is a feature of GitHub to collaborate on code. 

## Resolving merge conflict
1. Check out the main branch
2. Pull the remote branch
3. Check out your branch
4. Merge your branch with information from the main branch. When you are in your branch, use `git merge main` to identify the problem.
5. Choose what we want to save. 

# reset 
```bash
git reset 
```
It is allowed to remove the commit history, but without deleting changes.

soft - move to staged
```bash
git reset --soft <log>
```
mixed - working but not staged
```bash
git reset
```
hard - discarded entirely
```bash
git reset --hard <log>
```

`git revert`

`git stash` - saves information in a stash list, but you don't see it

`git stash list` - gives a list of information that you have stashed.

`git stash apply <stash log> `adds information so that you can see it now. 


# Links
https://youtu.be/S7XpTAnSDL4?si=TG3q21PlGjK7akO4