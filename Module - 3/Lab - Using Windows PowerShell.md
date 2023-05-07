### Part 1: Access PowerShell console.

a. Click Start. Search and select powershell.

b. Click Start. Search and select command prompt.

### Part 2: Explore Command Prompt and PowerShell commands.

a. Enter dir at the prompt in both windows.

Question: What are the outputs to the dir command?

![image](https://user-images.githubusercontent.com/116432525/236703805-60a43e53-6201-44ee-bf9d-65cad45aa8a0.png)

b. Try another command that you have used in the command prompt, such as ping, cd, and ipconfig.

Question:What are the results?

![image](https://user-images.githubusercontent.com/116432525/236703842-b9aad78b-5d54-4e13-aa0f-868157f17c42.png)

### Part 3: Explore cmdlets.

a. PowerShell commands, cmdlets, are constructed in the form of verb-noun string. To identify the PowerShell command to list the subdirectories and files in a directory, enter Get-Alias dir at the PowerShell prompt.

What is the PowerShell command for dir?

![image](https://user-images.githubusercontent.com/116432525/236703879-e378c6f5-6808-4494-bf8b-b278764d5c0c.png)

In PowerShell, the command equivalent to the "dir" command in the command prompt is "Get-ChildItem". The "Get-ChildItem" command lists the files and folders in the specified directory or location.

b. For more detailed information about cmdlets, perform an internet search for Microsoft powershell cmdlets.

c. Close the Command Prompt window when done.

### Part 4: Explore the netstat command using PowerShell.

a. At the PowerShell prompt, enter netstat -h to see the options available for the netstat command.

![image](https://user-images.githubusercontent.com/116432525/236703917-d47e7b7a-6a83-477c-ac7e-058bb418c364.png)

b. To display the routing table with the active routes, enter netstat -r at the prompt. 

![image](https://user-images.githubusercontent.com/116432525/236703938-5fa5036e-5e50-4fbc-92a9-61103b5dc638.png)

c. Open and run a second PowerShell with elevated privileges. Click Start. Search for PowerShell and right- click Windows PowerShell and select Run as administrator. Click Yes to allow this app to make changes to your device.

d. The netstat command can also display the processes associated with the active TCP connections. Enter the netstat -abno at the prompt.

![image](https://user-images.githubusercontent.com/116432525/236703989-6d01f51d-f16d-480f-8762-6c6348e60955.png)

e. Open the Task Manager. Navigate to the Details tab. Click the PID heading so the PID are in order.

f. Select one of the PIDs from the results of netstat -abno. PID 756 is used in this example.

![image](https://user-images.githubusercontent.com/116432525/236704136-8d65de6b-7b23-480d-8756-510bb9abc83f.png)
PID-2728 (esif_uf.exe)

g. Locate the selected PID in the Task Manager. Right-click the selected PID in the Task Manager to open the Properties dialog box for more information.

![image](https://user-images.githubusercontent.com/116432525/236704229-c8b3c0a4-d2bd-4834-9ead-8238521c248b.png)

### Part 5: Empty recycle bin using PowerShell.

PowerShell commands can simplify management of a large computer network. For example, if you wanted to implement a new security solution on all servers in the network you could use a PowerShell command or script to implement and verify that the services are running. You can also run PowerShell commands to simplify actions that would take multiple steps to execute using Windows graphical desktop tools

a. Open the Recycle Bin. Verify that there are items that can be deleted permanently from your PC. If not, restore those files.

b. If there are no files in the Recycle Bin, create a few files, such as text file using Notepad, and place them into the Recycle Bin.

c. In a PowerShell console, enter clear-recyclebin at the prompt.

![image](https://user-images.githubusercontent.com/116432525/236704304-749233b9-3b97-483a-9440-a5ac3cfdcb07.png)
![image](https://user-images.githubusercontent.com/116432525/236704332-d8ed54ba-7890-4f7a-8217-46ad9ecd6e12.png)


