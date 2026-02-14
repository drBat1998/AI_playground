Title: Git & GitHub Crash Course 2025
Author: [[]]
Tags: #youtube #git 


# Notes
Git config = configurate your name and email that would be represented inside of git commit.
```bash
git config --global user.name "Roman Koval"
git config --global user.email "rkoval20081998@biph.kiev.ua"
```
Chose repo and in terminal use comand git init to activate git for the repo.
```bash
git init
```

git add, in order to add files in repo that git could track them.
```bash
git add . # . - to add every single files. 
```

git commit in order to save changes that you add to the file. 
```bash
git commit -m "initial commit" 
```

git status gives you general information about traking files ...
```bash
git status
```

If you want to use GitHub in order to save and deliver some files, you have to create repo in GitHub and give information about it to your local machine. 
```bash
git remote add origin git@github.com:drBat1998/Bioinformatics.git
git branch main
git push -u origin main
```

.gitignore is a file where you should enter all files that you wont to save local only. 

if your branch name in local host and GitHub does not match use:
```bash 
git push origin HEAD:I_want_to_understand_git
```

Gettting files from GitHub
git clone - copy full repo
git pull - pull last changes from the GitHub to local repo


Git branching
```bash
git branch # create the branch 
```
```bash
git checkout main # change branches
```

```bash
git merge name_branch # to merge two branches
```

# Links
https://youtu.be/vA5TTz6BXhY?si=hnAlOKCHvzj3niSC