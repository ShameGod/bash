# bash
A repository of valuable information around the bash scripting 

## Main command lines : 

### pwd : 
Indicates in which directory the shell is running 

### mkdir :
Creates a directory. It has many options, the main ones are :
  - v for verbose to say that the script created the directory and 
  - p to has idempotent command, which means that if the directory already exists it won't return an error 

### less, head and tail : 
 - Less : To read a text file, you can add the -N to have the line number 
 - Tail, head : returns by default the 10 last/recent lines in a file. You can specify the number of lines with -n

### ls :
Returns the list of files in a directory : 
  - -l : using this option allows you to have some details on the files such as the : date, size, permission and the type of file 
  - -lh : -lh is equivalent to -l -h, when adding the -h the size of the files are human readable 
  - -a : to show the hidden files 
  - ../. : indicates the parent directory, while "." indicates the current directory 

### file : 
This command tells the type of a file, it can be a symbolic file, an emty file, an executable file, an ASCII file ...

### rm : 
To remove a file or a directory. by default you can't remove a directory, you have to add the option -r

### mv : 
to move a file/ directory to a target directory. 

### ln :
Enables the creation of a symbolic link, file that likes to another file. It is necessary to use an absolute path for the source.

### cp :
To copy a file, you can use the tag : --report-identical-files to make sure that the files are identical 

### echo :
to print a text
- \n : to go to the next line 
- \t : to mark a tab space 
- * : to print all the files in a directory 
- {} : to set variables and iterate over them : example ``` echo hello{rida,adam,lamy,safa} ``` or ``` echo hello{1..5} ```
- $(()) : to do basic arithmetic operations : +,-,*,%,** 

### grep : 
to search for something in a file, text or command response : 
  - -i: to ignore the case 
  - -c: to count the number of instances 

## Nested command lines in bash 

It is possible to chain commands such as 

``` echo here is the list of the files in this directory $(ls -l) ```
