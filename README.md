<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Azure configuration</h1>
Configuring the Azure environment for Active Directory.<br />
<p> &emsp; </p>



<h2>Video Demonstration</h2>

- ### [YouTube: Azure Setup](https://youtu.be/_UdS9Mp0wXY)
<p> &emsp; </p>


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell
- Windows Firewall
<p> &emsp; </p>


<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)
<p> &emsp; </p>


<h2>High-Level Deployment and Configuration Steps</h2>

- create resource group
- create virtual network
- create VMs
- make firewall rule
- test local network
<p> &emsp; </p>


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/UbUIUev.png" height="80%" width="80%" alt="VMs"/>
</p>
<p>
-Make a resource group, then add a virtual network onto it.<p></p>
-Create a windows server VM and a windows 10 VM in the resource group, both using the VNet created earlier.<p></p>
-The server VM will be our domain controller and win 10 the client.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>

  
<p>
<img src="https://i.imgur.com/Gb9fqcg.png" height="80%" width="80%" alt="static-IP"/>
</p>
<p>
-Set the Domain Controller VM's IP to be static since it will be the DNS server for our client.<p></p>
[VM -> networking -> network settings -> NIC -> ipconfig1 -> static & save] <p></p>
-Take note of the domain controller's private IP.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/Karf5lO.png" height="80%" width="80%" alt="setting-dns"/>
</p>
<p>
-Make the client's IP static as well, we will allow firewall traffic from its IP address later.<p></p>
-Set the client's DNS settings to point to DC's private address.<p></p>
[VM -> networking -> network settings -> NIC -> DNS servers -> custom -> <DC's private> & save]<p></p>
-Restart the client VM to make sure changes went through.
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/m9w94e4.jpeg" height="80%" width="80%" alt="firewall-rule"/>
</p>
<p>
-Boot the VMs and attempt to ping the domain VM's private IP from the client (It will fail). <p></p>
-Allow ICMPv4 traffic from the clients private IP.<p></p>
[run -> "wf.msc" -> inbound rules -> new rule -> custom -> all programs -> protocol ICMPv4 -> remote = client's private]
</p>
<br />
<p> &emsp; </p>
<p> &emsp; </p>



<p>
<img src="https://i.imgur.com/VyZClrZ.jpeg" height="80%" width="80%" alt="pinged"/>
</p>
<p>
-Ping the Domain VM's private IP again to confirm the client VM has local network access to it.
<br />
