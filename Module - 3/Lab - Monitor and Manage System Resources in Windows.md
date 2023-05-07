### Part 1: Starting and Stopping the Routing and Remote Access service

You will explore what happens when a service is stopped and then started. In this part, you will use routing and remote access service as the example service. This service allows the local device to become a router or a remote access server.

a. Navigate to the Control Panel > Click Network and Sharing Center. Note: If your Control Panel is set to View by: Category, change it to View by: Large icons or View by: Small icons. This lab assumes that you are using one of these settings.

b. Click Change adapter settings in the left pane. Reduce the size of the Network Connections window and leave it open.

c. Navigate to the Administrative Tools. (Navigate to the Control Panel > Click Administrative Tools)

d. In the Administrative Tools window, double-click the Performance Monitor icon.

e. In the Performance Monitor window, make sure Performance Monitor under Monitoring Tool heading in the left pane is highlighted. Click the Freeze Display icon (pause button) to stop the recording.

![image](https://user-images.githubusercontent.com/116432525/236702679-181ce9ed-a307-4eb7-8f07-d0d1910dbbca.png)

f. Right-click the graph and select Clear to clear the graph. Leave this window open.

g. Navigate to the Administrative Tools and select Services.

h. Expand the width of the Services window so you have a clear view of the content. Scroll down in the right pane until you see the service Routing and Remote Access. Double-click Routing and Remote Access.

![image](https://user-images.githubusercontent.com/116432525/236702750-033cc125-6d53-4776-8a1f-f7324e922192.png)

i. In the Routing and Remote Access Properties (Local Computer) window opens. In the Startup type drop-down field, select Manual and then click Apply.

![image](https://user-images.githubusercontent.com/116432525/236702765-ae57d1cf-7574-42f2-a942-a9b2477226da.png)

The Start button is now active. Do NOT click the Start button yet. Leave this window open.

j. Navigate to Performance Monitor window. Click the Unfreeze Display icon to start the recording.

k. Click the Routing and Remote Access Properties (Local Computer) window. To start the service, click Start. A window with a progress bar opens.

![image](https://user-images.githubusercontent.com/116432525/236702958-91c6cae9-bd50-4508-a425-e25befc44677.png)

l. The Routing and Remote Access Properties (Local Computer) window now shows the Stop and Pause button active. Leave this window open.

m. Navigate to Network Connections window. Press the function key F5 to refresh the content.

Question:What changes appear in the window after starting the Routing and Remote Access service?

![image](https://user-images.githubusercontent.com/116432525/236702992-ddf3b490-8b53-4d3b-b343-bb3da4714f38.png)

n. Navigate to Routing and Remote Access Properties (Local Computer) window and click Stop. This was the page when Routing and Remote Access Properties

![image](https://user-images.githubusercontent.com/116432525/236703016-93eb184a-bf09-492c-b9c1-ff356d3b9aaa.png)

  - Now the Incoming Network Connections got killed.

![image](https://user-images.githubusercontent.com/116432525/236703040-7ed54ab0-15d3-4977-a01e-e1d4bf628ffe.png)

## Part 2: Working in the Computer Management Utility

The Computer Management is used to manage a local or remote computer. The tools in this utility are grouped into three categories: system tools, storage, and services and applications.

a. Click Control Panel > Administrative Tools. Select Computer Management.

b. In the Computer Management window, expand the three categories by clicking on the arrow next to System Tools.

c. Click the arrow next to Event Viewer then click the arrow next to Windows Logs. Select System.

![image](https://user-images.githubusercontent.com/116432525/236703111-bf1b603e-2a54-4dc0-8556-556190c70e96.png)

d. The Event Properties window opens for the first event. Click the down arrow key to locate an event for Routing and Remote Access. You should find four events that describe the order for starting and stopping the Routing and Remote Access service. 

![image](https://user-images.githubusercontent.com/116432525/236703167-91fc6532-630a-4b4d-bbdb-775ee8c85a92.png)

What are the descriptions for each of the four events?

![image](https://user-images.githubusercontent.com/116432525/236703201-0e72063e-9649-49e3-aadb-0545000dc029.png)
![image](https://user-images.githubusercontent.com/116432525/236703210-b0a5d591-68c5-4bc3-a424-cd251f7d2d9b.png)

e. Close all open windows.

Part 3: Configuring Administrative Tools
For the rest of this lab, you will configure Advanced Administrative Tool features and monitor how this affects the computer.

a. Click Control Panel > Administrative Tools > Performance Monitor. The Performance Monitor window opens. Expand Data Collector Sets. Right-click User Defined, and select New > Data Collector Set

b. The Create new Data Collector Set window opens. In the Name field, type Memory Logs. Select the Create manually (Advanced) radio button, and click Next.

c. In the What type of data do you want to include? window, check the Performance counter box then click Next.

d. In the Which performance counters would you like to log? window, click Add.

e. From the list of available counters, locate and expand Memory. Select Available MBytes and click Add>>.

![image](https://user-images.githubusercontent.com/116432525/236703251-d78c651b-aa43-4115-a5d3-4aced8eba8ee.png)

f. You should see the Available MBytes counter added in the right pane. Click OK.

g. Set the Sample interval field to 4 seconds. Click Next

h. In the Where would you like the data to be saved? screen, click Browse.

i. In the Browse For Folder window , select your (C:) drive which is Local Disk (C:). Select PerfLogs and click OK.

j. The Where would you like the data to be saved? window opens with the directory information that you selected in the previous step. Click Next.

k. In the Create the data collector set? screen, click Finish.

l. Expand User Defined and select Memory Logs. Right-click Data Collector01and select Properties.

![image](https://user-images.githubusercontent.com/116432525/236703551-4a4ba0ee-8659-4029-9343-77682af0ea3a.png)

m. In the DataCollector01 Properties window, chhange the Log format: field to Comma Separated.

![image](https://user-images.githubusercontent.com/116432525/236703571-bd7fb470-a82f-4fb7-8348-466d2347283b.png)

n. Click the File tab.

Question:What is the full path name to the example file?

![image](https://user-images.githubusercontent.com/116432525/236703587-2eecc19b-5bc5-4226-a9b1-db6828d52970.png)

o. Click OK

p. Select the Memory Logs icon in the left pane of the Performance Monitor window. Click the green arrow icon to start the data collection set. Notice a green arrow is placed on top of the Memory Logs icon.

q. To force the computer to use some of the available memory, open and close a browser.

r. Click the black square icon to stop the data collection set.

s. Click Start > Computer,and click drive C: > PerfLogs. Locate the folder that starts with your PC’s name followed by a timestamp, DESKTOP-NDFE14H_20170514-000001 in the example. Double-click the folder to open it, and then double-click the DataCollector01.csv file. If prompted, click Continue to permit access to the folder.

t. Close the DataCollector01.csv file and the window with the PerfLogs folder.

u. Select the Performance Monitor window. Right-click Memory Logs > Delete.

![image](https://user-images.githubusercontent.com/116432525/236703667-21272a62-eeb5-40c8-8e2d-a922f8555b88.png)

v. The Performance Monitor > Confirm Delete window opens. Click Yes.

w. Open drive C: > PerfLogs folder. Right-click on the folder that was created to hold the Memory log file, then click Delete.

x. The Delete Folder window opens. Click Yes.

y. Close all open windows.
