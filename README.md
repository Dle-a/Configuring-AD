<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1> Active Directory Configurations in Azure</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>


<h2>Deployment and Configuration Steps</h2>

<p>
<img width="893" alt="image" src="https://github.com/user-attachments/assets/c1459726-67d6-4a06-8c63-6105fcfdea02" />
</p> Needs one more pictire above 



Now that Active Directory is installed on the domain controller VM, it is time to create new Organizational Units and Users. With the Active Directory Users and Computers console open, right click on the domain you created (in my case, ernestotest.com) and make a new Organizational Unit (OU). I have created two Organizational Units, _EMPLOYEES and _ADMINS. The reason behind this naming scheme is because a Powershell script will be utilized later. Within the _ADMINS OU, I created a new User called Jane Doe. Jane's account will be given administrative privileges through the use of a Security Group. To grant admin privileges to a User, right click on the user and open their Properties. Click Member Of then Add to apply the appropraite security group. In this case, I added Jane to the Domain Admins security group. From now on, I will be using Jane's account to make any further changes. I will be logging off as labuser and log in as jane_admin.







<img width="784" alt="image" src="https://github.com/user-attachments/assets/416bde1d-85ac-4a7b-92c9-8cd002fe679d" />

<p>
Before the client can join the domain, it is important to configure the DNS settings first. The DNS server has to pointing to the domain controller's private IP address. On the Azure portal, open the Networking tab and click on Network Interface. In the DNS servers, enter the domain controller's private IP address and save the changes. Restart the client VM in order to ensure the DNS changes are saved.

</p>
<br />

<p>
<img width="694" alt="image" src="https://github.com/user-attachments/assets/e9ef09d9-2929-4eb0-b4e9-430de1b39466" />
</p>
<p>
It is now time to make the client VM join the domain. In the System menu of the client VM, click on Rename this PC (advanced) and Change. Enter the domain and necessary credentials in order to let the client join the domain. I am logging in as Jane Doe for the purposes of the lab. It is important to note that the login credentials have to be input within the context of the domain path. The client should now be part of the domain. On the domain controller, the client should now appear in Computers in the Active Directory Users and Computers panel.

</p>
<br />

<p>
<img width="407" alt="image" src="https://github.com/user-attachments/assets/90b5fcf8-a5ed-457b-952a-9560b38be4ee" />
</p>
<p>
Before users in the domain can use the client computer, Remote Desktop has to be enabled for non-administrative users. While logged in as the administrator (in my case, Jane), open System Properties. Click on Remote Desktop and Select users that can remotely access this PC. Allow Domain Users access to Remote Desktop. Non-administrative users can now log in to Client-1. Normally a Group Policy can do the same and allows changes to many systems at once. For the purposes of this lab, a Group Policy won't be used to make this change.

<img width="796" alt="image" src="https://github.com/user-attachments/assets/a34b14dc-beb2-4438-8435-af947a935642" />

</p>
<img width="805" alt="image" src="https://github.com/user-attachments/assets/7020e834-61c3-4ba1-be7a-b01a150d51e6" />

<img width="863" alt="image" src="https://github.com/user-attachments/assets/bffb8fd3-0594-4c1f-94aa-d861530fe433" />

After creating the users, Client-1 can now be signed in as one of the new users that were created from the PowerShell script. Pick a name and simply sign in to the client with the context of the domain. In my case, it is ernestotest.com\bon.rovej.


<br />
Doing this lab has made me learn how to set up Active Directory and join clients to the domain. I also created users and assigned the necessary permissions. Active Directory is not difficult to learn despite all the menu navigation that takes place. This lab is a segway for me to learn about DNS settings in-depth and file permissions in action. I will go into detail about these topics in other labs.

