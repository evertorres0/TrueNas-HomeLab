<h1>TrueNas-HomeLab</h1>
<h2>Description</h2>
A homelab build that turns recycled hardware into a Nas , running SMB shares for document/photo scanning, file storage, and everyday access across devices.
<h2>Installing TrueNas</h2>
For my home project I chose to intall <a href="https://www.truenas.com/download-truenas-community-edition/">TrueNas Community Edition</a> and used Rufus to flash the ISO to 
a USB drive.<br /> 
<br />
After having flash your usb you can plug it to the computer you want to install to load into the bios select the usb to boot from.<br />
<br />
<ul>
  <li><b>Troubleshooting</b>
    <ul>
      <li>I had issues with ventoy normal boot so I switched over to rufus and made it a dvd instead of a iso </li>
      <li>I ran into an issue due to the drive having perious data on it so i use blkdisk to clean the drive</li>
      <li>If the system won’t boot from USB, check BIOS boot order and disable Secure Boot.</li>
    </ul>
  </li>
</ul>
<h2>TrueNas Configuration</h2>
After installing TrueNAS, configuration is done through the system’s web interface by navigating to its IP address in your browser. The first step I completed was changing the network settings from DHCP to a static IP address, ensuring the address remains consistent.<br />
<br />
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
Next, we will configure the storage pool. For this project, I am using a mirror configuration, which ensures that all data written to one drive is simultaneously written to the other. This setup provides strong redundancy and helps protect against drive failure.<br />
<br />
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
After your drives have been configure I added a dateset to create a share for my use propuse I created a SMB share. Before you create a SMB share you need to first create a a SMB user by going to Creditional>user> add username and password and check the box that says SMB user.<br />
<br />
To create a SMB share to go Dataset>AddDataset add a name and for dataset preset select SMB<br />
<p align="center">
  <img src="https://i.imgur.com/TFiEf9N.png" width="30%" alt="Add Dataset"/> <br /> 
</p>

<br />
I wanted to scan documents/photos with a network printer that I have. To be able to set this up I went to my printers web UI to be able to add the share to the address book of the printer.<br />
<br />
The host being the ip address of the server, the path being the name of the share and usernmae and passowrd of a SMB user of truenas.<br />
<p align="center"> Printer SMB Configuration: <br/>
<img src="https://i.imgur.com/R3Ov4Xa.png" height="80%" width="80%" alt="Printer SMB Configuration"/> <br /> </p>
<>
