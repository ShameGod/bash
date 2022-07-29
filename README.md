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

### Nested command lines in bash 

It is possible to chain commands such as 

``` echo here is the list of the files in this directory $(ls -l) ```


## Users control with bash 

### adduser, addgroup, deluser and delgroup
adduser creates a new user, and creates a file in the home directory
addgroup creates a new groupe, to add a user to the group we use the command : ```usermod -g [groupName] [userName]```
delgroupe to delete a group 
deluser to delete a user, you need to add "--remove-home" to remove the directory related to the user 

### file access parameters 
When executing the command ls -l, we get the following line 

![image](https://user-images.githubusercontent.com/42012627/173235694-89153857-66ea-4054-9845-73eab88b8908.png)

on the left of every file are the permissions to access it. there are 3 groups of them : 

![image](https://user-images.githubusercontent.com/42012627/173235769-b8189d91-3073-4e1c-a0df-6a5c69ff951d.png)

Ignore the first "d", it just indicates that this is a directory
1- The first group indicates the permissions for the user : 
  - w : write permission
  - r : read permission
  - x : execute permission 
2- The second group indicates the permissions for the group where the user belongs 
3- The last group indicates the permissions for other users 

### chown and chgrp : 
these command are here to transfer the permissions from a user to another and from a group to another

### chmod : 
This is the main command that changes the permissions of a file. It has the following syntax : 
``` sudo chmod [entity] [operation] [permission] ```
  - entity : it can have 3 values (u  for user, g for group, o for other)
  - operation : it can have 2 values (+ to add permissions, - to remove permissions)
  - permission : it can have 3 values and it is cumulative (w to write, r to read and x to execute)  

## Useful commands to writes scripts : 
You will find within the repository multiple file with classic examples of scripts 
### read : 
to get an input value 
### if statement : 
```
read price
echo $price

if [[ $price >30 ]]; 
	then
	echo "this is too expensive !"
else
	echo "not so expensive :)"
fi
```

### loops : 

while loop :

```
read price
while [[ $price != 10 ]]; do
	echo "not enough try again"
	read price
done
echo bravo you have got it ! 
```
for loop : 

```
for var in {rida,adam,brahim,fatima}; do
	echo user $var
done
```

### functions : 

```
sayHello(){
	echo "hello et bienvenue $nom ";
}

clear;
read nom;
sayHello;
```

### arrays : 

```
utilisateurs=("rida" "adam" "safa" "fatima")
for var in ${utilisateurs[@]}; do
	echo the user is $var
done
```
##### Be careful the white space can cause errors when declaring your arrays, there shouldn't be any white space between the "=" and "("


### the pipe operation | : 

This operation is used to send the result of a command as an input to the next one : 
for example 
```
ls -1 |while read filename; do echo "here is a file "; done
```
