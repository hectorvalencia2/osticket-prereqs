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


<h2>Installation Steps</h2>



![Screenshot 2024-03-13 040704](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/d163433a-144f-41b6-8034-6febacac0477)
![Screenshot 2024-03-13 041244](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/0d07ac9b-9d31-469e-a737-e458d08d0dcf)

Create a Resource Group. Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs. When creating the VM, allow it to create a new Virtual Network (Vnet)
Open this: Installation Files. We will use these files to install osTicket and some of the dependencies. 
Install / Enable IIS in Windows WITH CGI and Common HTTP Features
- From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi). From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi). Create the directory C:\PHP. From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP. From the Installation Files, download and install VC_redist.x86.exe. From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi) Typical Setup -> Launch Configuration Wizard (after install) -> Standard Configuration -> Password1

![Screenshot 2024-03-13 044531](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/37f7aadd-2df9-410a-812e-c10d7ce9adb4)

Open IIS as an Admin. Register PHP from within IIS. Reload IIS (Open IIS, Stop and Start the server). Install osTicket v1.15.8. Download osTicket from the Installation Files Folder. Extract and copy “upload” folder to c:\inetpub\wwwroot. Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”. Reload IIS (Open IIS, Stop and Start the server). Go to sites -> Default -> osTicket. On the right, click “Browse *:80”


![Screenshot 2024-03-13 042608](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/81731531-6beb-4d97-8e88-55b9358cfeaa)

Note that some extensions are not enabled. Go back to IIS, sites -> Default -> osTicket. Double-click PHP Manager. Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browse, observe the changes


![Screenshot 2024-03-13 042918](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/04290351-c6a0-4a7e-92ff-a077e84e9480)

Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php

![Screenshot 2024-03-13 043022](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/4be91049-511e-4028-ad0b-339d5a877426)

Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All

![Screenshot 2024-03-13 043102](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/57bb375c-4f55-473d-9876-f32abfbd7519)

Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)

![Screenshot 2024-03-13 043244](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/62fb2b30-0c15-454d-b276-e1517d072961)
![Screenshot 2024-03-13 043347](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/94a06e15-5c8c-4e0a-b4f7-73ce0986705e)

From the Installation Files, download and install HeidiSQL.
Open Heidi SQL
Create a new session, root/Password1
Connect to the session
Create a database called “osTicket”
Continue Setting up osticket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: Password1
Click “Install Now!”

![Screenshot 2024-03-13 043537](https://github.com/hectorvalencia2/osticket-prereqs/assets/161524174/181a177e-3944-4231-b4e5-bc8eb4bf37dd)

Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php



