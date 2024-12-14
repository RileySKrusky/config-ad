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

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
