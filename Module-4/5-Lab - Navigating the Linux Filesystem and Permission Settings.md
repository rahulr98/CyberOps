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
