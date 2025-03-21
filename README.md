<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- osTicket Installation Files 
- Heidi SQL 

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/twTXM2h.png" height="80%" width="80%"/>
</p>
<p>
First, we create a resource group in Microsoft Azure and name it osTicket. We then create a virtual machine (VM) within this resource group with a Windows 10 image and ensuring that it has at least 2 vCPUs.
</p>
<br />

<p>
<img src="https://i.imgur.com/D8XPDHV.png" height="80%" width="80%"/>
</p>
<p>
Using Remote Desktop Protocol (RDP) we access the VM. We do this by copying the public IPv4 address listed in the Azure portal for the VM. 
</p>
<br />

<p>
<img src="https://i.imgur.com/454C1be.jpg" height="80%" width="80%"/>
</p>
<p>
Once connected to the VM, we download the osTicket-Installation-Files.zip and unzip it onto the VM’s desktop. It will be called “os-Ticket-Installation-Files”. We will use the files in this folder to install osTicket. 
</p>
<br />

<p>
<img src="https://i.imgur.com/cKzqEdm.jpg" height="80%" width="80%"/>
</p>
<p>
We then enable Internet Information Services (IIS) by opening the Control Panel and navigating to “Turn Windows Features On or Off”. We then scroll down to locate IIS and click inside the checkbox to activate it. We expand this selection, find World Wide Web Services > Application Development Features > CGI. We make sure that CGI is selected and then click OK.
</p>
<br />

<p>
<img src="https://i.imgur.com/QQFnNHj.jpg" height="80%" width="80%"/>
</p>
<p>
From the osTicket installation folder on the VM’s desktop, we locate and install PHP Manager (PHPManagerForIIS_V1.5.0.msi) to proceed with setup. 
</p>
<br />

<p>
<img src="https://i.imgur.com/lquTlzu.jpg" height="80%" width="80%"/>
</p>
<p>
Within the same folder, we install the Rewrite Module to continue configuring the environment. 
</p>
<br />

<p>
<img src="https://i.imgur.com/B2SzEis.jpg" height="80%" width="80%"/>
</p>
<br />
<p>
<img src="https://i.imgur.com/8P7f40q.jpg" height="80%" width="80%"/>
</p>
<p>
We then create the directory  “C:\PHP”. We unzip the file PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and extract all of the contents into the C:\PHP directory. 
</p>
<br />

<p>
<img src="https://i.imgur.com/knZSoIA.jpg" height="80%" width="80%"/>
</p>
<p>
Next, we install VC_redist.x86.exe from the osTicket installation folder to ensure that the necessary Visual C++ Redistributable components are in place. 
</p>
<br />

<p>
<img src="https://i.imgur.com/WYL4mtp.jpg" height="80%" width="80%"/>
</p>
<p>
We next install MySQL (mysql-5.5.62-win32.msi) from the osTicket installation folder in order to set up the MySQL database server. We then launch the configuration wizard and choose standard configuration. When asked for username and password, we elect to keep things simple for the purposes of this project and type in “root” for both. We finalize the setup by clicking the execute button. 
</p>
<br />

<p>
<img src="https://i.imgur.com/nTy8mSt.jpg" height="80%" width="80%"/>
</p>
<p>
Then we open IIS Manager as an administrator. We register PHP within IIS by configuring the necessary settings. After this is done, we restart the server by selecting “restart” in the IIS Manager. 
</p>
<br />

<p>
<img src="https://i.imgur.com/LlYYFNW.jpg" height="80%" width="80%"/>
</p>
<p>
From the osTicket-Installation-Files folder, we unzip osTicket-v1.15.8.zip and copy the upload folder to C:\inetpub\wwwroot. Then, within C:\inetpub\wwwroot, we rename the upload folder to osTicket. 
</p>
<br />

<p>
<img src="https://i.imgur.com/Dv4osVN.jpg" height="80%" width="80%"/>
</p>
<p>
We then return to the IIS Manager and restart the server. We enable the necessary PHP extensions by navigating to Sites > Default > osTicket, then double-click “PHP Manager”. We select “Disable or enable an extension” and enable php_intl.dll, php_opcache.dll and php_imap.dll. After that, we refresh the osTicket web server and verify that the Intl Extension is now enabled.
</p>
<br />

<p>
<img src="https://i.imgur.com/x7ufz26.jpg" height="80%" width="80%"/>
</p>
<p>
Next, we navigage to C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php and rename the file to ost-config.php in the same directory (C:\inetpub\wwwroot\osTicket\include).
</p>
<br />

<p>
<img src="https://i.imgur.com/wX1JU14.jpg" height="80%" width="80%"/>
</p>
<p>
We then assign the appropriate permissions to ost-config.php by right-clicking the file and selecting “Properties”. In the Security tab, we disable inheritance, remove all existing permissions, and grant “everyone” full access. 
</p>
<br />

<p>
<img src="https://i.imgur.com/AFjJEOy.jpg" height="80%" width="80%"/>
</p>
<p>
We proceed with the osTicket setup in our browser by clicking “Continue”. We assign a name of our choice to our helpdesk, and select a default email address to receive customer-submitted ticket notifications. 
</p>
<br />

<p>
<img src="https://i.imgur.com/MACU1hM.jpg" height="80%" width="80%"/>

<br />

<p>
<img src="https://i.imgur.com/BnoYudj.jpg" height="80%" width="80%"/>

<br />

<p>
<img src="https://i.imgur.com/WcmGrT3.jpg" height="80%" width="80%"/>
</p>
<p>
From the os-Ticket-Installations-Files folder, install HeidiSQL. After installation, open it and create a new session, with user and password both “root”. Create a database called “osTicket” by right-clicking on “Unnamed” on the lefthand panel. 
</p>
<br />

<p>
<img src="https://i.imgur.com/EzcrHPt.jpg" height="80%" width="80%"/>

<br />

<p>
<img src="https://i.imgur.com/Mb2o8Bj.jpg" height="80%" width="80%"/>
</p>
<p>
Last, we continue setting up osTicket in the web browser of the VM. Under MySQL Database we type in “osTicket”. For both MySQL Username and MySQL Password, we type in “root”. When we click on the “Install Now” button we have finished with the installation of osTicket to our virtual machine.
</p>
<br />
