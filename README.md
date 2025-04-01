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

- IIS (Internet Information Service) Server with CGI Enabled
- SQL Server (I used MySQL and HeidiSQL)
- PHP Manager
- Item 4
- Item 5

<h2>Installation Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
The first thing we are going to do is set up Internet Information Services (IIS) as well as CGI. To do this, go to your Control Panel, select Programs, then Programs and Features, followed by Turn Windows Features on or off. Check Internet Information Services (IIS). Under IIS, there will be more options—expand World Wide Web Services, expand Application Development Features, and select CGI. CGI (Common Gateway Interface) is a standard protocol used to enable web servers to execute external programs. Upon installing IIS and CGI, open your web browser and navigate to 127.0.0.1. If you see the Windows IIS screen, the installation was successful.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, we are going to install PHP Manager. Download all the required applications and place them in a folder—I will be referring to this as the “Installation Files” folder. Open the Installation Files folder and install PHP Manager, making sure to accept all prompts by selecting "Yes" when required. Right after, we will install Rewrite. Open the Rewrite installation file and proceed with the installation.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, we are going to create a directory on the C drive. Open Windows Explorer and click on "This PC." Select your C drive, then right-click anywhere on the screen, select "New," and then "Folder." Name the folder "PHP" in all caps. Next, locate the PHP files in the Installation Files folder and extract them into the newly created PHP folder on the C drive.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, we are going to install VC_Redist from the Installation Files folder, as well as MySQL. Run the VC_Redist installer and follow the wizard to complete the installation. Next, install MySQL by selecting the "Typical Setup" option during installation. When launching MySQL, choose "Standard Configuration." For this demonstration, we will set both the username and password to "root." <strong>Warning:</strong> Do not use "root" as a username and password in a real environment, as it is a security risk.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, we will configure some settings inside IIS. Press the Windows key and type "IIS" in the Start menu search bar. Right-click on "Internet Information Services" and select "Run as Administrator." Once IIS is open, we will register PHP with IIS. Click on "PHP Manager," then click "Register" and browse to the PHP folder you created earlier on the C drive. Select the file named "PHP-cgi." Finally, go back to IIS and click "Restart" to restart the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to your Installation Files folder and click the osTicket zip file. Copy the "upload" folder into C:\inetpub\wwwroot and rename it to "osTicket." Once done, restart IIS. After IIS has restarted, expand Sites > Default Web Site > osTicket. On the right side, click "Browse." This should open the osTicket web page. It will show that some extensions are not enabled. To fix this, go back to IIS, expand IIS > Sites > Default Sites > osTicket, and double-click "PHP Manager." Click "Enable or Disable an Extension." Enable the following extensions: "PHP_imap," "PHP_intl," and "PHP_opcache." Once selected, click the "Enable" button on the right side. Refresh your browser to see the changes. There should be two options in red—this is fine, and we will not need them.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, we are going to rename a file on the hard drive. In Windows Explorer, browse to C:\inetpub\www\osTicket\include. Find "ost-sampleconfig.php" and rename it to "ost-config.php." Once it is renamed, we will change the permissions. Right-click on the file and select "Properties," then go to the "Security" tab. Click "Advanced," then select "Disable inheritance." This will clear the permissions inherited from parent folders, as we will be starting from scratch. Next, we will add new permissions. Since this is a test environment, I will give "Everyone" full control. <strong>Note:</strong> This is not recommended in a real environment due to security concerns.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in your web browser, continue the installation of osTicket. Fill out the necessary information, but stop once you reach the database settings. Now, we are going to install HeidiSQL. In the Installation Files folder, install HeidiSQL and launch it upon completion. In HeidiSQL, click "New." For the username and password, enter the SQL username and password from earlier, which are both "root." Create a database called "osTicket" by right-clicking the unnamed icon and typing "osTicket."  

Back in the web browser, insert the following information:  
- **MySQL database**: osTicket  
- **Username/Password**: root  

Click "Install," and everything should work!

</p>
<br />
