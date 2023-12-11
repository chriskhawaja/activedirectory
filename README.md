![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/56c8463a-c1c7-4849-b776-fd015bdf292f)






<h1>Installing Active Directory in Microsoft Azure</h1>

<h2>Project Summary</h2>
This project involves the creation of two virtual machines. One of the virtual machines will be running a Windows Server 2019 image, while the other one will be running a Windows 10 Pro image. Once both VM's are created, we will boot into the VM running Windows Server, and through server manager, convert the VM into a domain controller. Furthermore, we will use the VM to install Active Directory Domain Services and connect the Windows 10 Pro VM (Client) to our domain (Windows Server 2019). Once Active Directory is installed on our domain controller, we will create organizational units, users, security groups, disable/unlock accounts, and reset passwords. Additionally, we will sign-on to a user account that we created in our domain, from our client VM. In the end, this project will teach users about basic Active Directory fundamentals. 
<h2>Platforms and Technologies Used</h2>

- Microsoft Azure (Virtual Machine Deployment)
- Powershell (Creating users in Active Directory)
- Azure Resource Group (Contains VM's)
- RDP (Remotely Accessing Virtual Machines)
  - TCP Port 3389
- Server Manager (Installing Active Directory)
<h2>Operating Systems Used </h2>

- Windows 10 Pro (Client)
- Windows Server 2019 (Domain Controller)

<h2>Installation of Active Directory</h2>

- Step 1
  - Create a Resource Group within Microsoft Azure
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/8b1c5692-8724-491e-b741-8b5e7c4b0291)


- Step 2  - within the Resource Group that was created
  - Create an Azure Virtual Machine running a Windows Server 2019 Image
  - Make sure to place this Virtual Machine into the resource group that was created
  - Ensure that 2 Virtual CPU's are selected
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d6fc0dd9-b018-47fd-8c82-1839f478febd)


- Step 3
 - Repeat this same process except choose the Windows 10 Pro Image and create
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/7c687135-5c6a-4137-a14b-44a2374277b7)

- Step 4
  - Before we can boot into our VM, we have to set the IP address of our VM1 to static
    - Since this VM will be our domain controller (server), it needs to have a static IP address, rather than a dynamic IP address
    - Servers will typically be configured with static IP addresses
   - To do this, we will go to our domain controller VM (DC-1), and click the networking tab on the left
   - We will then click "dc-1959_z1", which is to the right of "Network Interface:"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/aa8aaef3-3bff-40f7-b84e-c95ea94383e5)
- We will then clikc the "IP Configurations" tab on the left and select "ipconfig1" under Name 
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/a74e1be7-0f89-4cd8-915e-e5b4b8cc1975)
Under Allocation, we will select "Static" and press "Save"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/f4af4642-38e8-406b-9b84-8b28e2ae79a1)

- Step 5
  - You can now boot into the virtual machine via RDP (Reference previous labs if there is any confusion on how to do this)
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/22068aae-be66-4273-bd6b-db4b3b2178ca)


- Step 6
 - Once you boot into the VM and Server Manager loads up, select "Add roles and features" under "Configure this local server"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/b9914c00-e73f-4650-9b2d-bf1057b9735b)
- Proceed through the installation wizard and once you reach the "Select Server Roles" section, be sure to select "Active Directory Domain Services"
  - Select "Add features"
  - Select "Install" and wait for Active Directory to install
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/94c17972-d444-42d7-bbc2-c56376b9b959)
- Close out of the installation wizard and select the flag with the exclamation mark (towards top right of screen)
  - Select "Promote this server to a domain controller" 
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/dca853d2-49e4-478e-8b88-cdc20e9fc8c4)
- Once the Deployment Configuration Wizard pops up, select "add new forest", and create your domain name
  - Make sure to remember the password you set for your domain
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fcf4d4aa-dd5b-458f-a332-eedf276bd504)
- Proceed through all the other steps by clicking next and select "install" (You will be signed out and asked to login again
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/4a14a7af-65c8-418b-b4a4-5f874395bcd5)
- Once you remote back into the VM, you have to make sure that your are logging in correctly
  - Since this is a Domain Controller now, you must enter the domain name, followed by a "\" and your username
  - Enter the password you created for the domain as well
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/9511d9cf-7323-4787-8a25-6b4cfca36ca9)

- Step 7
  - Load up Server Manager from the start menu at the bottom left corner
  - Once in Server Manager, select "Tools" from the top right
  - Under Tools, select "Active Directory Users and Computers"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d4a2459d-5ea6-4e3d-b5ae-bb86179e6d83)
- We can now create organization units by right clicking "www.mydomain.com", hovering over new, and selecting "organizational unit"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fac3b8bf-054f-4690-9d72-501f96c715d5)
- We can now create our first user by clicking our organization unit "_EMPLOYEES"
- Right-clicking anywhere in the blank space
- Hovering over new and selecting "user"
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/eb316b28-e1b5-4121-8ad6-5ec7cb6d607f)
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/22f5479d-72a1-4823-9f86-a9781d7f0da6)
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d6e31ff2-0b88-4301-867d-2eaa6b1b01a2)
- We can now create a security group for the Accounting department and add Jane Doe to the group
- Select "Users"
- Right-click in the blank space and hover over "New"
- Select "Group"
- We will name the group "Accounting" and make sure it is a security group
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/2c6e60c4-d11d-452c-92e4-8979be9c7997)
- Now, we can add Jane Doe to the Accounting Security Group
- Select "Employees"
- Right-clik on Jane Doe
- Select "Add to Group" and we will type in Accounting
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d0055219-bc48-4f0d-b272-44626e52b05b)
- We will now add 1,000 users into an OU called "_EMPLOYEES_FROM_PS"
  - Be sure to open Powershell ISE from the start menu
  - Select the white paper logo under "File"
  - Copy and paste the script into Powershell
  - Press the green arrow to run the script
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/b1478b27-7cd7-45ea-a2a3-e3533d8525ac)
- We can now select the "_EMPLOYEES_FROM_PS" OU
- Right-click on any random user created and select "Reset Password"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/ce7d1766-28e9-4ade-a2b5-61339688dc0e)
- If we want to ensure that their password must be rest upon login, we can double-click on any random user
- Select the "Account" tab
- Make sure that "User must change password at next logon" is checked
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/a5a1cc7a-6459-4d57-9490-8c76c6af0de5)
- We can also disable accounts by right-clicking on the user and selecting "disable account"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/2ec234d4-6c1b-4bd9-9c82-9dba824fd5ae)
- We can also unlock a user's account by double-clicking on their name, selecting the "Account" tab, and checking "Unlock Account"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fd8ce371-d28f-4f43-a16e-293cd6ebf6fd)

- Step 8
  - We will now connect our VM2 (Client) to our Domain (VM1)
  - First, we need to change the DNS server to match the private IP address of VM1, rather than the virtual network DNS
    - The DNS must match the domain controller's private IP address to connect to the domain
  - In Azure, go to the client VM and select the "Networking" tab on the left 
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/854d3f2a-f222-421c-a15d-48a08a6de574)
- Select DC-1-vnet/default, which is to the right of "Virtual network/subnet:"
- From there, select "DNS Servers" tab on the left, and choose "custom" under DNS servers
  - Input the private IP Address of VM1 (Domain Controller) and select "save"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/c2a32a4e-bdd6-44ab-9782-06210c03a9e5)
- Be sure to restart the client VM
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/3713ed54-7419-49c0-853c-405bf0bfdf3f)
- Remote into the Client VM
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/937f6abd-5a7e-4b22-a7a3-8f20f8f5872c)
- Right-click on the Windows logo in the bottom left corner and select "System"
- Under "Related Settings", select "Rename this PC (Advanced)"
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/db974659-d0a8-47c7-99ae-6a6c3a2ba13e)
- Below Network ID, select the "Change" button and input your domain name
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/d60030e2-601c-4fe1-9972-59071ea9bbb7)
- Since we created 1,000 accounts on the DC, we will use one of those accounts to connect the Client to the Domain
 ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/028b8ea0-164a-4b79-b59d-8385ab237b2b)
- We can now see that our Client-VM is connect to our Domain Controller
![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/e42753a7-3a6a-4374-8b34-a277378850af)
- Log out of the session and sign-on using one of the accounts made in AD

- Step 9
   - We will now allow users to remotely access the domain
   - Go to system settings, under Related Settings, select "Remote Desktop"
   - Select at the bottom - "Select users who can remotely access this PC"
   - Be sure to add "Domain Users"
     ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/42870c26-fd05-453a-ad06-c9763283a28f)
- As you can see, we are officially signed onto VM2 with the bat.juko account we made in AD
  ![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/fc21a174-5b5f-4423-8a96-4ebf55257de0)

