# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > 
**show current working directory path:** pwd . 

**creating a directory:** mkdir *name of directory* (E.g. mkdir march2018) .     

**deleting a directory:** rm -r *name of directory* (E.g. rm -r march2018) [Be careful this removes everything in it too] .  

**creating a file using `touch` command:** touch *filename.filetype* (E.g. touch newnote.txt) . 

**deleting a file:** rm *filename* (E.g. rm oldnote.txt) . 

**renaming a file:** mv *oldfilename newfilename* (Renames 'oldfilename' to 'newfilename') . 

**listing hidden files:** ls -a (Shows files that start with a dot which are usually hidden) . 

**copying a file from one directory to another:** cp *directory1/filetocopy newdirectory/* (Copies 'filetocopy' in 'directory1' to 'newdirectory') .    

**moving a file from one directory to another:** mv *filetomove newdirectory/* (Moves 'filetomove' into 'newdirectory') . 

**returning home:** cd ~ (If you get lost, returns you to home directory) . 

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > 
`ls`  - lists files and directories in current directory . 

`ls -a`  - lists all contents in the current directory .   

`ls -l`  - lists all contents in the current directory in a long list format .    

`ls -lh`  - combines ls -l and ls -h commands (lists all files in a long list and human readable format) . 

`ls -lah`  - combines ls -l, ls -a, and ls -h commands (list all object, do not ignore files starting with a dot and in human 
readable format) . 

`ls -t`  - lists files and directories in the current directory in order of time modified . 

`ls -Glp` - lists contents in a long list format, without group names and uses '/' to indicate directories . 

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > 
`ls -c` - lists all contents by timestamp . 

`ls -m` - lists all contents as a comma-separated list

`ls -r` - lists all contents in reverse order

`ls -R` - Also displays subdirectories

`ls -q` - Displays all non-printed characters as a '?'


---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > 
The `xargs` command converts the standard input into a command which can be repeated multiple times if necessary. There are many ways of using `xargs` in the command line. One of the most common uses of `xargs` is alongside the `find` command to locate files with certain attributes (E.g. file type/age of file/file name). We can then perform another command on these files.    

For example: 
If we would like to locate files that are older than a number of days and remove them, we can combine the `find` and `rm` commands using `xargs` to do this. In this example we are removing all files in the 'October2018' directory that are older than 6 weeks or 42 days old:  


`find /October2018 -mtime +42 | xargs rm`


 

