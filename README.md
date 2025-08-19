<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Creating an Active Directory Home Lab using Microsoft Azure</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

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
- Deploying Active Directory on the Domain Controller
- Establishing a connection between the 2 machines (Client and the Domain Controller)
- Creating users using PowerShell
- Configuring basic Group Policy settings

<h2>Deployment and Configuration Steps</h2>

<h3> 1. Creating the Virtual Machines in Azure </h3>

   - Create Resource Group 
   - Create Domain Controller and Virtual Network
     - set password and username to machine
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
    - Restart the Domain Controller VM and log back in as the user: domain123.com/yourusernamehere (You will input the domain that was created and the username for the admin account created earlier)
  - asdf




