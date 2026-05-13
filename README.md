# Active-Directory-Lab1
Deployment and configuration of a Windows Server Active Directory environment including domain controller setup, user management, organizational units, group policies, and client domain joining.


<h2>This project demonstrates the deployment and configuration of a Windows Server Active Directory environment designed for a small business with multiple departments.
The lab simulates how an IT administrator would deploy a Domain Controller, manage users and organizational units, apply security policies, and connect client machines to the domain.</h2>


<h2>Technologies used</h2>

. Windows server

. Windows 10

. Active Directory Domain Service (AD DS)

. Group Policy Management

. VirtualBox


<h2>Lab Enviroment</h2>

Components     -        Configuration

Virtualization   -        VirtualBox

server OS         -       Windows Server 2022

client OS          -      Windows 10 pro 

Domain              -     HomeLab

Server IP         -       192.168.1.50

Client IP         --       192.168.1.52

<h2>Network Architecture</h2>

The environment consists of:

. 1 DC - Domain Controller

. 1 Windows 10 pro client machine

. Bridged for domain communication

. Bridged adapter for internet access 

<h2>Step 1 - Install Windows Server</h2>

Create a new virtual machine and install windows server.

Recommended configuration:

. RAM: 4GB

. Storage: 50GB

. Adapter 1: Bridged Adapter 

<img width="959" height="473" alt="image" src="https://github.com/user-attachments/assets/bf77b5fd-5844-4440-8f33-50865182da46" />

After installation:

. Rename the server to DC01 in server manager by selecting the local server option and changing the name. restart when prompted to.



<h2>Step 2 - Configure static IP address</h2>

Navigate to:

control panel -> network and sharing center -> change adapter settings.

There is 1 adapters, usually Ethernet 1 ( rename it as " Bridged Network" ). right click it, select properties, select ipv4, select use the following IP (to create a static IP) and set the following configurations, disable Ipv6 only. 

. IP address: 192.168.1.50

. Subnet mask: 255.255.255.0

. Default Gateway: 192.168.1.1

. Preffered DNS server: 192.168.1.50 

<img width="959" height="473" alt="image" src="https://github.com/user-attachments/assets/fc51ab0e-cfd1-4dd2-b8c2-d3f02c758586" />


<h2>Step 3 - install active directory domain services</h2>

open server manager

select:

Add roles and features -> install active directory domain services.

after installatoin:

promote server to a domain controller

Domain name: YOUR OWN CHOICE: 

Homelab.com

confirm domain and server name by clicking on local server in server manager
<img width="1434" height="942" alt="image" src="https://github.com/user-attachments/assets/6ee4ca56-5b36-4f77-8fa8-10abd2b99670" />


<h2>Step 4 - Create   Organizational Units (OUs)</h2>
Active Directory Users and computers, in tools -> right click your Domain Name homelab.com -> select new -> organizational unit
Create department-based " GROUPS-OU and USERS-OU ":

Groups-OU
. HR

. Finance

. IT

. Sales

Users-OU

.Jerry polpoo

.Cinco sanchez

.Berry

.Tanjim

<img width="1482" height="911" alt="image" src="https://github.com/user-attachments/assets/e3fe6a3d-5250-4131-b304-275fc63ad98e" />

<h2>Step 5 - ADD USERS INTO THEIR ROLES (OUs)</h2>
After OUs are created now ADD each member into their access roles. Right click any group LIKE "SALES" then press PROPERTIES -> Members -> ADD -> Type USER "NAME" -> click CHECK NAME to add user into the role.   

<img width="1450" height="952" alt="image" src="https://github.com/user-attachments/assets/e1bcc8d6-8f6f-45a3-a12d-659ece3df61f" />

<h2>Step 6 - Configure Group Policy</h2>


Open Group Policy Management Control

Create policies such as:

<h2>Password Policy</h2>

. Enforce password complexity

. Minimum password length

<img width="1429" height="922" alt="image" src="https://github.com/user-attachments/assets/4525ad45-9e59-4b19-b646-c5cf1c51a1ac" />


<h2>Security Restrictions</h2>

. Disable USB storage

. Restrict control panel access

<img width="1448" height="944" alt="image" src="https://github.com/user-attachments/assets/ca30c73c-9092-4194-99e3-6d7bc4306203" />
<img width="1433" height="972" alt="image" src="https://github.com/user-attachments/assets/a08b7bdc-68db-46c1-a9bf-6ec245d2c8a4" />

<h2>Step 7 - Install Windows 10 Client</h2>

Create a windows 10 virtual machine.

Configuration:

. RAM: 2GB

. Bridged Adapter:


Assign IP settings:

. IP Address: 192.168.1.52

. DNS Server: 192.168.0.1

<h2>TESTING IP ADDRESS CONNECTIVITY: 192.168.1.52
<img width="1295" height="856" alt="image" src="https://github.com/user-attachments/assets/7c00465f-18fc-4dc0-a8a5-fe68e263a93e" />
<img width="1163" height="619" alt="image" src="https://github.com/user-attachments/assets/bb117325-ca47-4e29-9609-be3214e8d13e" />

<h2>Step 8 - Join Client Machine to Domain</h2>

Navigate to:

System -> Changing Settings -> Change

Join the domain:

Homelab.com

Use Domain Administrator credentials.

Restart the computer.

<h2>Step 9 - Test Domain Login</h2>

Log into the client machine using a domain account:
<img width="1055" height="578" alt="image" src="https://github.com/user-attachments/assets/9b6ac1c4-6a41-4d51-909c-5270c9a30e19" />

<h2>Step 10 (final step) - Monitor Authentication Logs</h2>

Open Event Viewer 

Navigate to:

Windows Logs -> Security


Review:

. Successful Login events

<img width="1248" height="857" alt="image" src="https://github.com/user-attachments/assets/28bb896d-696b-4e80-8f3c-cc72eebcb07a" />

<h2>Skills Demonstrated</h2>


. Active Directory Domain Services
. Windows Server Administration
. Organizational Unit Design
. User and Group Management
. Group Policy Configuration
. Domain Controller Deployment
. Client Machine Domain Joining
. Authentication Monitoring


<h2>Project Outcome</h2>


This project demonstrates the deployment and management of a centralized identity management system using Active Directory in a simulated business environment.
The infrastructure allows administrators to efficiently manage users, enforce security policies, and control access to network resources.


<h2>What I Learned</h2>


Through this project, I gained hands-on experience with deploying and managing a Windows-based directory service using Active Directory Domain Services.
I learned how to design and implement a structured domain environment by creating Organizational Units (OUs) to reflect real-world business departments. This improved my understanding of how to logically organize users, groups, and resources for efficient administration. I developed practical skills in user and group management, including creating domain users, assigning them to security groups, and applying role-based access control. This helped me understand how permissions and access are managed in enterprise environments.
Using Group Policy Management Console, I configured and applied Group Policy Objects (GPOs) to enforce security settings such as password policies, restricting access to system features, and controlling user environments. 

I also learned the importance of linking GPOs correctly to Organizational Units.
I successfully joined a Windows client machine to the domain, which strengthened my understanding of domain-based authentication and centralized user management.
Additionally, I used Event Viewer to monitor authentication logs and analyze security events such as successful logons, logoffs, and administrative activities. This gave me insight into how system administrators track user activity and troubleshoot issues.
Overall, this project helped me understand how enterprise IT environments are structured and managed, and improved my confidence in working with Windows Server, Active Directory, and system administration tools.




