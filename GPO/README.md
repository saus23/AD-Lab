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
- Create 2 new folders inside the C: drive on the Domain Controller, "admins" and "teams".<p></p>
- Share both folders on the network.<p></p>
[right click -> properties -> sharing -> share -> share]
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/NIWAtvC.jpeg" height="80%" width="80%" alt="sec groups"/>
</p>
<p>
- Create security groups for the ADMINS and TEAM Organizational Units.<p></p>
[right-click the appropriate OU -> new -> group -> "admin_sec" & repeat for "team_sec"]
<p> &emsp; </p>
- Add the members of the team OU to the team_sec group, and repeat for the admin_sec group.<p></p>
- Go back to the C: drive and set the new sec groups to their respective folders.<p></p>
[right-click -> security -> edit -> add -> (sec group)] & set allow Full control.<p>
and again in the sharing tab [advanced sharing -> permissions -> add -> (sec group)]<p></p>
<p> &emsp; </p>
- Restart the client for access to the new folders ("pgupdate /force" may work but I had no luck with it here).
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/Q5NHIZw.jpeg" height="80%" width="80%" alt="drive remap"/>
</p>
<p>
- Create a new Group Policy Object for the ADMINS and TEAM Organizational Units.<p></p>
[start -> group policy management -> expand domain -> right-click OU -> "create GPO & link here"]<p></p>
<p> &emsp; </p>
- Edit the new GPOs to remap the network folder to be drive E: on clients.<p></p>
[right-click GPO -> edit -> user config -> preferences -> drive maps -> new -> mapped drive -> action: create -> location: \\dc\admins -> use first available: E -> show this drive -> common tab -> highlight item-level targeting -> new item (OU)]<p></p>
<p> &emsp; </p>
- Run "gpupdate /force" and a new E: drive is visible on client with the contents from the folders on the Domain Controller.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>

<p>
<img src="https://i.imgur.com/Wb8vafY.jpeg" height="80%" width="80%" alt="wallpapers"/>
</p>
<p>
- Find different desktop wallpapers for the TEAM and ADMINS Organizational Units & place them in their respective folders.<p></p>
- For simplicity save them as admin_wp.jpg and client_wp.jpg<p></p>
- Return to Group Policy Management and set wallpapers for OUs.<p></p>
[right-click GPO -> edit -> user config -> admin templates -> desktop -> desktop -> desktop wallpaper -> enable -> wallpaper name: \\dc\admin_wp.jpg]<p></p>
<p> &emsp; </p>
- Repeate for TEAM GPO and restart the machines.<p></p>
- The machines will now show a background based on the OU of the user.
</p>
<br />
