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

  i. Up to this point, we have been using full or absolute paths. Absolute path is the term used when referring to paths that always start at the root (/) directory. It is also possible to work with relative paths. Relative paths reduce the amount of text to be typed. To understand relative paths, we must understand the . and .. (dot and double dot) directories. From the cyops_folder3 directory, issue a ls –la:
  analyst@secOps ~]$ ls –la /home/analyst/cyops_folder3
  
![41](https://github.com/rahulr98/CyberOps/assets/116432525/daba1429-ac8f-473c-bee5-04bbf04a6430)

  
