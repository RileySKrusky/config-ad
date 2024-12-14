<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
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

1) Creating Resource Group
2) Creating A Virtuall Network


<h2>Deployment and Configuration Steps</h2>

<h3>1) Creating Resource Group</h3>

<p>Open up your Microsoft Azure and search for "Resource Group" in the search bar. Once you have selected "Resource Groups", click the top left button that says "Create". I will be naming my resource group "Active-Directory-Lab". Make sure to select your region to the corrisponding region you are in (I'm in Canada, so my region would be Central Canada). Once you are done, you can simply review and create.</p>

<img src="https://i.imgur.com/Adulmc4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>2) Creating A Virtuall Network</h3>

<p> For this step, you will go up to the search bar again and search up "Virtual Networks". After you have selected Virtual Networks you can begin the procces by clicking the "Create" icon on the top left under "Virtual Networks". You will then be prompted to the "Create Virtual Network" screen where you will follow the same procedure as the one listed in step 2. Make sure you have selected the resopurce group you just created and make sure your region is the same as your resource group. I will be naming my virtual network "Active-Directory-Vnet". Once you have completed those steps, press "Review and Create" and "Create" on the bottom left of the screen. </p>

<img src="https://i.imgur.com/UMjl4mE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>3) Creating Your Domain Controller VM (Virtual Machine) </h3>

<p>To start, search up "Virtual Machines" in your search bar and select. Select the "Create" button on the top left of the screen and click on "Azure virtual machine".  </p>

<img src="https://i.imgur.com/L0CveLE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p> After you have done this, you will have to make sure you have these settings selected:</p> 
<p>-Resource Group - Active-Director-Lab (Or the resource group you created in step 1)</p>
<p>-The same region you have selected for all your applications (For Example:  mine is Central Canada)</p> 
<p>-Image - (Windows Server 2022 Datacenter: Azure Edition - x64 Gen2)</p>
<p>-Size - At least 2 vcpus, 8 GiB memory</p>
<p>-Selected Inbound Ports - RDP (3389)</p>

<img src="https://i.imgur.com/wRpF2OO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/GBW1G7T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>Your username and password can be whatever you want as long as you write it down and remember it because we will be logging into this user later in the lab. Once you have finished these steps, if it is on the bottom of your starting page, check the "Licensing" box and then move on through the pages untill you get to the "Networking" page where you make sure that your virtual network that you just created is selected. You can then "Review and Create" and "Create". </p>

<h3>4) Creating A CLient Virtual Machine</h3>

<p>This next step will be very similar to step 3 because we will be creating another "Virtual Machine". The only difference with this virtual machine is we will be naming it "client-1". This will essentially be a test virtual machine for us. Make sure these settings are selected:</p>

<p>-Resource Group - Active-Director-Lab (Or the resource group you created in step 1)</p>
<p>-The same region you have selected for all your applications (For Example:  mine is Central Canada)</p> 
<p>-Image - (Windows 10 Pro, version 22H2 - x64 Gen2)</p>
<p>-Size - At least 2 vcpus, 8 GiB memory</p>
<p>-Selected Inbound Ports - RDP (3389)</p>

<p> Make sure the license box is checked on the first page as well. </p>

<img src="https://i.imgur.com/srCWe7O.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Susbj6e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>When you are done with those settings, go into the "Networking" tab and make sure:</p>
<p>-Virtual Network : Active-Directory-Vnet</p>
<p>-Subnet : Default</p>
<p>Public IP: Client-1 ip</p>

<p>After you are done with these settings you can "Review and Create" -> "Create".</p>

<h3>5) Making DC-1's IP Address (Static)</h3>

<p>The reason we are making DC-1's IP "Static" is so that when we turn off our computer, our IP Address will stay the same. If we were to leave our IP Address for DC-1 on "Dynamic", their is a possibility that our IP address would change when we turn off our computer. To change our virtual machines ip address from "Static" to "Dynamic", first we would have to go into our DC-1 virtual machine by searching "Virtual Machine" and clicking on "DC-1" -> "Networking" -> "Network Settings" -> "Network Interface / ip configuration" (It'll have a green computer chip icon to the left of it) -> "ipconfig-1", make sure to select "Static" under "Private IP Adress Settings" then "Save".</p>

<img src="https://i.imgur.com/aQO5bjh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/mqji9V2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<h3>6) Firewall</h3>

<p>In most cases, it isn't safe to disable your firewall on your computer, but because this is simply a test "Virtual Machine" it is not going to create any harm. First we will have to log into our "DC-1" virtual machine. Open up your "Remote Destkop" software and make sure to copy the public ip address from this virtual machine. You can do this by searching up "Virtual Machine", clicking the "DC-1" VM you just created and looking for the public address displayed on the right side of the Virtual Machine tab.</p>

<img src="https://i.imgur.com/eSDoOof.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/4HcrXIA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>Once you are here, make sure to login using the username and password you created when we first made "DC-1". Once you have logged into your "DC-1" Virtual Desktop, right-click your windows icon on the bottom left and then select "Run", type in "wf.msc". You will see your windows firewall tab will open up once you do this.</p>

<img src="https://i.imgur.com/Zj1Amaz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

<p>In this window make sure to turn off your "Domain" and "Private" firewalls and then press "Apply" and "Ok".</p>

<img src="https://i.imgur.com/ZQ4ViI2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>



