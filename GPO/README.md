<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Group Policy Objects and Organizational Units</h1>
Organizational Units & Group Policy Objects usage.<br />
<p> &emsp; </p>



<h2>Video Demonstration</h2>

- ### [YouTube: Group Policy Objects & Organizational Units](https://youtu.be/WD1___7Z-ac)
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

- Create network folders for client sessions
- Create security groups to allow folder access to specific Organizational Units
- Remap network folder to become "E:" drive
- Create Group Policy Objects to set backgrounds based on Organization Units
<p> &emsp; </p>


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/0j3QGct.jpeg" height="80%" width="80%" alt="folder permissions"/>
</p>
<p>
-Create 2 new folders inside the C: drive on the Domain Controller, "admins" and "teams".<p></p>
-Share both folders on the network.<p></p>
[right click -> properties -> sharing -> share -> share]
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/NIWAtvC.jpeg" height="80%" width="80%" alt="sec groups"/>
</p>
<p>
-Create security groups for the ADMINS and TEAM Organizational Units.<p></p>
[right-click the appropriate OU -> new -> group -> "admin_sec" & repeat for "team_sec"]
<p> &emsp; </p>
-Add the members of the team OU to the team_sec group, and repeat for the admin_sec group.<p></p>
-Go back to the C: drive and set the new sec groups to their respective folders.<p></p>
[right-click -> security -> edit -> add -> (sec group)] & set allow Full control.<p>
and again in the sharing tab [advanced sharing -> permissions -> add -> (sec group)]
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
