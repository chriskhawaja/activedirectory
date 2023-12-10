![image](https://github.com/chriskhawaja/activedirectory/assets/153021794/56c8463a-c1c7-4849-b776-fd015bdf292f)






<h1>Installing Active Directory in Microsoft Azure</h1>

<h2>Project Summary</h2>
This project involves the creation of two virtual machines. One of the virtual machines will be running a Windows Server 2019 image, while the other one will be running a Windows 10 Pro image. Once both VM's are created, we will boot into the VM running Windows Server, and through server manager, convert the VM into a domain controller. Furthermore, we will use the VM to install Active Directory Domain Services and connect the Windows 10 Pro VM (Client) to our domain (Windows Server 2019). Once Active Directory is installed on our domain controller, we will create organizational units, users, security groups, containers, disable/unlock accounts, and reset passwords. Additionally, we will sign-on to a user account that we created in our domain, from our client VM. In the end, this project will teach users about basic Active Directory fundamentals. 
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

<h2>Project Demonstration</h2>

- Step 1
  - Create a Resource Group within Microsoft Azure
![image](https://github.com/chriskhawaja/azure-network-protocols/assets/153021794/36006b36-ffd9-41f5-9f41-7f04ae2ce17e)

- Step 2  - within the Resource Group that was created
  - Create an Azure Virtual Machine running a Windows 10 Pro Image
  - Make sure to place this Virtual Machine into the resource group that was created
  - Ensure that 2 Virtual CPU's are selected
  ![image](https://github.com/chriskhawaja/azure-network-protocols/assets/153021794/baef5b4a-f3ed-40d2-90d6-fcd570da6d1c)

- Step 3
  - Before booting into your VM, make sure to download and create and account for Proton VPN
    - This is because downloading Proton VPN in a VM can be challenging
    - Whenever you use a VM in Azure, the VM can be anywhere in the world
      - If your VM is in France, you might have trouble download Proton VPN on Google when everything is in French
      - Make sure to copy the URL, and then once you are in your VM, paste the link into Google
- Also, take note of your IP address on your computer before remoting into your VM
  - You can do this by typing in "what is my IP address" on Google and clicking the first link 
    ![image](https://github.com/chriskhawaja/vpn/assets/153021794/2aceaf82-5081-4030-a432-98396b8c05e6)
![image](https://github.com/chriskhawaja/vpn/assets/153021794/26bff450-c222-4f85-adf1-6aebe0852a16)

- Step 4
  - Utilizing RDP on Windows, remote into Virtual Machine 1 (Windows Pro) - by typing in the IP Address
  - If using a Mac computer, go to the app store and download the Microsoft Remote Desktop application
  - You will be prompted with a login screen - use the credentials you provided during the virtual machine creation process
![image](https://github.com/chriskhawaja/azure-network-protocols/assets/153021794/6d103328-f103-429d-aef5-f47c17e1aa1b)


- Step 5
  - Once you are booted into the Virtual Machine, proceed to look up your IP address
    - This will be different than your normal IP address outside of your VM
      - You can observe that a VM has some similarities to a VM
        - You can see that this VM IP address states that I am in Phoenix, when in actuality, I am in a completely different state
        - I am able to access a VM within my normal desktop computer, and have it appear that I am literally in Phoenix, when I am not
 ![image](https://github.com/chriskhawaja/vpn/assets/153021794/448cef4f-e60f-443e-9448-e1c47402a94d)


- Step 6
  - Once you have pasted the Proton VPN download link, open Proton VPN in the VM, and sign on with the credentials that you made
  - Select "quick connect" to access a random VPN server somewhere in the world
![image](https://github.com/chriskhawaja/vpn/assets/153021794/277e9dac-3e52-4c7d-aea3-46b6145c6441)


- Step 7
  - We are now connected to a VPN server in Japan
  - Visit websites such as www.google.com and www.netflix.com to see the difference
    - You can note the differences in language and the presentation of different Japanese shows
![image](https://github.com/chriskhawaja/vpn/assets/153021794/0f800a58-fe7c-42e6-b401-5a8ef8d0cef3)
![image](https://github.com/chriskhawaja/vpn/assets/153021794/a95d70b3-a831-497b-99c4-ddf84b597e5f)
![image](https://github.com/chriskhawaja/vpn/assets/153021794/12975747-ccbc-4555-8eb9-3a44a26b14eb)


- Step 8
  - Be sure to search on google for "what is my ip address?"
    - Notice the change in IP address from our original VM IP address
    - Remember, this is because we are connected to a VPN server in Japan
![image](https://github.com/chriskhawaja/vpn/assets/153021794/0bd495e1-52cd-40be-b281-d150ff296e8f)

- Step 9
  - Feel free to select "change server" to access different VPN servers around the world
  - As you can see, after changing the VPN server, it now shows we have the IP address of a location in the Netherlands
    - However, we are not actually in the Netherlands
  ![image](https://github.com/chriskhawaja/vpn/assets/153021794/fdb94271-8d59-4154-bd63-572e2ef56522)
