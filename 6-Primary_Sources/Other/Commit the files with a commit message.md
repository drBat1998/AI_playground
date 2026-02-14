Title: Commit the files with a commit message
Tags: #git


# Notes
$ git add file1 file2

Commit the files with a commit message
$ git commit -m "Fixed files 1 and 2" -- file1 file2

If you accidentally commit the wrong files
$ git reset --soft HEAD~1

If you want to unstage the files and start over
$ git reset

Unstaged changes after reset:
M file1
M file2
M file3
M file4
# Links
https://stackoverflow.com/questions/7239333/how-do-i-commit-only-some-files