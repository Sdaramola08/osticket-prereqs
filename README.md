<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [How to create a Virtual Machine in Azure ft Mr. Madakor](https://firebasestorage.googleapis.com/v0/b/coursecareers-prod.appspot.com/o/courses%2Fit-course%2FFINAL_DRAFT_osTicket%20Overview%20and%20Virtual%20Machine%20Creation.mp4?alt=media&token=9a98be70-3ff9-4bfd-a5a2-9649fdc47a25)

- ### [How To Install osTicket ft Mr. Madakor](https://firebasestorage.googleapis.com/v0/b/coursecareers-prod.appspot.com/o/courses%2Fit-course%2FFINAL_DRAFT_Installation.mp4?alt=media&token=4189d60b-8268-4375-a291-4590f73783dc)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- PC/Laptop with internet connection
- A credit card to make a subscription (Do not worry you are not getting chareged, instead you 	 get a free $200 credit     after you subscribe).
- Google Chrome & Google drive (Not Mandatory)
- An Email Address


<h2>Installation Steps</h2>

<h2>Part 1 (Create Virtual Machine in Azure)<h2>

<p>
<img src="https://i.imgur.com/3NRB32w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Create an Azure Account. (Get you credit cards ready!)
- Sign in to the [Azure portal](https://portal.azure.com)).
- Click on the "Create a resource" button, which is located on the upper left-hand corner of     the Azure portal.
- In the search box, type "Virtual Machine" and press Enter.
- Select the "Virtual Machine" option from the search results.
- Click the "Create" button to begin the process of creating a new VM.
- Create a Windows 10 Virtual Machine (VM) with 2-4 Virtual CPUs
  When creating the VM, allow it to create a new Virtual Network (Vnet)
- In the "Create a Virtual Machine" blade, you will be asked to specify the following details:
  - Resource group: Choose an existing resource group or create a new one.
  - Virtual machine name: Enter a unique name for your VM.
  - Region: Select the region in which you want to create your VM.
  - Image: Choose an operating system image for your VM. You can select from a list of pre-       configured images or       use a custom image.
  - Size: Select the size of the VM based on the number of cores, memory, and other hardware       resources you want.
  - Authentication type: Select the authentication type you want to use. You can either use a     password or an SSH         public key.
- Once you have specified all the required details, click the "Review + create" button to       review your selections.
- Review the summary of your VM configuration and click the "Create" button to create the VM.   It may take a few minutes   for the VM to be created.

<h2>Part 2 (Installation)<h2>

<p>
<img src="https://i.imgur.com/10cAbKv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

- Connect to your Virtual Machine with Remote Desktop
- Install / Enable IIS in Windows
- Install Web Platform installer (download from here: [LINK](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6))
  - Open after installation
  - Add MySQL 5.5 (it will ask for credentials to be created later)
    - Name: root
    - Password: Password1
  - Add All simple versions of x86 PHP up until 7.3
  - Fix any failures if required (download from here: [LINK](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6))
    - Install PHP Version 7.3.8 (or any other version if necessary, [ARCHIVES](https://windows.php.net/downloads/releases/archives/))
    - Install PHP Manager 1.5.0 for IIS 10 (folder you unzipped on the desktop)
    - Install Microsoft Visual C++ 2009 Redistributable Package

- Install osTicket v1.15.8
  - Download osTicket (download from here: [LINK](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6))
  - Extract and copy the “upload” folder INTO c:\inetpub\wwwroot
  - Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”

- Reload IIS (Open IIS, Stop and Start the Server)
  - Go to sites -> Default -> osTicket
  - On the right, click “Browse *:80”

- Enable Estensions in IIS: Note that some extensions are not enabled
  - Go back to IIS, sites -> Default -> osTicket
  - Double-click PHP Manager
  - Click “Enable or disable an extension”
    - Enable: php_imap.dll
    - Enable: php_intl.dll
    - Enable: php_opcache.dll

- Refresh the osTicket site in your browse, observe the changes 
- Rename:
  - From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
	  To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Assign Permissions: ost-config.php
  - Disable inheritance -> Remove All
  - New Permissions -> Everyone -> All

- Continue Setting up osTicket in the browser (click continue)
  - Name Helpdesk
  - Default email (receives email from customers)

- Download and Install HeidiSQL (download from here: [LINK](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6))
  - Create a new session, root/Password1
  - Connect to the session
  - Create a database called “osTicket”

- Continue Setting up osTicket in the browser
- MySQL Database: osTicket
  - MySQL Username: root
  - MySQL Password: Password1

- Click "Install Now"
- Congratulations, osTicket as now been installed
- Clean up
  - Delete: C:\inetpub\wwwroot\osTicket\setup
  - Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
- Login to the osTicket Admin Panel (http://localhost/osTicket/scp/login.php)

Notes: 
- Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
- End Users osTicket URL: http://localhost/osTicket/ 

<br />
