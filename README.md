<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating an Active Directory Home Lab using Microsoft Azure</h1>
This guide outlines how to implement Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop Protocol
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Brief Overview</h2>

- Creating our VMs: Domain Controller and the Client machine
- Establishing a connection between the 2 machines (Client and the Domain Controller)
- Deploying Active Directory on the Domain Controller
- Creating users using PowerShell
- Configuring basic Group Policy settings

<h2>Deployment and Configuration Steps</h2>

<h3> 1. Creating the Virtual Machines in Azure </h3>

   - Create Resource Group 
   - Create Domain Controller and Virtual Network
     - set password and username to machine (Ex: defaultuser123/Password123) (*Do not use these username's and passwords anywhere outside of this lab*)
     - set domain controllers IP to Static
     - log into the VM via Remote Desktop Protocol (RDP) and disable the Windows Firewall for now, to ensure connectivity
   - Create Client Machine
     - set password and user name to machine
     - Use the same region and attach the client to the same virtual network as the Domain Controller
     - Once Client VM is created, change the Client's DNS settings to the Domain Controller's Private IP address
     - After configuring the network settings, log into the Client VM using RDP and ping the Domain Controller's private IP address
    
<h3>2. Deploying Active Directory</h3> 

  - Log into the Domain Controller via RDP and install Active Directory Services
    - Promote the machine to a Domain Controller, setup a new forest (create a simple domain name, for ex: domain123.com)
    - Restart the Domain Controller VM and log back in as the user: domain123.com\yourusernamehere (You will input the domain that was created and the username for the admin account created earlier)
  - Creating Organization Units and Groups
    - In Active Directory Users and Computers, create and Organizational Unit (OU) and name it "_EMPLOYEES" (format it this way so we can differentiate it from Windows created groups and files)
    - Create another OU and name it "_ADMINS", next create a new employee and give it a name (Ex: John Doe) and username (Ex: john_admin) & password (Ex: Password123) and assign it to the Domain Admins Security Group
    - This will be the admin account we login to from now on
  - Joining the Client to your domain
    - Login to the Client machine as the original admin account and join the machine to the domain (the machine should restart)
    - Login to the Domain Controller and verify that the Client machine shows up in Active Directory Users and Computers
    - Create a new OU called "_CLIENTS" and move the Client machine into the "_CLIENTS" OU
   
<h3>3. Adding Users and Setting Permissions</h3>

  - Setting up RDP for non-admin users on the Client Machine
    - Log into the Client machine as our domain123.com\john_admin
    - open system properties and within the RDP section, allow domain users to access the remote desktop
    - You will now be able to login to the Client machine as a non-admin user now
  - Creating an additional user
    - Login to the Domain Controller and with Active Directory Users and Computers, and add a new user, for example name them bob johnson and set the username to bob_johnson and the password to Password123
    - Create a new 
    



