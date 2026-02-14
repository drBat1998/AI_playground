Title: Linux Crash Course for Beginners with Labs
Author: [[freeCodeCamp.org]]
Tags: #linux


# Notes
## Log into Local and Remote consoles 
SSH - ==S==ecure ==SH==ell
` ip a` - inet 1....... - ip adres 

`ssh user_name@ip_adres` 
`ssh -v user_name@ip_adres` -verbose mode
## Read and Use System Documentation
`ls --help`
`man ls`

`apropos` = to search command that we forgot 
if don't work use `mandb` to update database

## Working with files and directories
`ls` - list
`ls -alh`

Absolute path = full path
/home/aaron/Documens/file.pds

`pwd` - print working directory
`cd`- change directory

Relative path - path from working directory

to create use `touch`

to create a directory `mkdir`

to copy use `cp [sourse] [destination]`
to copy all directories and all files the dir contains use `cp -r`

to move us `mv` + rename ability

to remove `rm`
to remove the dir and file in it use `rm -r`

# Create and Manage Hard link
`stat file_name` - show useful stats
`ln path_to_target path_to_link` - create a hard link that gives access to files for multiple users. 
- if one user deletes a link, the file won't erase and will be available for other users with hard link.
- only if all hard links erase the file would arise from hard drive. 

Limitations
- only files and not directories
- only files on the same filesystem

# Create and Manage Soft link
soft link consists of a link to real file 
`ln -s path_to_target path_to_link`
`readlink file_name`



To change group of the file 'chge name_group file_name'
To change owner 'sudo crown owner_name file_name '
File permission 
-rwx rwx rwx
	first owner
	Group 
	Other
R-read
W-write 
X-execute
First sign is about file type:
	d for directory 
	'-' for regular file 

## Change permissions 
'chmd ' u+wrx g+wrx o+wrx to add
Chmd u-wrx to remove permissions 

## Search file with 'grep'
'grep search_pattern file_name' case sensitive 
'grep -i search_pattern file_name' case insensitive 
'grep -r pattern dir_name' find in directory 
'grep  -wi search_pattern file_name' find exactly the word 
'grep -io pattern file_name' only matches 


## Analysis the text with regular expression 

`^` - in 6 num - "The line begins with" - `grep "^sam" names.txt` - "Grep the lines that begin with sam"
`$` - in 4 num - "The line ends with" -` grep "sam$"` - "Grep the lines that end with sam"
`.` - "Match any ONE character" - `grep -wr "c.t /etc/"` - "Grep the line where the word starts with c and end with t and has one character between these two characters"
`\` - "Escaping for special characters" - `grep '\.' /etc/login.defs`
`*` - in 8 num - "Match the previous element 0 or more times" - `grep -r "/.*/" directory_name` - "Grep pathways"
`\+` - "Match the previous element at least one time"

# Links
https://youtu.be/6WatcfENsOU?si=2Fm5OLR0yAIcxRC9