## Part 1: Graphical Text Editors

### Step 1: Open SciTE from the GUI
  a. Log on to the CyberOps VM as the user analyst using the password cyberops. The account analyst is used as the example user account throughout this lab.
  b. On the top bar, navigate to Applications > CyberOPS > SciTE to launch the SciTE text editor.
  
![1](https://github.com/rahulr98/CyberOps/assets/116432525/2fbf9ff8-402c-4060-8a80-d12c86627f25)
![2](https://github.com/rahulr98/CyberOps/assets/116432525/e2818fa3-f7da-43f6-b6c0-1f70a93e5c25)

c. SciTE is simple but includes a few important features: tabbed environment, syntax highlighting and more. Spend a few minutes with SciTE. In the main work area, type or copy and paste the text below: “Space, is big. Really big. You just won't believe how vastly, hugely, mindbogglingly big it is. I mean, you may think it's a long way down the road to the chemist, but that's just peanuts to space.” ― Douglas Adams, The Hitchhiker’s Guide to the Galaxy.

![3](https://github.com/rahulr98/CyberOps/assets/116432525/95dca9ff-c03c-41cd-9daa-74966316ef03)

d. Click File > Save to save the file. Notice that SciTE attempts to save the file to the current user’s home directory, which is analyst, by default. Name the file space.txt and click Save.

![4](https://github.com/rahulr98/CyberOps/assets/116432525/09369b13-e01c-42a3-b89b-801f7d56636c)

e. Close SciTE by clicking the X icon on the upper right side of the window and then reopen SciTE.

f. Click File > Open... and search for the newly saved file, space.txt.

g. Even though SciTE is looking at the correct directory (/home/analyst), space.txt is not displayed. This is because SciTE is looking for known extensions and .txt is not one of them. To display all files, click the dropdown menu at the bottom of the Open File window and select All Files (*).

h. Select space.txt to open it. Note: While the Linux file systems do not rely on extensions, some applications such as SciTE may attempt to use them to identify file types.

![6](https://github.com/rahulr98/CyberOps/assets/116432525/8f385407-639e-45ac-966b-d722989847cc)

i. Close space.txt when finished.

Question: Could you immediately find space.txt?

Yes when the 'all sources' was changed to 'all files' the txt file is opened.
Step 2: Open SciTE from the Terminal.
a. Alternatively, you can also open SciTE from the command line. Click the terminal icon located in the Dock at the bottom of the desktop. The terminal emulator opens.
b. Type ls to see the contents of the current directory. Notice space.txt is listed. This means you do not have to provide path information to open the file.
c. Type scite space.txt to open SciTE. Note that this will not only launch SciTE in the GUI, but it will also automatically load the space.txt text file that was previously created.

![8](https://github.com/rahulr98/CyberOps/assets/116432525/2f5ef10f-de81-43de-a495-59466d5d1d0c)

d. Notice that while SciTE is open on the foreground, the terminal window used to launch it is still open in the background. In addition, notice that the terminal window used to launch SciTE no longer displays the prompt. Question: Why is the prompt not shown in the terminal?
  - When the SciTE programs is launched, it runs in foreground and the terminal goes in backgorund. The terminal only shows the prompt when it is ready to accept any input, as it goes to backgorund it no longer receives any input.
e. Close this instance of SciTE by either clicking the X icon as before, or by switching the focus back to the terminal window that launched SciTE and stopping the process. You can stop the process by pressing CTRL+C. Note: Starting SciTE from the command line is helpful when you want to run SciTE as root. Simply precede scite with the sudo command, sudo scite.

![9](https://github.com/rahulr98/CyberOps/assets/116432525/e90a16c1-b560-4caa-80b8-9717d4b50fa1)

f. Close SciTE and move on to the next section.

## Part 2: Command Line Text Editors
  a. In the terminal window, type nano space.txt to open the text file created in Part 1. [analyst@secOps ~]$ nano space.txt image
  
![12](https://github.com/rahulr98/CyberOps/assets/116432525/a57a15b5-525d-4c4d-a9bc-bd3d96c3ad64)

  b. nano will launch and automatically load the space.txt text file. While the text may seem to be truncated or incomplete, it is not. Because the text was created with no return characters and line wrapping is not enabled, by default, nano is displaying one long line of text. Use the Home and End keyboard keys to quickly navigate to the beginning and to the end of a line, respectively. What character does nano use to represent that a line continues beyond the boundaries of the screen?

Nano uses the $ character to represent that a line continues beyond the boundaries of the screen. This character appears at the end of the line, indicating that there is more text to the right that cannot be displayed on the current screen. T
  c. As shown on the bottom shortcut lines, CTRL+X can be used to exit nano. nano will ask if you want to save the file before exiting (‘Y’ for Yes, or N for ‘No’). If ‘Y’ is chosen, you will be prompted to press enter to accept the given file name, or change the file name, or provide a file name if it is a new unnamed document.

  d. To control nano, you can use CTRL, ALT, ESCAPE or the META keys. The META key is the key on the keyboard with a Windows or Mac logo, depending on your keyboard configuration. Navigation in nano is very user friendly. Use the arrows to move around the files. Page Up and Page Down can also be used to skip forward or backwards entire pages. Spend some time with nano and its help screen. To enter the help screen, press CTRL+G. Press q to quit the help screen and return to document editing in nano.

## Part 3: Working with Configuration Files
  Step 1: Locating Configuration Files
  a. Use the ls command to list all the files in the analyst home directory:

![13](https://github.com/rahulr98/CyberOps/assets/116432525/5cc4f56c-6521-48a7-97fa-4e573300f58c)

While a few files are displayed, none of them seem to be configuration files. This is because it is convention to hide home-directory-hosted configuration files by preceding their names with a “.” (dot) character.

  b. Use the ls command again but this time add the –a option to also include hidden files in the output

![14](https://github.com/rahulr98/CyberOps/assets/116432525/72f03146-24fd-45fa-88dd-62db29c2f690)

  c. Use cat command to display the contents of the .bashrc file. This file is used to configure user-specific terminal behavior and customization. [analyst@secOps
  
![15](https://github.com/rahulr98/CyberOps/assets/116432525/61370ffc-7cce-41bc-8fff-02bd3dd4fc7d)

  d. While configuration files related to user applications are conventionally placed under the user’s home directory, configuration files relating to system-wide services are place in the /etc directory, by convention. Web services, print services, ftp services, and email services are examples of services that affect the entire system and of which configuration files are stored under /etc. Notice that regular users do not have writing access to /etc. This is important as it restricts the ability to change the system-wide service configuration to the root user only. Use the ls command to list the contents of the /etc directory: [analyst@secOps ~]$ ls /etc
  
![16](https://github.com/rahulr98/CyberOps/assets/116432525/e01a6256-5a2b-4b15-b812-b713ecec4242)

  e. Use the cat command to display the contents of the bash.bashrc file:

![17](https://github.com/rahulr98/CyberOps/assets/116432525/d52f0ecc-a203-450d-bf42-092a3359d980)

  Step 2: Editing and Saving Configuration files
  Let’s edit .bashrc to change the color of the shell prompt from green to red for the analyst user. 
  a. First, open SciTE by selecting Applications > CyberOPS > SciTE from the tool bar located in the upper portion of the Cisco CyberOPS VM screen. 
  b. Select File > Open to launch SciTE’s Open File window. 
  c. Because .bashrc is a hidden file with no extension, SciTE does not display it in the file list. If the Location feature is not visible in the dialog box, Change the type of file shown by selecting All Files (*) from the type drop box, as shown below. All the files in the analyst’s home directory are shown. 
  d. Select .bashrc and click Open.
  e. Locate 32 and replace it with 31. 32 is the color code for green, while 31 represents red.
  f. Save the file by selecting File > Save and close SciTE by clicking the X icon. g. Click the Terminal application icon located on the Dock, at the bottom center of the Cisco CyberOPS VM screen. The prompt should appear in red instead of green.
  
![19](https://github.com/rahulr98/CyberOps/assets/116432525/bb576a55-814e-4f97-9a9b-82b9b6be4754)
![20](https://github.com/rahulr98/CyberOps/assets/116432525/b15aef15-866b-4177-bc68-e8a7864a47ee)
![21](https://github.com/rahulr98/CyberOps/assets/116432525/cd690360-b443-4cb5-ac36-86fd8f5023ab)

  Question: Did the terminal window which was already open also change color from green to red? Explain.
       ANS: No,the prompt immediately did not change when the colour was changed in .bashrc. If we take a new tab the colour is changed. This may be beacuse it runs in backgroud.
  h. The same change could have been made from the command line with a text editor such as nano. From a new terminal window, type nano .bashrc to launch nano and automatically load the .bashrc file in it: [analyst@secOps ~]$ nano .bashrc

  i. Change 31 to 32. 32 is the color code to yellow. 

![22](https://github.com/rahulr98/CyberOps/assets/116432525/fdc1f902-bdfa-4ca5-9add-bf54d1eb3b75)
![23](https://github.com/rahulr98/CyberOps/assets/116432525/ba9c4198-bdc6-4237-af06-9a1d769eb47a)
![23](https://github.com/rahulr98/CyberOps/assets/116432525/c2e68889-66d4-4b7a-8b02-4fef8b52e4fb)
![24](https://github.com/rahulr98/CyberOps/assets/116432525/b3697afd-782f-4fec-aa7a-3b4b65eda7c8)

  j. Press CTRL+X to save and then press Y to confirm. The text editor nano will also offer you the chance to change the filename. Simply press ENTER to use the same name, .bashrc. k. The text editor nano will end, and you will be back on the shell prompt. This time reload the bash terminal by entering the command bash in the terminal. The prompt should now appear in yellow instead of red.
 
 Step 3: Editing Configuration Files for Services
  a. First, open nginx’s configuration file in a nano. The configuration file name used here is custom_server.conf. Notice below that the command is preceded by the sudo command. After typing nano include a space and the -l switch to turn on line-numbering. [analyst@secOps ~]$ sudo nano -l /etc/nginx/custom_server.conf
  b. While the configuration file has many parameters, we will configure only two: the port nginx listens on for incoming connections, and the directory it will serve web pages from, including the index HTML homepage file. 
  c. Notice that at the bottom of the window, above the nano commands, the line number is highlighted and listed. On line 39, change the port number from 81 to 8080. This will tell nginx to listen to HTTP requests on port TCP 8080. 
  d. Next, move to line 47 and change the path from /usr/share/nginx/html/ to /usr/share/nginx/html/text_ed_lab/ Note: Be careful not to remove the semi-colon at the end of the line or nginx will throw an error on startup. image
  
![27](https://github.com/rahulr98/CyberOps/assets/116432525/05fa86d8-7091-465c-9211-ed89a57ad29e)
![28](https://github.com/rahulr98/CyberOps/assets/116432525/39985a60-4eb3-4c3b-a5b9-3356d7573bf9)
![29](https://github.com/rahulr98/CyberOps/assets/116432525/5374b585-62f1-4399-ab19-f23fc49ff6e6)

  e. Press CTRL+X to save the file. Press Y and then ENTER to confirm and use the custom_server.conf as the filename. f. Type the command below to execute nginx using the modified configuration file: [analyst@secOps ~]$ sudo nginx -c custom_server.conf

  g. Click the web browser icon on the Dock to launch Firefox. h. On the address bar, type 127.0.0.1:8080 to connect to a web server hosted on the local machine on port 8080. A page related to this lab should appear. 8081.

![32](https://github.com/rahulr98/CyberOps/assets/116432525/4e4aa2bb-1a45-49a5-8a27-7fce0eb57e2c)

  i. After successfully opening the nginx homepage, look at the connection message in the terminal window.

![31](https://github.com/rahulr98/CyberOps/assets/116432525/b843cde4-cf4d-4eb4-87d7-cbf50ba41f16)
  
  j. To shut down the nginx webserver, press ENTER to get a command prompt and type the following command in the terminal window:
      - [analyst@secOps ~]$ sudo pkill nginx

![33](https://github.com/rahulr98/CyberOps/assets/116432525/ad59744b-bfca-43c1-b20b-49c27ee4d071)

Question: What is the error message referring to?
      ANS: The error message tells that inside the text_ed_lab no file called favicon.io is present. 
  
  k. You can test whether the nginx server is indeed shut down by first clearing the recent history in the web browser, then close and re-open the web browser, then go to the nginx homepage at 127.0.0.1:8080.
  
  Question: Does the web page appear?
       ANS:  yes, still it appears.
