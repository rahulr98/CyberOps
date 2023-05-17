## Part 1: Shell Basics

  The shell is the term used to refer to the command interpreter in Linux. Also known as Terminal, Command Line and Command Prompt, the shell is very powerful way to interact with a Linux computer.
  
### Step 1: Access the Command Line
  
  a. Log on to the CyberOps Workstation VM as the analyst using the password cyberops. The account analyst is used as the example user account throughout this lab.
  
  b. To access the command line, click the terminal icon located in the Dock, at the bottom of VM screen. The terminal emulator opens.
  
### Step 2: Display Manual Pages from the command line.

  You can display command line help using the man command. A man page, short for manual page, is a builtin documentation of the Linux commands. A man page provides detailed information about a given command and all its available options.
  
  a. To learn more about the man page, type: [analyst@secOps ~]$ man man

![34](https://github.com/rahulr98/CyberOps/assets/116432525/96979137-93e3-4cb8-9c8e-aa78aeee2bc9)

  Question:Name a few sections that are included in a man page.

  b. Type q to exit the man page.
  c. Use the man command to learn more about the cp command: [analyst@secOps ~]$ man cp

![35](https://github.com/rahulr98/CyberOps/assets/116432525/73530391-570d-45b7-9d11-3416400e0b70)
![36](https://github.com/rahulr98/CyberOps/assets/116432525/7347ec90-cbb0-452a-a5ad-e81b28041a11)

 Question: What is the function of the cp command?
      ANS: The cp command is a commonly used command in Unix-like operating systems, including Linux. It stands for "copy" and is used to copy files and directories from one location to another. The cp command allows you to duplicate files, create backups, and transfer data between directories or devices.
  
### Step 3: Create and change directories.

  In this step, you will use the change directory (cd), make directory (mkdir), and list directory (ls) commands.
  Note: A directory is another word for folder. The terms directory and folder are used interchangeably throughout this lab.

  a. Type pwd at the prompt: [analyst@secOps ~]$ pwd
  b. Navigate to the /home/analyst directory if it is not your current directory. Type cd /home/analyst: [analyst@secOps ~]$ cd /home/analyst
  c. Type ls -l at the command prompt to list the files and folders that are in the current folder. Standing for list, the -l option displays file size, permissions, ownership, date of creation and more: [analyst@secOps ~]$ ls -l
  
![37](https://github.com/rahulr98/CyberOps/assets/116432525/603b69a8-8b00-423e-9a4b-2e2eb9e7933e)

  d. In the current directory, use the mkdir command to create three new folders: cyops_folder1, cyops_folder2, and cyops_folder3. Type mkdir cyops_folder1 and press Enter. Repeat these steps to create cyops_folder2 and cyops_folder3.
  [analyst@secOps ~]$ mkdir cyops_folder1
  [analyst@secOps ~]$ mkdir cyops_folder2
  [analyst@secOps ~]$ mkdir cyops_folder3
 
  e. Type ls -l to verify that the folders have been created:
  [analyst@secOps ~]$ ls -l
  
![38](https://github.com/rahulr98/CyberOps/assets/116432525/95b7d0c4-1208-4fd5-8c3e-3f644fd5997a)

  f. Type cd /home/analyst/cyops_folder3 at the command prompt and press Enter.
  [analyst@secOps ~]$ cd /home/analyst/cyops_folder3
  
![39](https://github.com/rahulr98/CyberOps/assets/116432525/f61f2298-a0c2-4357-8a28-2f4df89c2bd9)

  g. Use the mkdir command to create a new folder named cyops_folder4 inside the cyops_folder3 folder:
  [analyst@secOps ~]$ mkdir /home/analyst/cyops_folder3/cyops_folder4

  h. Use the ls -l command to verify the folder creation.
  analyst@secOps ~]$ ls –l /home/analyst/cyops_folder3

![40](https://github.com/rahulr98/CyberOps/assets/116432525/0195cffd-7b74-444d-b409-3aca5d4402b9)

  i. Up to this point, we have been using full or absolute paths. Absolute path is    the term used when referring to paths that always start at the   root (/) directory. It is also possible to work with relative paths. Relative paths reduce the amount of text to be typed. To understand relative paths, we must understand the . and .. (dot and double dot) directories. From the cyops_folder3 directory, issue a ls –la:
  analyst@secOps ~]$ ls –la /home/analyst/cyops_folder3
  
![41](https://github.com/rahulr98/CyberOps/assets/116432525/daba1429-ac8f-473c-bee5-04bbf04a6430)

  j. Change the current directory to /home/analyst/cyops_folder3:  [analyst@secOps ~]$ cd /home/analyst/cyops_folder3

  k. Type cd .  :[analyst@secOps cyops_folder3]$ cd .
  
![42](https://github.com/rahulr98/CyberOps/assets/116432525/f24cfaee-a53d-4123-b883-c9053022ebfd)

  l. Changing the directory to the .. directory, will change to the directory that is one level up. This directory is also known as parent directory. Type cd ..[analyst@secOps cyops_folder3]$ cd ..

![43](https://github.com/rahulr98/CyberOps/assets/116432525/2f00ea17-d512-4a23-a6d3-dc0cedb29f55)

### Step 4: Redirect Outputs.
  Another powerful command line operator in Linux is known as redirect. Represented by the > symbol, this 
  operator allows the output of a command to be redirected to some location other the current terminal window (the default).

  a. Use the cd command to change to the /home/analyst/ (~) directory:
  [analyst@secOps /]$ cd /home/analyst/
  
  b. Use the echo command to echo a message. Because no output was defined, echo will output to the current terminal window:  analyst@secOps ~]$ echo This is a message echoed to the terminal by echo. _echo hi how are you?_
 
 c. Use the > operator to redirect the output of echo to a text file instead of to the screen:
analyst@secOps ~]$ _echo hi how are you? > some_text_file.txt_

  d. Notice, that even though the some_text_file.txt file did not exist, prior to the echo command, it was automatically created to receive the output generated by echo. Use the ls -l command to verify if the file was really created:
[analyst@secOps ~]$ ls –l some_text_file.txt

  e. Use the cat command to display the contents of the some_text_file.txt text file:
[analyst@secOps ~]$ cat some_text_file.txt

  f. Use the > operator again to redirect a different echo output of echo to the some_text_file.txt text file:
analyst@secOps ~]$  _echo hi Im fine. > some_text_file.txt_
  
  g. Once again, use the cat command to display the contents of the some_text_file.txt text file:
[analyst@secOps ~]$ cat some_text_file.txt

![44](https://github.com/rahulr98/CyberOps/assets/116432525/2af91aa3-6614-4d04-a2f4-409e174a8ac0)
![45](https://github.com/rahulr98/CyberOps/assets/116432525/e67e2f50-e69a-475a-a1cc-548bd7df85f4)

### Step 6: Work with hidden files in Linux.
  a. In Linux, files with names that begin with a ‘.’ (single dot) are not shown by default. While dot-files have nothing else special about them, they are called hidden files because of this feature. Examples of hidden files are .file5, .file6, .file7
  
  b. Use ls -l to display the files stored in the analyst home directory.
  [analyst@secOps ~]$ ls –l
  How many files are displayed? **_36_**

![46](https://github.com/rahulr98/CyberOps/assets/116432525/de021757-5c93-43c6-bace-4c69699561f6)

  c. Use the ls -la command to display all files in the home directory of analyst, including the hidden files.
  [analyst@secOps ~]$ ls –la
  Questions:How many more files are displayed than before? **_160_**
  
 ![47](https://github.com/rahulr98/CyberOps/assets/116432525/3864aa97-ea32-4dc1-b7dc-11236c05e59d)

## Part 2: Copying, Deleting, and Moving Files
### Step 1: Copying Files
  a. The cp command is used to copy files around the local file system. When using cp, a new copy of the file is created and placed in the specified location, leaving the original file intact. The first parameter is the source file and the second is the destination. Issue the command below to copy some_text_file.txt from the home directory to the cyops_folder2 folder:
  [analyst@secOps ~]$ cp some_text_file.txt cyops_folder2/
  
  b. Use the ls command to verify that some_text_file.txt is now in cyops_folder2:
  [analyst@secOps ~]$ ls cyops_folder2/some_text_file.txt

  c. Use the ls command to verify that some_text_file.txt is also in the home directory:
  [analyst@secOps ~]$ ls -l

![48 S1](https://github.com/rahulr98/CyberOps/assets/116432525/e895d1ac-9116-4f3a-b996-2bc82071cb37)

### Step 2: Deleting Files and Directories
  a. Use the rm command to remove files. Issue the command below to remove the file some_text_file.txt from the home directory. The ls command is then used to show that the file some_text_file.txt has been removed from the home directory:
  [analyst@secOps ~]$ rm some_text_file.txt
  [analyst@secOps ~]$ ls -l
  
  b. In Linux, directories are seen as a type of file. As such, the rm command is also used to delete directories but the -r (recursive) option must be used. Notice that all files and other directories inside a given directory are also deleted when deleting a parent directory with the -r option. Issue the command below to delete the cyops_folder1 folder and its contents:
  [analyst@secOps ~]$ rm –r cyops_folder1
  [analyst@secOps ~]$ ls -l

![49](https://github.com/rahulr98/CyberOps/assets/116432525/8c5f6b91-806d-4def-a685-ce155c87a890)

### Step 3: Moving Files and Directories
  a. Moving files works similarly to copying files. The difference is that moving a file removes it from its original location. Use the mv commands to move files around the local filesystem. Like the cp commands, the mvcommand also requires source and destination parameters. Issue the command below to move the some_text_file.txt from /home/analyst/cyops_folder2 back to the home directory:
  [analyst@secOps ~]$ mv cyops_folder2/some_text_file.txt .
  [analyst@secOps ~]$ ls –l cyops_folder2/
  [analyst@secOps ~]$ ls –l /home/analyst/

![50](https://github.com/rahulr98/CyberOps/assets/116432525/cbe2d6f2-600d-4892-9286-a4cf89c46458)

  
