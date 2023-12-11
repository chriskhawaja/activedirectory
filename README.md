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

