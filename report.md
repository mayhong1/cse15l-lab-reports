# Lab Report 1 

This lab report is about the commands cd, ls, and cat

## Here are some examples of the command cd

** no arguments **
![Image](screenshot1.png)	

Working directory: /home

Nothing happens because cd switches the current working directory to the argument (which should be a path), and since there is no argument, the current working directory stays as is. There is no error.

** path to a directory as an argument **
![Image](screenshot2.png)	

Working directory: /home/lecture1

The current directory is switched from /home to /home/lecture1. This happens because the cd command switches the current working directory to the argument, which is lecture1. There is no error.

** path to a file as an argument **
![Image](screenshot3.png)	

Working directory: /home/lecture1

The cd command switches the current working directory to the argument. An error occurs because the argument isn't a path to a directory, so the command therefore doesn't work. 

## Here are some examples of the command ls

** no arguments **
![Image](screenshot8.png)	

Working directory: /home

The argument for the ls command should be a path, and the output should be a list of the files and folders in the path. Since there is no argument, the files in the current working directory are listed, which is just the lecture1 folder. There is no error.

** path to a directory as an argument **
![Image](screenshot9.png)	

Working directory: /home

All the files in the lecture1 folder are listed because the ls command lists all the files in the given path, which in this case would be the lecture1 folder as that is the arguement. There is no error.

** path to a file as an argument **
![Image](screenshot10.png)	

Working directory: /home/lecture1

Hello.java is listed because that is the only file that is in the /home/lecture1/Hello.java path. There is no error. 

## Here are some examples of the command cat

** no arguments **
![Image](screenshot5.png)	

Working directory: /home

** path to a directory as an argument **
![Image](screenshot6.png)	

Working directory: /home

Cat is meant to print the contents of a file. In this case, the argument is a path to a directory, not a file, so an error occurs.

** path to a file as an argument **
![Image](screenshot7.png)	
Working directory: /home/lecture1

The content of the file Hello.java is printed because the cat command prints the contents of the file of the given path. There is no error.
