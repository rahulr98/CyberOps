## Part 1: Log File Overview

### Step 1: Web server log file example

  a. Use the cat command below to list a web server sample log file. The sample file is located at /var/log:
    [analyst@secOps ~]$ cat /var/log/logstash-tutorial.log
 
![1](https://github.com/rahulr98/CyberOps/assets/116432525/59f8c9d8-4c1a-4c31-958c-4e6e21c7a144)

  Explain why the output of the cat command is in a different format than the single entry shown in item.

   - The 'cat' command if being given to a file it lists the contents of a file and if being given to a directory it lists the number of files present in the directory.

  ### Step 2: Operating system log file example

  a. [analyst@secOps ~]$ sudo more /var/log/messages
  
![2](https://github.com/rahulr98/CyberOps/assets/116432525/9b4e0aca-5824-48e9-815d-44b77c391238)

  Notice that the events listed above are very different from the web server events. Because the operating system itself is generating this log, all recorded events are in relation to the OS itself.
  
  b. If necessary, enter Ctrl + C to exit out of the previous command.

  c. Log files are very important for troubleshooting. Assume that a user of that specific system reported that all network operations were slow around 4:20 am on May 19.

  Question: Can you find evidence of that in the log entries shown above? If so, in what lines? Explain.

  To easily find the specific time mentioned, the below listed command can be given:
  cat /etc/log/messages | grep "May 19 04:2"

  This command can help in finding the information of the specific time.

## Part 2: Locating Log Files in Unknown Systems
  a. When working with new software, the first step is to look at the documentation. It provides important information about the software, including information about its log files. Use the man command to display the nginx manual page:
  [analyst@secOps ~]$ man nginx

![3](https://github.com/rahulr98/CyberOps/assets/116432525/0be46f91-08bf-40cd-9c77-95460ef6aa61)

  b. Scroll down the page to locate the nginx logging section. The documentation makes it clear that nginx supports logging, with the location of its log files defined at compilation time.

![4](https://github.com/rahulr98/CyberOps/assets/116432525/8c2c740a-1d44-4d19-937f-b94026a331b9)

  c. The manual page also contains information on the files used by nginx. Scroll down further to display the nginx operating files under the Files section:

![5](https://github.com/rahulr98/CyberOps/assets/116432525/e44eb0f9-52c0-4950-bdd0-eb8816ccdac8)

  d. Before looking for nginx files, use the ps and the grep commands to ensure nginx is running in the VM.

  Note: Use man to learn more about ps and grep commands.
  [analyst@secOps ~]$ ps ax | grep nginx
  
![6](https://github.com/rahulr98/CyberOps/assets/116432525/6fced1b0-2bed-439e-864d-7d87863e1992)

  e. [analyst@secOps ~]$ ls /etc/

![7](https://github.com/rahulr98/CyberOps/assets/116432525/57c7a5b5-237e-4ab2-bb01-bc52506414de)

  f. Notice the nginx folder under /etc in the output above. Using ls again, we find a number of files, including one named nginx.conf.
  [analyst@secOps ~]$ ls -l /etc/nginx/
  
![8](https://github.com/rahulr98/CyberOps/assets/116432525/a293decf-5ad2-41f6-94d3-067c7689af41)

  h. A quick look at the configuration file reveals that it is an nginx configuration file. Because there is no direct mention to the location of nginx log files, it is very likely that nginx is using default values for it. Following the convention of storing log files under /var/log, use the ls command to list its contents:
  [analyst@secOps ~]$ ls -l /var/log/
  
![9](https://github.com/rahulr98/CyberOps/assets/116432525/17ed8bf0-c62f-47a5-87c8-503715a7a44c)

  i. As shown above, the /var/log directory has a subdirectory named nginx. Use the ls command again to list the contents of /var/log/nginx.
  
![10](https://github.com/rahulr98/CyberOps/assets/116432525/d688e6b5-77b2-48f5-9134-b516a0cca0fc)

  Note: Because the /var/log/nginx belongs to the http user, you must execute ls as root by preceding it with the sudo command.
  [analyst@secOps ~]$ sudo ls -l /var/log/nginx
  
![11](https://github.com/rahulr98/CyberOps/assets/116432525/3b7c1f6f-5d62-45fd-bd44-4e1f1c6bd4fa)

## Part 3: Monitoring Log Files in Real Time

### Step 1: Using the tail command

  The tail command displays the end of a text file. By default, tail will display the last ten (10) lines of a text file. Note: If you do not see any log entries, navigate to 127.0.0.1 in a web browser and refresh the page a few time.

  a. Use the tail command to display the end of the /var/log/nginx/access.log.
  [analyst@secOps ~]$ sudo tail /var/log/nginx/access.log

![12](https://github.com/rahulr98/CyberOps/assets/116432525/c14f02c9-a897-41ab-baa5-b98e7671b7dc)

  b. Use the –n option to specify how many lines from the end of a file, tail should display.
  [analyst@secOps ~]$ sudo tail -n 5 /var/log/nginx/access.log
  
![13](https://github.com/rahulr98/CyberOps/assets/116432525/3f59ee53-ee00-4afc-b254-99dccc5b1a55)

  b. Use the –n option to specify how many lines from the end of a file, tail should display.
  [analyst@secOps ~]$ sudo tail -n 5 /var/log/nginx/access.log
  
![14](https://github.com/rahulr98/CyberOps/assets/116432525/acc555e4-c6b2-4e1a-bd56-7648cf3dbb75)

  d. Because the log file is being updated by nginx, we can state with certainty that /var/log/acess.log is in fact the log file in use by nginx.

  e. Enter Ctrl + C to end the tail monitoring session.

### Step 2: BONUS TOOL: Journalctl
  a. In a terminal window in the CyberOps Workstation VM, issue the journalctl command with no options to display all journal log entries (it can be quite long):
  [analyst@secOps ~]$ journalctl

![15](https://github.com/rahulr98/CyberOps/assets/116432525/a24aa10f-4c72-4513-925f-68a0c8eb48b2)

  How can you run journalctl and see all log entries?

  This can be done by using 'sudo journalctl --no-pager'
  
  b. journalctl includes options to help in filtering the output. Use the –b option to display boot-related log entries:
  [analyst@secOps ~]$ sudo journalctl -b -2
  
![17](https://github.com/rahulr98/CyberOps/assets/116432525/4210c1a7-844c-4c45-8ae4-67374a60aa35)

  d. Use the --list-boots option to list previous boots:
  [analyst@secOps ~]$ sudo journalctl –-list-boots

![17](https://github.com/rahulr98/CyberOps/assets/116432525/71b9dc6a-3a35-40e4-a771-5d6934dbfc2f)

  e. Use the --since “” to specify the time range of which log entries should be displayed. The two commands below display all log entries generated in the last two hours and in the last day, respectively:
  [analyst@secOps ~]$ sudo journalctl –-since "2 hours ago"
  
![18](https://github.com/rahulr98/CyberOps/assets/116432525/dcb280b9-cf77-4d32-9715-b6654869d9a1)
 
