<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Implementation (Azure)</h1>
On-premises Active Directory implementation within Azure Virtual Machines.<br />

<p> &emsp; </p>



<h2>Video Demonstration</h2>

- ### [YouTube: Active Directory implementation](https://youtu.be/kJ41bwvgI-g)
<p> &emsp; </p>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
<p> &emsp; </p>


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
<p> &emsp; </p>


<h2>High-Level Deployment and Configuration Steps</h2>

- Install AD DS
- Create Organizational Units and Users

<p> &emsp; </p>


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/HWQetzn.png" height="80%" width="80%" alt="server-manager"/>
</p>
<p>
- Login to the DC VM and Install Active Directory. <p></p>
[server manager -> add roles -> (rolebased) -> (select dc) -> check AD DS -> continue with defaults -> install]<p></p>
<p> &emsp; </p>
- After installation completes promote the system as Domain Controller.<p></p>
[server manager notifications -> "promote to DC" -> new forest -> set password -> continue with defaults -> install]<p></p>
<p> &emsp; </p>
- Restart the Domain Controller (or if the box was checked for it then a restart will happen automatically).
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>




<p>
<img src="https://i.imgur.com/seuJLgf.png" height="80%" width="80%" alt="users-and-computers"/>
</p>
<p>
- Log back into the Domain Controller (Specifying the domain name is required from now on).<p></p>
Syntax: [user@domain.local] or [domain.local\user] <p></p>
<p> &emsp; </p>
- Create Organizational Units. <p></p>
[start -> windows administrative tools -> active directory users and computers -> expand domain -> new -> organizational units] <p></p>
<p> &emsp; </p>
- Create an admin in an "ADMINS" Organizational Unit. <p></p>
[right-click OU -> new -> user -> set password -> right-click the new name -> member of -> "Domain Admins"]<p></p>
<p> &emsp; </p>
- Create a normal user in a separate OU. <p></p>
- Restart the Domain Controller and sign in using the newly created admin.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>




<p>
<img src="https://i.imgur.com/pPn8V86.jpeg" height="80%" width="80%" alt="client"/>
</p>
<p>
- Login to the client VM with its original user and join it to the domain.<p></p>
[start -> system -> rename this PC -> change -> member of -> YourDomain -> give admin credentials -> restart]<p></p>
<p> &emsp; </p>
- On the DC in "Users and Computers" our client should now be visible in the computers section.<p></p>
- Login to the client using the admin user and allow client access to non-administrator users.<p></p>
[start -> system -> remote desktop -> select users -> add -> "Domain Users"]<p></p>
<p> &emsp; </p>
- Normal users and admins are now able to use the client.
</p>
<br />

