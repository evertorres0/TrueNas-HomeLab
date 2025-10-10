<h1>TrueNas-HomeLab</h1>
<h2>Description</h2>
A home lab project showcasing the installation and configuration of TrueNAS Community Edition. This setup demonstrates storage pooling with redundancy, SMB file sharing, static IP networking, and printer integration.TrueNAS is an open-source network-attached storage (NAS) operating system built on OpenZFS, designed to deliver reliable data protection, file sharing, and storage management.
<h2>Hardware Used</h2>
<ul>
  <li>Processor: Intel CPU (legacy system)</li>
  <li>Memory: 16 GB DDR3 RAM</li>
  <li>Primary Storage: 250 GB SSD (system installation)</li>
  <li>Secondary Storage: 2 × 500 GB HDDs (configured in mirror for redundancy)</li>
</ul>
<h2>Installing TrueNas</h2>
For my home project I chose to intall <a href="https://www.truenas.com/download-truenas-community-edition/">TrueNas Community Edition</a> and used Rufus to flash the ISO to a USB drive.<br /> 
After having flash your usb you can plug it to the computer you want to install to load into the bios select the usb to boot from.<br /><br />
<ul>
  <li><b>Troubleshooting</b>
    <ul>
      <li>I encountered issues with Ventoy’s normal boot option, I switched to Rufus and created the media as a DVD image instead of an ISO. </li>
      <li>I was also given a error because of the pervious data on the drive, I use tools such as blkdiscard to clean the drive before proceeding.</li>
      <li>Make sure to disable Secure Boot.</li>
    </ul>
  </li>
</ul>
<h2>TrueNas Configuration</h2>
After installing TrueNAS, configuration is done through the system’s web interface by navigating to its IP address in your browser. The first step I completed was changing the network settings from DHCP to a static IP address, ensuring the address remains consistent.<br /><br />
<b>To configure a static IP:</b>
  <ul>
    <li>In the left-hand menu, go to Network.</li>
    <li>Under Interfaces, click the edit (pen) icon for the desired interface.</li>
    <li>Uncheck DHCP.</li>
    <li>Add an alias with your chosen IP address and subnet mask.</li>
  </ul>
<p align="center">
  <img src="https://i.imgur.com/vAOaJ9P.png"width="30%" alt="Network Configuration"/> <br /> 
</p>
<br />
Next, I configure the storage pool. For this project, I am using a mirror configuration, which ensures that all data written to one drive is simultaneously written to the other. This setup provides strong redundancy and helps protect against drive failure.<br /><br />
<b>To create the pool:</b>
  <ul>
    <li>In the left-hand menu, navigate to Storage > Create Pool.</li>
    <li>Assign a name to the pool.</li>
    <li>For the layout, select Mirror.</li>
    <li>For disk size, select storage drives.</li>
    <li>Select Go To Review, then Create Pool.</li>
  </ul>
<p align="center">
  <img src="https://i.imgur.com/JNU5vSS.png" valign="top" width="20%" /> 
  <img src="https://i.imgur.com/KgbqvYS.png" valign="top" width="20%" /> 
</p>
<br />
After configuring the storage pool, I created a dataset to use as a shared resource. For my setup, I chose to create an SMB share.Before setting up the SMB share, you must first create an SMB user.<br /><br />
<b>Creating a SMB user</b><br />
<ul>
  <li>In the left-hand menu, navigate to Credentials > Users.</li>
  <li>Click Add to create a new user.</li>
  <li>Enter a username and password.</li>
  <li>Check the box labeled SMB User.</li>
</ul>
<p align="center">
  <img src="https://i.imgur.com/HxphVpw.png" alt="Add User"/>
</p>
<br />
Once the user has been created, I proceed to configure and enable the SMB share for your dataset.<br />
<br />
<b>To set up an SMB share:</b><br />
<ul>
  <li>Navigate to Dataset > Add Dataset.</li>
  <li>Enter a name for the dataset.</li>
  <li>For the dataset preset, select SMB.</li>
  <li>Once the dataset is created, go to Edit Permissions.</li>
  <li>Assign the previously created SMB user to ensure they have access to the share.</li>
</ul>
<br />
<p align="center">
  <img src="https://i.imgur.com/TFiEf9N.png" width="30%" alt="Add Dataset"/> <br /> 
</p>
<br />
My goal was to enable my network printer to scan documents and photos directly to the TrueNAS share. To set this up, I accessed the printer’s web interface and added the SMB share to the printer’s address book.<br />
<br />
<b>Configuring Network Printer:</b><br />
<ul>
  <li>Open the printer’s web interface in a browser.</li>
  <li>Navigate to the Address Book or equivalent section.</li>
  <li>Add a new SMB destination with the following details:
    <ul>
      <li>Host: Enter the IP address of the TrueNAS server.</li>
      <li>Path: Enter the name of the SMB share you created.</li>
      <li>Credentials: Provide the username and password of the SMB user configured in TrueNAS.</li>
    </ul>
  </li>
</ul>
<p align="center">
  <img src="https://i.imgur.com/R3Ov4Xa.png" height="80%" width="80%" alt="Printer SMB Configuration"/> <br /> 
</p>
