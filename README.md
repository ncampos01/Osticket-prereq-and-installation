# Osticket Prereq and Installation
<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>


This guideline outlines the prerequisites and installation of the open-source help desk ticketing system (osTicket).<br />




<h2>Resources and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2) (4vCPU)

<h2>List of Prerequisites</h2>

- Running Azure VM
- <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> Installation Files </a>


<h2>Installation Steps</h2>

- First Install Prereq files as osTicekt will not run properly without them.
- Creating and installation of osTicket within Azure Cloud Services.

<h2>Part 1: Creation Of VM </h2>
 
 - Create a Resource Group in Azure.
 - Create a Windows VM(10 OS is best) with 4vCPU.
- When creating a VM make sure to allow the creation of a new Vnet.



<h2>Part 2: Prereq installation and Installation of osTicket.</h2>


- Enter VM that was created.
- Open tab and press on this link <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> Installation Files </a> : which contains all files that will need to be installed before main installation of osTicket( REMINDER failure to run any of these programs will mess with Main Install).

<ul><!-- Start of main list -->
    <li>Install / Enable IIS in Windows WITH
CGI and Common HTTP Features
World Wide Web Services -> Application Development Features -></li>
 <ul><!-- Start of main list -->
     <li>CGI</li>
      <li>Common HTTP Features AND IIS Management Console Internet Information Services -> Web Management Tools -> IIS Management Console</li>
	     <li>IIS Management Console</li>
</ul><!-- end of main list --> </ul>

<img src="https://support.winhost.com/AvatarHandler.ashx?fid=2777549&key=3721805266">
 


- From the Installation Files, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)

- From the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
<ul><!--Start of main list -->
    <li>Create the directory C:\PHP
      <ul><!--Start of nested list--> 
          <li>From the Installation Files, download PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) and unzip the contents into C:\PHP</li>
      </ul><!--End of nested list-->
    </li>
</ul><!--End of main list-->

 <ul><!--Start main list-->
     <li>From the Installation Files, download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
 <ul><!--Start of nested list-->
	 <li>Typical Setup ->
         <li>Launch Configuration Wizard (after install) ->
         <li>Standard Configuration ->
         <li>Password1</li>
 </ul><!--End of nested list-->
     </li>
 </ul><!--End of main list-->
 

<ul><!--Start of main list-->
	<li>Open IIS as an Admin
 <ul><!--Start of nested list-->
     <li>Register PHP from within IIS
     <li>Reload IIS (Open IIS, Stop and Start the server)
     <li>Install osTicket v1.15.8
     <li>Download osTicket from the Installation Files Folder
     <li>Extract and copy “upload” folder to c:\inetpub\wwwroot
     <li>Within c:\inetpub\wwwroot, Rename “upload” to “osTicket”
     <li>Reload IIS (Open IIS, Stop and Start the server)</li>
 </ul><!--End of nestted list-->
	</li>

 </ul><!--End of main list-->
 
<ul><!--Start of main list-->
	<li>Go to sites -> Default -> osTicket
<ul><!--Start of nested list-->
	<li>On the right, click “Browse *:80”</li>
</ul><!--End of nested list-->
	</li> 
</ul><!--End of main list-->

- !Note that some extensions are not enabled!
<ul><!--Start of main list-->
	<li>Go back to IIS, sites -> Default -> osTicket
		<ul><!--Start of nested list-->
			<li>Double-click PHP Manager
			<li>Click “Enable or disable an extension”
			<li>Enable: php_imap.dll
			<li>Enable: php_intl.dll
			<li>Enable: php_opcache.dll</li>
		</ul><!--End of nested list-->
	<li>Refresh the osTicket site in your browse, observe the changes
	</li>
</ul><!--End of main list-->

<ul><!--Start of main list-->
	<li>Rename: ost-config.php
		<ul><!--Start of nested list-->
			<li>From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
			<li>To: C:\inetpub\wwwroot\osTicket\include\ost-config.php</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

<ul><!--Start of main list-->
        <li>Assign Permissions: ost-config.php
		<ul><!--Start of nested list-->
			<li>Disable inheritance -> Remove All
			<li>New Permissions -> Everyone -> All</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

<ul><!--Start of main list-->
	<li>Continue Setting up osTicket in the browser (click Continue)
		<ul><!--Start of nested list-->
			<li>Name Helpdesk
			<li>Default email (receives email from customers)</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

<ul><!--Start of main list-->
        <li>From the  <a href="https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6"> Installation Files </a>, download and install HeidiSQL.
		<ul><!--Start of nested list-->
			<li>Open Heidi SQL
			<li>Create a new session, root/Password1
			<li>Connect to the session
			<li>Create a database called “osTicket”</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

<ul><!--Start of main list-->
        <li>Continue Setting up osTicket in the browser
		<ul><!--Startr of nested list-->
			<li>MySQL Database: osTicket
			<li>MySQL Username: root
			<li>MySQL Password: Password1 (to make it easier to remember)
			<li>Click “Install Now!”</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

- Congrats, IF it is installed with no errors!
Browse to your help desk login page: http://localhost/osTicket/scp/login.php

- End Users osTicket URL:
http://localhost/osTicket/ 

<ul><!--Start of main list-->
	<li>Clean up
		<ul><!--Star of nested list-->
			<li>Delete: C:\inetpub\wwwroot\osTicket\setup
			<li>Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php</li>
		</ul><!--End of nested list-->
	</li>
</ul><!--End of main list-->

- Notes:
Browse to your help desk login page: http://localhost/osTicket/scp/login.php  
End Users osTicket URL: http://localhost/osTicket/ 
<br />
