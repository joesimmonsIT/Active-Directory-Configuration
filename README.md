<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory Configuration Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Resource Group
- Virtual Machines
- Static IP Address
- Virtual Machine Connectivity
- ICMP Traffic Access
- Active Directory Installation
- Creating Organizational Units in Active Directory
- Logging Out - Domain Controller
- Admin LogIn
- Connecting VM to Domain Controller
- Logging Into VM with Domain Admin
- Domain Users Access
- Creating Multiple Users
- Non-Admin User LogIn
- Password Reset

<h2> Resource Group </h2>

<p>
<img src="https://i.imgur.com/HGcJpqa.png"/>
</p>
<p>
Go to Azure Portal "(Portal.Azure.com)".
</p>
<br />

<p>
<img src="https://i.imgur.com/ei5RlmO.png"/>
</p>
<p>
Type "resource group" in the search bar. <br /> <br />
Select "Resource groups" from the search results. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/cXwBMX7.png"/>
</p>
<p>
Select "Create".
</p>
<br />

<p>
<img src="https://i.imgur.com/84GUS7h.png"/>
</p>
<p>
Subscription: Select appropriate subscription if you have more than one Azure subscription. <br /> <br />
If you only have one subscription skip this step and move on to the next step. <br /> <br />
Resource group: Select desired resource group name, for this tutorial we will be using "AD-Lab". <br /> <br />
Region: Select desired Region, for this tutorial we will be using "(US) East US". <br /> <br />
Select "Review + create". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/j499rQY.png"/>
</p>
<p>
Once all the steps are completed correctly you should see a green checkmark and the words "Validation passed". <br /> <br />
Select the "Create" button at the bottom to proceed with the creation of the Resource Group. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/AnEfpKB.png"/>
</p>
<p>
Resource Group "AD-Lab" has successfully been created.
</p>
<br />

<h2> Virtual Machines </h2>
<p>
<img src="https://i.imgur.com/KpkeCsk.png"/>
</p>
<p>
Go to Azure Portal "(Portal.Azure.com)". <br /> <br />
Type "Virtual machines" in the search bar. <br /> <br />
Select "Virtual machines" from the search results. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/kAzzpct.png"/>
</p>
<p>
Select "+ Create". <br /> <br />
Select "Azure virtual machine". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/pThCEAm.png"/>
</p>
<p>
Subscription: Select appropriate subscription if you have more than one Azure subscription. <br /> <br />
If you only have one subscription skip this step and move on to the next step. <br /> <br />
Resource group: Select desired resource group name, for this tutorial we will be using "AD-Lab". <br /> <br />
Virtual machine name: Select the desired virtual machine name, for this tutorial we will be using "DC-1". <br /> <br />
Region: Select desired Region, for this tutorial we will be using "(US) East US". <br /> <br />
Availability Zone: Select the desired zone, for this tutorial we will be using "Zone 2". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/qOstVjX.png"/>
</p>
<p>
Image: Select desired image, for this tutorial we will be using "Windows Server 2022".
</p>
<br />

<p>
<img src="https://i.imgur.com/f9Of4uG.png"/>
</p>
<p>
Size: Select the desired size, for this tutorial we will be using "Standard - 2 vcpus". <br /> <br />
Username: Select the desired Username, for this tutorial we will be using "labuser". <br /> <br />
Password: Create a password that you can easily remember or write down and easily retrieve. <br /> <br />
Confirm Password: Re-enter the same password from the previous step. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/ZSZ7rHn.png"/>
</p>
<p>
Select "Review + create".
</p>
<br />

<p>
<img src="https://i.imgur.com/BBuKbYm.png"/>
</p>
<p>
Once all the steps have been completed correctly you should see a green check mark and the words "Validation passed." <br /> <br />
Select "Create" to proceed with the creation of the virtual machine. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/70GJmRE.png"/>
</p>
<p>
The deployment (creation) of the virtual machine is in process to be completed.
</p>
<br />

<p>
<img src="https://i.imgur.com/qXJtdVF.png"/>
</p>
<p>
The creation of the virtual machine is completed. <br /> <br />
Select "Create another VM". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/g6hepnn.png"/>
</p>
<p>
Subscription: Select appropriate subscription if you have more than one Azure subscription. <br /> <br />
If you only have one subscription skip this step and move on to the next step. <br /> <br />
Resource group: Select desired resource group name, for this tutorial we will be using "AD-Lab". <br /> <br />
Virtual machine name: Select the desired virtual machine name, for this tutorial we will be using "Client-1". <br /> <br />
Region: Select desired Region, for this tutorial we will be using "(US) East US". <br /> <br />
Availability Zone: Select the desired zone, for this tutorial we will be using "Zone 2". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/fZjdeTQ.png"/>
</p>
<p>
For the Image select the desired image, for this tutorial we will be using "Windows 10 Pro".
</p>
<br />

<p>
<img src="https://i.imgur.com/iF6j01T.png"/>
</p>
<p>
Size: Select the desired size, for this tutorial we will be using "Standard - 2 vcpus". <br /> <br />
Username: Select the desired Username, for this tutorial we will be using "labuser". <br /> <br />
Password: Create a password that you can easily remember or write down and easily retrieve. <br /> <br />
Confirm Password: Re-enter the same password from the previous step. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/tcWbzdA.png"/>
</p>
<p>
Acknowledge the Licensing Confirmation by check the box, it should turn blue. <br /> <br />
Select "Review + Create" to proceed with creating the virtual machine. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/A8kpfzJ.png"/>
</p>
<p>
Once all the steps have been completed correctly you should see a green check mark and the words "Validation passed." <br /> <br />
Select "Create" to proceed with the creation of the virtual machine. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/2BBpkdF.png"/>
</p>
<p>
The deployment (creation) of the virtual machine is in process to be completed.
</p>
<br />

<p>
<img src="https://i.imgur.com/ecCpUcB.png"/>
</p>
<p>
The creation of the virtual machine is completed. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/apCJSva.png"/>
</p>
<p>
Type "virtual machines" in the search bar. <br /> <br />
Select "Virtual machines" from the search results. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/DYDBlb9.png"/>
</p>
<p>
Select "DC-1".
</p>
<br />

<h2> Static IP Address </h2>
<p>
<img src="https://i.imgur.com/oZHUddY.png"/>
</p>
<p>
Select "Networking". <br /> <br />
Collapse and Select "Network Settings". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/NL11K1A.png"/>
</p>
<p>
Select "Network Interface".
</p>
<br />

<p>
<img src="https://i.imgur.com/xmuqH9R.png"/>
</p>
<p>
Collapse "Settings". <br /> <br />
Select "IP configurations". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/8bVkH8P.png"/>
</p>
<p>
Select "ipconfig1".
</p>
<br />

<p>
<img src="https://i.imgur.com/dw8tIE4.png"/>
</p>
<p>
Change Allocation from Dynamic to "Static". <br /> <br />
Select "Save". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/sYlvCXh.png"/>
</p>
<p>
DC-1's Private IP Address is now set to Static.
</p>
<br />

<p>
<img src="https://i.imgur.com/EMSZKw3.png"/>
</p>
<p>
Select "Refresh".
</p>
<br />

<h2> Virtual Machine Connectivity </h2>
<p>
<img src="https://i.imgur.com/hskurKY.png"/>
</p>
<p>
Go to Azure Portal "(Portal.Azure.com)". <br /> <br />
Select "Virtual Machines" icon. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/e4oBR9M.png"/>
</p>
<p>
Select "Client-1".
</p>
<br />

<p>
<img src="https://i.imgur.com/8ndQOjf.png"/>
</p>
<p>
Copy Public IP Address.
</p>
<br />

<p>
<img src="https://i.imgur.com/HxaLDZo.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "Remote Desktop Connection" in search bar. <br /> <br />
Press "Enter". <br /> <br />
Paste Public IP Address. <br /> <br />
Select "Connect".<br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/L88uk3q.png"/>
</p>
<p>
Enter Username for the second virtual machine created, for this tutorial we will be using "labuser". <br /> <br />
Enter Password for the same virtual machine. <br /> <br />
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/iP2wrF4.png"/>
</p>
<p>
Select "Yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/yTLmjUL.png"/>
</p>
<p>
Return back to Virtual Machines. <br /> <br />
Select "DC-1". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/pDon5yc.png"/>
</p>
<p>
Scroll down to "Networking". <br /> <br />
Copy Private IP Address. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/LExTRRc.png"/>
</p>
<p>
Once Remote Desktop Connection is complete for Client-1 go to the Windows Pane. <br /> <br />
Type "cmd" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/wbNchX6.png"/>
</p>
<p>
Type "ping (spacebar)-t (spacebar)" Paste Private IP Address. <br /> <br />
Observer the message "Request time out", this is because of the Static Private IP Address for DC-1. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/27M8oHy.png"/>
</p>
<p>
Return back to Azure. <br /> <br />
Go to Virtual Machines. <br /> <br />
Select "DC-1". <br /> <br />
Copy Public IP Address. <br /> <br />
Go to Windows Pane. <br /> <br />
Type "Remote Desktop Connection" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
Paste Public IP Address. <br /> <br />
Select "Connect". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/y1uoTdL.png"/>
</p>
<p>
Enter Username for the first virtual machine created, for this tutorial we will be using "labuser". <br /> <br />
Enter Password for the same virtual machine. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/tcC5yfH.png"/>
</p>
<p>
Select "Yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/29uuySX.png"/>
</p>
<p>
Remote Desktop Connection for DC-1 is a success.
</p>
<br />

<h2> ICMP Traffic Access </h2>
<p>
<img src="https://i.imgur.com/v02SvcC.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "wf.msc" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/shCmWTN.png"/>
</p>
<p>
Select "Inbound Rules"
</p>
<br />

<p>
<img src="https://i.imgur.com/26JjUZl.png"/>
</p>
<p>
Select "Protocol" Column.
</p>
<br />

<p>
<img src="https://i.imgur.com/1r36vBL.png"/>
</p>
<p>
Sort "Protocol Column in ascending order.
</p>
<br />

<p>
<img src="https://i.imgur.com/Ct75Aup.png"/>
</p>
<p>
Locate "ICMPv4". <br /> <br />
Select the "2nd" entry.<br /> <br />
Right Click and "Enable Rule". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/MWouEwC.png"/>
</p>
<p>
Select "3rd entry - Local subnet"
</p>
<br />

<p>
<img src="https://i.imgur.com/ycKojGv.png"/>
</p>
<p>
Right Click and "Enable Rule".
</p>
<br />

<p>
<img src="https://i.imgur.com/eP0EK3Z.png"/>
</p>
<p>
Go back to Command Prompt. <br /> <br />
Observe the unlimited ICMP traffic flowing in. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/SZ0XIgw.png"/>
</p>
<p>
Select "Ctrl + C" to stop ICMP Traffic.
</p>
<br />

<h2> Active Directory Installation </h2>
<p>
<img src="https://i.imgur.com/29uuySX.png"/>
</p>
<p>
Select "Add roles and features".
</p>
<br />

<p>
<img src="https://i.imgur.com/RA4Qoyl.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/cwQoWzu.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/nQqCzIp.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/ZXC0a06.png"/>
</p>
<p>
Select "Active Directory Domain Services".
</p>
<br />

<p>
<img src="https://i.imgur.com/vmrpFN6.png"/>
</p>
<p>
Select "Add Features".
</p>
<br />

<p>
<img src="https://i.imgur.com/XNjLbJo.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/cb9jcZs.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/KpFOeqE.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/KwdX6wx.png"/>
</p>
<p>
Select "Install".
</p>
<br />

<p>
<img src="https://i.imgur.com/KjDJf8F.png"/>
</p>
<p>
Installation in progress.
</p>
<br />

<p>
<img src="https://i.imgur.com/d0p89bO.png"/>
</p>
<p>
Installation complete. <br /> <br />
Select "Close". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/G51cw64.png"/>
</p>
<p>
Click "Yellow" Icon.
</p>
<br />

<p>
<img src="https://i.imgur.com/4rkLAwf.png"/>
</p>
<p>
Select "Promote this server to a domain controller".
</p>
<br />

<p>
<img src="https://i.imgur.com/8Lg4O5P.png"/>
</p>
<p>
Select "Add a new forest". <br /> <br />
Root domain name: "mydomain.com". <br /> <br />
Select "Next". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/C9u8Lcz.png"/>
</p>
<p>
Password: Create Password. <br /> <br />
Confirm Password: Re-enter Password. <br /> <br />
Select "Next". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/kK1KZCh.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/In0F2YH.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/0uXnxaf.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/H41m8Pw.png"/>
</p>
<p>
Select "Next".
</p>
<br />

<p>
<img src="https://i.imgur.com/WRL6IeM.png"/>
</p>
<p>
Select "Install".
</p>
<br />

<p>
<img src="https://i.imgur.com/j4WMHDY.png"/>
</p>
<p>
Installation is complete. <br /> <br />
DC-1 automatic restared to enable Active Directory features. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/F0TqyR2.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "Remote Desktop Connection" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
Select "Connect". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/wOmQdUT.png"/>
</p>
<p>
Select "More choices". <br /> <br />
Select "Use a different account". <br /> <br />
Username: mydomain.com\labuser (since DC-1 is now a domain controller). <br /> <br />
Password: Same DC-1 Password. <br /> <br />
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/0inOwpI.png"/>
</p>
<p>
Select "Yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/vRSGscK.png"/>
</p>
<p>
Active Directory is ready for engagement.
</p>
<br />

<h2> Creating Organizational Units in Active Directory </h2>

<p>
<img src="https://i.imgur.com/BoZxfUs.png"/>
</p>
<p>
Select "Tools".
</p>
<br />

<p>
<img src="https://i.imgur.com/2278rKb.png"/>
</p>
<p>
Select "Active Directory Users and Computers".
</p>
<br />

<p>
<img src="https://i.imgur.com/Xayee8Q.png"/>
</p>
<p>
Select "mydomain.com".
</p>
<br />

<p>
<img src="https://i.imgur.com/TMKkb0m.png"/>
</p>
<p>
Right Click. <br /> <br />
Select "New". <br /> <br />
Select "Organizational Unit". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/xaXsztB.png"/>
</p>
<p>
Name: "_EMPLOYEES".<br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/3PXo0VZ.png"/>
</p>
<p>
"_EMPLOYEES" Organizational Unit has been successfully created and added to "mydomain.com" Domain Controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/kERBs4p.png"/>
</p>
<p>
Select "mydomain.com". <br /> <br />
Right Click and Select "New". <br /> <br />
Select "Organizational Unit". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/9GopHTQ.png"/>
</p>
<p>
Name: "_ADMINS". <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/YoRtXgY.png"/>
</p>
<p>
Select "mydomain.com". <br /> <br />
Right Click and Select "Refresh". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/lpQyaNw.png"/>
</p>
<p>
Select "_ADMINS". <br /> <br />
Right Click and Select "New". <br /> <br />
Select "User". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/Kd3mxTC.png"/>
</p>
<p>
First Name: "Jane". <br /> <br />
Last Name: "Doe". <br /> <br />
Full Name: "Jane Doe". <br /> <br />
Username logon name: "jane_admin". <br /><br />
Select "Next". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/iBGHPWj.png"/>
</p>
<p>
Password: Create a Password. <br /> <br />
Confirm Password: Re-enter same Password. <br /> <br />
Uncheck "User must change password at next login". <br /> <br />
Check "Password never expires". <br /> <br />
Select "Next". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/qZh3ijY.png"/>
</p>
<p>
Select "Finish".
</p>
<br />

<p>
<img src="https://i.imgur.com/o7u7Vox.png"/>
</p>
<p>
Select "Jane Doe".
</p>
<br />

<p>
<img src="https://i.imgur.com/fsrmvq0.png"/>
</p>
<p>
Right Click and Select "Properties".
</p>
<br />

<p>
<img src="https://i.imgur.com/KccTtm8.png"/>
</p>
<p>
Select "Member Of".
</p>
<br />

<p>
<img src="https://i.imgur.com/0lHpYID.png"/>
</p>
<p>
Select "Add".
</p>
<br />

<p>
<img src="https://i.imgur.com/5YytGDw.png"/>
</p>
<p>
Type "domain". <br /> <br />
Select "Check Names". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/fRZTQyY.png"/>
</p>
<p>
Select "Domain Admins". <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/i8bdPz8.png"/>
</p>
<p>
Select "OK".
</p>
<br />

<p>
<img src="https://i.imgur.com/MhsoDUt.png"/>
</p>
<p>
Select "Apply".
</p>
<br />

<p>
<img src="https://i.imgur.com/RREdbLx.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/wAbHDnh.png"/>
</p>
<p>
Jane Doe "Access" preferences has been updated.
</p>
<br />

<h2> Logging Out - Domain Controller </h2>
<p>
<img src="https://i.imgur.com/DYgYzK7.png"/>
</p>
<p>
Go to the Windows Pane. <br /> <br />
Type "cmd" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/TVokNia.png"/>
</p>
<p>
Type "whoami" and Press "Enter". <br /> <br />
Type "logoff" and Press "Enter". <br /> <br />
</p>
<br />

<h2> Admin LogIn </h2>
<p>
<img src="https://i.imgur.com/aREsgzp.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "Remote Desktop Connection" in search bar. <br /> <br />
Press "Enter". <br /> <br />
Select "Connect". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/SEVWlvW.png"/>
</p>
<p>
Select "More choices". <br /> <br />
Select "Use a different account". <br /> <br />
Username: mydomain.com\jane_admin. <br /> <br />
Password: Enter Administrator Password. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/0jnOcR1.png"/>
</p>
<p>
Select "Yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/pmPLDIz.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "cmd" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
Type "whoami". <br /> <br />
We have successfully logged in as Domain Admin. <br /> <br />
</p>
<br />

<h2> Connecting VM to Domain Controller </h2>
<p>
<img src="https://i.imgur.com/p6vunsn.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Right Click "Start" button. <br /> <br />
Select "System". <br /> <br />
Select "Rename this PC (advanced)". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/lvSiko5.png"/>
</p>
<p>
Select "Change".
</p>
<br />

<p>
<img src="https://i.imgur.com/SWMaftu.png"/>
</p>
<p>
Select "Domain". <br /> <br />
We need to change the DNS Server for Client-1. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/GURrPUG.png"/>
</p>
<p>
Go to Azure Portal "(Portal.Azure.com)". <br /> <br />
Select "Virtual Machines" icon. <br /> <br />
Select "DC-1". <br /> <br />
Collapse "Networking". <br /> <br />
Select "Network settings". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/QEiiNGX.png"/>
</p>
<p>
Copy "Private IP Address".
</p>
<br />

<p>
<img src="https://i.imgur.com/1fbwLsx.png"/>
</p>
<p>
Go to "Virtual Machines". <br /> <br />
Select "Client-1". <br /> <br />
Collapse "Networking". <br /> <br />
Select "Network settings". <br /> <br />
Select "Network interface". <br /> <br />
Collapse "Settings". <br /> <br />
Select "DNS Servers". <br /> <br />
Select "Custom". <br /> <br />
Paste Private IP Address in DNS Server. <br /> <br />
Select "Save". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/ZafpFAz.png"/>
</p>
<p>
Go to "Virtual Machines". <br /> <br />
Select "Client-1". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/3nzdft9.png"/>
</p>
<p>
Select "Restart". <br /> <br />
Select "Yes". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/bSlhtvF.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "Remote Desktop Connection" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
Go to "Virtual Machines". <br /> <br />
Select "Client-1". <br /> <br />
Copy Public IP Address. <br /> <br />
Paste Public IP Address. <br /> <br />
Select "Connect". <br /> <br />
Select "More choices". <br /> <br />
Select "Use a different account". <br /> <br />
Username: mydomain.com\labuser. <br /> <br />
Password: Enter Client-1 Password. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/GfJXE01.png"/>
</p>
<p>
Select "Yes".
</p>
<br />

<p>
<img src="https://i.imgur.com/TbdblfN.png"/>
</p>
<p>
Go to Windows Pane. <br /> <br />
Type "cmd" in the search bar. <br /> <br />
Press "Enter". <br /> <br />
Type "whoami" and Press "Enter". <br /> <br />
Type "hostname" and Press "Enter". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/9ahDW5a.png"/>
</p>
<p>
Type "ipconfig (spacebar) /all" and Press "Enter". <br /> <br />
Observe that the DNS Server is the same as the Private IP Address for the Domain Controller. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/6rjlP63.png"/>
</p>
<p>
Select the "Start" button. <br /> <br />
Right Click and Select "System". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/Unubueh.png"/>
</p>
<p>
Select "Rename this PC (advanced)".
</p>
<br />

<p>
<img src="https://i.imgur.com/qCIn7UE.png"/>
</p>
<p>
Select "Change".
</p>
<br />

<p>
<img src="https://i.imgur.com/b6PJJ1p.png"/>
</p>
<p>
Select "Domain" and type "mydomain.com". <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/o6qxp6q.png"/>
</p>
<p>
Enter Domain Admin Username: "mydomain.com\jane_admin. <br /> <br />
Enter Domain Admin Password: ***********. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/L9Fl1HG.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/I1nQxqq.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/twcj6hn.png"/>
</p>
<p>
Select "Close".
</p>
<br />

<p>
<img src="https://i.imgur.com/RW4R9w5.png"/>
</p>
<p>
Select "Restart Now".
</p>
<br />

<h2> Logging Into VM with Domain Admin </h2>

<p>
<img src="https://i.imgur.com/gHZDpzj.png"/>
</p>
<p>
Go to "Remote Desktop Connection". <br /> <br />
Select "Connect". <br /> <br />
Enter Domain Admin Username. <br /> <br />
Enter Domain Admin Password. <br /> <br />
Select "Ok". <br /> <br />
Select "Yes". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/0c91W9F.png"
</p>
<p>
Go to "Command Prompt". <br /> <br />
Type "whoami" and Press "Enter". <br /> <br />
Type "hostname" and Press "Enter". <br /> <br />
Observe we have successfully logged into Client-1 as Domain Admin. <br /> <br />
</p>
<br />

<h2> Domain Users Access </h2>
<p>
<img src="https://i.imgur.com/uaqJ2BK.png"/>
</p>
<p>
Right Click the "Start" button. <br /> <br />
Select "System". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/RBbZaki.png"/>
</p>
<p>
Select "Remote desktop".
</p>
<br />

<p>
<img src="https://i.imgur.com/93WiJIA.png"/>
</p>
<p>
Select "Select users that can remotely access this PC".
</p>
<br />

<p>
<img src="https://i.imgur.com/FsEEIKm.png"/>
</p>
<p>
Click "Add".
</p>
<br />

<p>
<img src="https://i.imgur.com/0laJVWH.png"/>
</p>
<p>
Type "domain" and Select "Check Names".
</p>
<br />

<p>
<img src="https://i.imgur.com/sGtWxwL.png"/>
</p>
<p>
Select "Domain Users". <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/rjnjB4F.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<p>
<img src="https://i.imgur.com/Cdf4F8F.png"/>
</p>
<p>
Select "Ok".
</p>
<br />

<h2> Creating Multiple Users </h2>
<p>
<img src="https://i.imgur.com/7sdhn6j.png"/>
</p>
<p>
Go to the Windows Pane. <br /> <br />
Type "powershell" in the search bar. <br /> <br />
Select "Windows Powershell ISE" from search results. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/Ue1ueKi.png"/>
</p>
<p>
Powershell is ready for use.
</p>
<br />

<p>
<img src="https://i.imgur.com/nAHdRmf.png"/>
</p>
<p>
Select the "white sheet" to start a new script.
</p>
<br />

<p>
<img src="https://i.imgur.com/TT0eDq5.png"/>
</p>
<p>
Copy and Paste the Create Multiple Users script.
</p>
<br />

<p>
<img src="https://i.imgur.com/0feUl5i.png"/>
</p>
<p>
Select "Run Script".
</p>
<br />

<p>
<img src="https://i.imgur.com/CyIIrDU.png"/>
</p>
<p>
Observe the new users being created.
</p>
<br />

<p>
<img src="https://i.imgur.com/SEmP06V.png"/>
</p>
<p>
Go to "Active Directory". <br /> <br />
Select "_EMPLOYEES". <br /> <br />
Right Click and Select "Refresh". <br /> <br />
</p>
<br />

<h2> Non-Admin User LogIn </h2>
<p>
<img src="https://i.imgur.com/MKjUrn0.png"/>
</p>
<p>
Go to "Command Prompt". <br /> <br />
Type "logoff" and Press "Enter". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/AY2wMUY.png"/>
</p>
<p>
Go back to "Active Directory". <br /> <br />
Select an employee. <br /> <br />
Right Click and Select "Properties". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/PdxYMur.png"/>
</p>
<p>
Select "Account". <br /> <br />
Document the employee's username. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/xITpBD6.png"/>
</p>
<p>
Go back to your "Computer". <br /> <br />
Open "Remote Desktop Connection". <br /> <br />
Press "Connect". <br /> <br />
Enter the employee's username. <br /> <br />
Enter the employee's password. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/06vyvxG.png"/>
</p>
<p>
Go to "Command Prompt". <br /> <br />
Type "whoami" and Press "Enter". <br /> <br />
Type "hostname" and Press "Enter". <br /> <br />
We have successfully logged into Client-1 with the employee credentials you selected from Active Directory. <br /> <br />
</p>
<br />

<h2> Password Reset </h2>
<p>
<img src="https://i.imgur.com/sea0WKB.png"/>
</p>
<p>
Go to Active Directory. <br /> <br />
Select "_EMPLOYEES". <br /> <br />
Select desired employee. <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/UZvz3lu.png"/>
</p>
<p>
Right Click and Select "Properties".
</p>
<br />

<p>
<img src="https://i.imgur.com/9cGCa1T.png"/>
</p>
<p>
Select "Account".
</p>
<br />

<p>
<img src="https://i.imgur.com/h7Do3sp.png"/>
</p>
<p>
Select "Unlock account". <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/V6vHaiH.png"/>
</p>
<p>
The 2nd option to password reset the employee's password is the following: <br /> <br />
Select "_EMPLOYEES". <br /> <br />
Select desired employee. <br /> <br />
Right Click and Select "Reset Password". <br /> <br />
</p>
<br />

<p>
<img src="https://i.imgur.com/mEh5gZB.png"/>
</p>
<p>
There are several options to reset the password: <br /> <br />
(1) Create a new password. <br /> <br />
(2) Allow the option to change password at next login. <br /> <br />
(3) Unlock the user's account. <br /> <br />
Select the desired preferences. <br /> <br />
Select "Ok". <br /> <br />
</p>
<br />


<p>
<img src="https://i.imgur.com/IcMoVCv.png"/>
</p>
<p>
The Employee's password should be resetted. <br /> <br />
Congratulations you have successfully completed this tutorial. <br /> <br />
</p>
<br />
