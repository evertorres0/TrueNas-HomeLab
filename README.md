<h1>TrueNas-HomeLab</h1>
A homelab build that turns recycled hardware into a TrueNAS NAS, running SMB shares for document/photo scanning, file storage, and everyday access across devices.
<h2>Download & Create Boot Media</h2>
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
<h2>Basic TrueNas Configuration<h2/>
