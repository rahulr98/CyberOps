## Part 1: Exploring Filesystems in Linux
### Step 1: Access the command line.

  Launch the CyberOps Workstation VM and open a terminal window.
  
### Step 2: Display the filesystems currently mounted.
  
  a. Use the lsblk command to display all block devices:
  [analyst@secOps ~]$ lsblk

![image](https://github.com/rahulr98/CyberOps/assets/116432525/32bc66c9-4628-4698-b171-bf9b26959b69)

  b. Use the mount command to display more detailed information on the currently mounted filesystems in the CyberOps Workstation VM.
  [analyst@secOps ~]$ mount
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/42c10a27-5cf3-4ec2-867c-49cf25162e7f)

  c. Run the mount command again, but this time, use the pipe | to send the output of mount to grep to filter the output and display only the root filesystem:
  [analyst@secOps ~]$ mount | grep sda1

![image](https://github.com/rahulr98/CyberOps/assets/116432525/c57a7a8a-aa38-459a-9e3a-9f017bd93ab3)

  d. Issue the following two commands below on the CyberOps Workstation VM:
  [analyst@secOps ~]$ cd /
  [analyst@secOps /]$ ls -l

![image](https://github.com/rahulr98/CyberOps/assets/116432525/769e9d04-0585-4af4-ad50-405a490e4602)

  What is the meaning of the output? Where are the listed files physically stored?

  The listed files and directories are physically stored on the root filesystem, which, as determined earlier using the "mount" command, is located on the first partition of the sda block device (/dev/sda1).
  Why is /dev/sdb1 not shown in the output above?

  The output of the "ls -l" command in the root directory does not include the files and directories from the "/dev/sdb1" partition because the "/dev/sdb1" partition is not mounted on the root directory ("/").

### Step 3: Manually mounting and unmounting filesystems
  
  a. Use the ls -l command to verify that the directory second_drive is in the analyst's home directory.
  [analyst@secOps /]$ cd ~
  [analyst@secOps ~]$ ls –l

![2023-05-18_16-13](https://github.com/rahulr98/CyberOps/assets/116432525/ecb8d9d3-e6cf-451d-8b44-7d3252a89173)

  b. Use ls -l again to list the contents of the newly created second_drive directory.
  [analyst@secOps ~]$ ls -l second_drive/ 
  
  c. Use the mount command to mount /dev/sdb1 on the newly created second_drive directory. The syntax of mount is: mount [options] .
  [analyst@secOps ~]$ sudo mount /dev/sdb1 ~/second_drive/

  d. Now that the /dev/sdb1 has been mounted on /home/analyst/second_drive, use ls -l to list the contents of the directory again.
  [analyst@secOps ~]$ ls -l second_drive/
  
![as](https://github.com/rahulr98/CyberOps/assets/116432525/91b7fbc9-8f61-46de-876b-537d4601d162)

  Why is the directory no longer empty? Where are the listed files physically stored?

  The directory is no longer empty because the files from /ddev/sdb1 are being mounted to ~/second_drive/

  e. Issue the mount command with no options again to display detailed information about the /dev/sdb1 partition. As before, use the grep command to display only the /dev/sdX filesystems:
  [analyst@secOps ~]$ mount | grep /dev/sd
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/1dff32c4-a7ad-41c6-96cf-57fd989c0363)

  f. Unmounting filesystems is just as simple. Make sure you change the directory to something outside of the mounting point and use the umount command, as shown below:
  [analyst@secOps ~]$ sudo umount /dev/sdb1

![image](https://github.com/rahulr98/CyberOps/assets/116432525/8256069d-eda7-4990-ae28-4f6e02c82e58)
![image](https://github.com/rahulr98/CyberOps/assets/116432525/4c46db8d-6c8a-4b22-8cfd-31de80335fb2)

### Part 2: File Permission

## Step 1: Visualize and Change the File Permissions.

  a. Navigate to /home/analyst/lab.support.files/scripts/.
  [analyst@secOps ~]$ cd lab.support.files/scripts/
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/911fa972-9ca4-4f1a-990e-b6e53943e4a3)

  Consider the cyops.mn file as an example. Who is the owner of the file? How about the group?

   - User 'analyst' . Group 'analyst'

  The permissions for cyops.mn are –rw-r--r--. What does that mean?

   - It means that user has only read and write permission, while group and others have only read permission.

  c. The touch command is very simple and useful. It allows for the quick creation of an empty text file. Use the command below to create an empty file in the /mnt directory:
  [analyst@secOps scripts]$ touch /mnt/myNewFile.txt
  [analyst@secOps ~]$ ls -ld /mnt

![image](https://github.com/rahulr98/CyberOps/assets/116432525/d1d25fd5-2289-4f8b-a79f-ae3abde2c164)
  
  What can be done for the touch command shown above to be successful?

   - Can add 'sudo' to the command to impersonate as user.

  d. The chmod command is used to change the permissions of a file or directory. As before, mount the /dev/sdb1 partition on the /home/analyst/second_drive directory created earlier in this lab:
  [analyst@secOps ~]$ sudo mount /dev/sdb1 ~/second_drive/

  e. Change to the second_drive directory and list the contents of it:
  [analyst@secOps ~]$ cd ~/second_drive
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/8a37318a-9db8-4f6b-b880-8e4fe868386b)

   What are the permissions of the myFile.txt file?

   - It means that user has only read and write permission, while group and others  have only read permission.
   
   f. Use the chmod command to change the permissions of myFile.txt.
    [analyst@secOps second_drive]$ sudo chmod 665 myFile.txt
    [analyst@secOps second_drive]$ ls -l
 
 ![image](https://github.com/rahulr98/CyberOps/assets/116432525/f41c2f2d-0de6-4a51-be29-35a7a25d9201)
  
  Did the permissions change? What are the permissions of myFile.txt?

  - Yes now users and group has got write permission while others has got executable permission.
  
  What command would change the permissions of myFile.txt to rwxrwxrwx, granting any user in the system full access to the file?

  - chmod 777 myFile.txt

  g. The chown command is used to change ownership of a file or directory. Issue the command below to make root the owner of the myFile.txt:
[analyst@secOps second_drive]$ sudo chown analyst myFile.txt

![image](https://github.com/rahulr98/CyberOps/assets/116432525/2f49f73c-795e-401d-800b-d3bc27872a05)

  h. Now that analyst is the file owner, try appending the word ‘test’ to the end of myFile.txt.
  [analyst@secOps second_drive]$ echo test >> myFile.txt
  [analyst@secOps second_drive]$ cat myFile.txt

  Question: Was the operation successful? Explain
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/f5df076a-fb4f-43fb-92dc-905537c3b54e)

## Step 2: Directory and Permissions

  a. Change back to the /home/analyst/lab.support.files directory and issue the ls -l command to list all the files with details:
  [analyst@secOps second_drive]$ cd ~/lab.support.files/
  [analyst@secOps lab.support.files]$ ls -l
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/ed7e3b30-d043-4ab7-9aac-c9dc68a48c8b)

  Question:Compare the permissions of the malware directory with the mininet_services file. What is the difference between beginning part of the malware line and the mininet_services line?

  - Malware is a directory and mininet_services is a file.

### Part 3: Symbolic Links and other Special File Types

## Step 1: Examine file types.
  
  a. Use the ls -l command to display the files in the /home/analyst folder. Notice the first characters of each line are either a “–“ indicating a file or a “d” indicating a directory.
  [analyst@secOps ~]$ ls -l
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/c3e0a8bd-9c96-4656-8b45-581f68431a5f)

  b. Produce a listing of the /dev directory. Scroll to the middle of the output and notice how the block files begin with a “b”, the character device files begin with a “c” and the symbolic link files begin with an “l”:
  [analyst@secOps ~]$ ls -l /dev/

![image](https://github.com/rahulr98/CyberOps/assets/116432525/2c6e6537-4375-4973-a446-a1e8acbbf5e4)

  c. Symbolic links in Linux are like shortcuts in Windows. There are two types of links in Linux: symbolic links and hard links. The difference between symbolic links and a hard links is that a symbolic link file points to the filename of another file and a hard link file points to the contents of another file. Create two files by using echo:
  [analyst@secOps ~]$ echo "symbolic" > file1.txt
  [analyst@secOps ~]$ cat file1.txt
  [analyst@secOps ~]$ echo "hard" > file2.txt
  [analyst@secOps ~]$ cat file2.txt
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/eed3c3c7-ebd9-4ee3-8ea8-c14824df1590)

  d. Use ln –s to create a symbolic link to file1.txt, and ln to create a hard link to file2.txt:
  [analyst@secOps ~]$ ln –s file1.txt file1symbolic
  [analyst@secOps ~]$ ln file2.txt file2hard
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/dbafa63b-6b85-4354-b49f-f6a8321c7fd5)

  f. Change the names of the original files: file1.txt and file2.txt, and notice how it effects the linked files.
  [analyst@secOps ~]$ mv file1.txt file1new.txt
  [analyst@secOps ~]$ mv file2.txt file2new.txt
  [analyst@secOps ~]$ cat file1symbolic
  [analyst@secOps ~]$ cat file2hard hard
  
![image](https://github.com/rahulr98/CyberOps/assets/116432525/0fbf20a7-e4ba-484b-a189-7113b69e394d)
![image](https://github.com/rahulr98/CyberOps/assets/116432525/7285b2da-f818-41cf-85c3-6e530657253b)

  What do you think would happen to file2hard if you opened a text editor and changed the text in file2new.txt?
 
![image](https://github.com/rahulr98/CyberOps/assets/116432525/cb6fc79b-3ccc-4db2-8789-ce02351c5007)

  - When the text of file2new.txt is changed, the text of file2hard also changed.
