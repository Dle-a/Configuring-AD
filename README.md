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

- Step 1
- Step 2
- Step 3
- Step 4

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
![Screenshot 2025-02-18 201734](https://github.com/user-attachments/assets/978a17d8-509f-4bdb-82f9-88061536fa91)
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
