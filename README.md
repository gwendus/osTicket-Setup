<p align="center">

<img src="https://d7umqicpi7263.cloudfront.net/img/product/29bda7f2-2c99-40b8-a338-1448bc043ff1.com/214c16a85047ad91f1dfcddfb916db68" height="40%" width="40%" alt="osTicket logo"/>
 
 <h1># osTicket-Setup</h1>
This tutorial outlines the prerequisites, installation, and configuration of the open-source help desk ticketing system osTicket.
<br />


<h2>Environments and Technologies</h2>

- <b>Microsoft Azure</b> 
- <b>Remote Desktop</b>
- <b>Internet Information Services (IIS)</b>

<h2>Operating Systems</h2>

- <b>Windows 10</b> (22H2)
  <br />

<h2>List of Prerequisites</h2>

- <b>PHP manager for IIS</b> - configures PHP to run IIS
- <b>Rewrite module</b> - simplifies and redirects uders to URLs
- <b>VC_redist.x86 (redistributable)</b> - configures libraries dependent on Microsoft Visual C++ 
- <b>MySQL </b> - database program
- <b>HeidiSQL</b>- UI for SQL


<h2>Installation Steps:</h2>
After setting up the Windows 10 VM in Azure, begin a remote desktop session and log in with your credentials. Next, open Microsoft Edge. Download and extract <a href="https://docs.google.com/document/d/1DyjX8LeVU98LjhXO2t2K2F0aHywI2N9GD57T3taO5qo/edit?tab=t.0" target="_blank">osTicket-Installation-Files.zip</a>.
  <br>
<img src="https://i.imgur.com/tRNPgoz.png" height="60%" width="60%" alt="osTicket Extraction"/>
<br />
<br />

Enable Internet Information Services.
From Control Panel, select "Uninstall a Program," then "turn Windows Features on or off," and select "Internet Information Services."</b>
Enable "CGI" nested within "World Wide Web Services -> Application Development Features."  </b>

<img src="https://i.imgur.com/BWylFzh.png" height="50%" width="50%" alt="Enabling CGI"/><br />
<img src="https://i.imgur.com/umVDwYt.png" height="50%" width="50%" alt="IIS enabled"/><br />
<br />
<br />

Install PHP manager for IIS.

<img src="https://i.imgur.com/Rr7ksup.png" height="40%" width="40%" alt="PHP manager installation wizard"/>
<br />
<br />

Install the rewrite modules (rewrite_amd64 file).

<img src="https://i.imgur.com/dLuYYxQ.png" height="40%" width="40%" alt="PHP manager installation wizard"/>
<br />
<br />

Create a directory under the file path "C:\PHP." This allows osTicket to work with PHP.  <br/>
<img src="https://i.imgur.com/D6YkbLd.png" height="50%" width="50%" alt="PHP filepath"/>
<br />
<br />

Install the C++ redistributable. <br/>
<img src="https://i.imgur.com/IYngI1B.png" height="40%" width="40%" alt="C++ redistributable"/>
<br />
<br />

Install MySQL. Select "Standard configuration." Configure the root user account. <br/>
<img src="https://i.imgur.com/tyn6viM.png" height="40%" width="40%" alt="MySQL and root configuration"/>
<br />
<br />

Run IIS as an administrator. Register new PHP version. Select "C:\PHP\php-cgi.exe." Reload IIS when finished. <br/>
<img src="https://i.imgur.com/6Nme20D.png" height="40%" width="40%" alt="Register new PHP version."/>
<br />
<br />


Extract the osTicket folder. Move to C:\inetpub\wwwwroot, then rename upload to osTicket. Reload IIS when complete. Within IIS, select "sites" in the left hand column. Select Browse. You will reach this page in the osTicket Installer webpage. <br/>
<img src="https://i.imgur.com/Tkf59sk.png" height="50%" width="50%" alt="Register new PHP version."/>
<br />
<br />

We will now enable some necessary extensions. Select "PHP manager" from within IIS. Click "Enable or disable an extension." Toggle on the following extensions: "php_imap.dll, php_intl.dll and php_opcache.dll." Refresh the osTicket webpage and observe the difference.  <br/>
<img src="https://i.imgur.com/DdjpCTh.png" height="50%" width="50%" alt="Extensions enabled."/>
<br />
<br />
Within the extracted osTicket folder, rename C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php to C:\inetpub\wwwroot\osTicket\include\ost-config.php.
Change permissions for this file. Right click, then Properties -> Security tab -> Advanced -> Disable inheritance (remove option) -> Add -> Select a principal -> Type everyone in the box -> Check names -> OK. Click on Full control.  <br/>
<img src="https://i.imgur.com/sZUlWpf.png" height="60%" width="60%" alt="configure extracted folder"/>

Within the osTicket installation webpage, create credentials and provide the necessary information. The MySQL database name should be "osTicket" and the password for the database must be the same as the root account for MySQL. This is distinct from the credentials for the admin account for osTicket. 
Before we can continue, we must install HeidiSQL (a user interface for MySQL).
Accept default settings. Create a new session (bottom left hand corner), select "new" and login to the SQL database with your root credentials. Then rename the session "osTicket" with no spaces. <br/>
<img src="https://i.imgur.com/tSDglKg.png" height="50%" width="50%" alt="heidisql configuration."/>
<br />
<br />


Finish the installation of osTicket by selecting "Install Now." If you successfully followed along, you should see the following page. Observe the links at the bottom of the page. Bookmark the web pages for admin control and general users. Congratulations! <br/>
<img src="https://i.imgur.com/f7PTmOO.png" height="50%" width="50%" alt="Register new PHP version."/>
<br />
<br />
</p>


<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
