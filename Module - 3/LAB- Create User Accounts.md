## Part 1: Creating a New Local User Account
Step 1: Open the User Account Tool.

a. Log on to the Windows PC with an Administrator account. The account CyberOpsUser is used in this example.

b. Click Start > search Control Panel. Select User Accounts in the Small icons view. To change the view, select Small icons in the View by drop down list.

Step 2: Create a user account.

a. In the User Accounts window, click Manage another account.

b. In the Manage Accounts window, click Add a new user in PC settings.

c. In the Settings window, click Add someone else to this PC.

d. In the How will this person sign in? window, click I don't have this person's sign-in information.

e. In the Let's create your account window opens, click Add a user without a Microsoft account.

f. In the Create an account for this PC window, provide the necessary information to create the new user account named User1. Click Next to create the new user account.

Question: What type of user account did you just create?

Created a local user account. It is a user account that is not linked to a Microsoft account and is specific to the computer where it was created.

g. Attempt to log into the newly created user account. It should be successful.

h. Navigate to C:\Users folder. Right-click the User1 folder and select Properties, and then the Security tab.

Question: Which groups or users have full control of this folder? Type your answers here.

i. Open the folder that belongs to CyberOpsUser. Right-click the folder and click the Properties tab.Question: Were you able to access the folder? Explain. Type your answers here.

j. Log out of User1 account. Log back in as CyberOpsUser.

k. Navigate to C:\Users folder. Right-click the folder and select Properties. Click the Security tab.Question: Which groups or users have full control of this folder?

![image](https://user-images.githubusercontent.com/116432525/236697845-77de1986-47d6-48ca-b2c1-cce737b75904.png)

i. Open the folder that belongs to CyberOpsUser. Right-click the folder and click the Properties tab.Question: Were you able to access the folder? Explain.
j. Log out of User1 account. Log back in as CyberOpsUser. 
k. Navigate to C:\Users folder. Right-click the folder and select Properties. Click the Security tab.Question: Which groups or users have full control of this folder?

![image](https://user-images.githubusercontent.com/116432525/236697920-eda71e40-b471-4456-aede-1a8fc2f7fe3d.png)

## Part 2: Reviewing User Account Properties
a. Click Start > Search for Control Panel > Select Administrative Tools > Select Computer Management. b. Select Local Users and Groups. Click the Users folder.

## Part 3: Modifying Local User Accounts
Step 1: Change the account type

a. Navigate to the Control Panel and select User Accounts. Click Manage another account. Select User1. 
b. In the Change an Account window, click the User1 account. Click Change the account type. 
c. Select the Administrator radio button. Click Change Account Type. 
d. Now the account User1 has administrative rights.

![image](https://user-images.githubusercontent.com/116432525/236699218-e082da13-bddb-4f90-9ac8-36e1b8a1a98b.png)

e. Navigate to Control Panel > Administrative Tools > Computer Management.

Click Local Users and Groups> Users. f. Right-click User1 and select Properties.

Step 2: Delete the account.

a. To delete the account, right-click User1and select Delete.

b. Click OK to confirm the deletion.

Question: What is another way to delete a user account?

![image](https://user-images.githubusercontent.com/116432525/236699192-9c9a108d-c2e7-4d73-b300-f223d27cb1cd.png)

### Reflection Questions

Why is it important to protect all accounts with strong passwords?
  - Protecting user accounts with strong passwords is essential because weak passwords can leave accounts vulnerable to hacking, identity theft, and other cyber attacks. When an account is hacked, the attacker may gain access to sensitive information, such as personal information, financial information, or sensitive business data. This information can be used for a variety of malicious purposes, including identity theft, financial fraud, or corporate espionage. In addition, a hacked account may be used to launch attacks on other users, further propagating the cyber threat.
Why would you create a user with Standard privileges?
  - Creating a user account with standard privileges is a common practice in computer security to ensure that the user has limited access to the system and its resources.

