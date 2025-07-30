# Joining-a-Windows-11-Virtual-Machine-to-an-Active-Directory-Domain

### Objective
Successfully configured and joined a Windows 11 virtual machine to a local Active Directory domain hosted on Windows Server 2022 within a Proxmox virtualized environment. Demonstrated the ability to manage networking, domain authentication, and system configuration across both client and server systems.

### Skills Learned
- Configuring static IP addresses and DNS for private domain networks
- Renaming client machines to follow enterprise naming conventions
- Joining Windows 11 machines to Active Directory domains
- Authenticating and testing domain user accounts
- Validating domain joins through Active Directory Users and Computers (ADUC)
- Troubleshooting network connectivity and DNS resolution issuess<br>
  <br>
### Tools Used
- Proxmox VE – Virtual environment for deploying and managing Windows VMs
- Windows Server 2022 – Active Directory Domain Services, DNS
- Windows 11 – Client OS for domain joining and testing
- Active Directory Users and Computers (ADUC) – For validating computer object entries
- Windows Settings and Control Panel – For networking and device configuration<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">
  
### Step 1: Verify Windows Server 2022 Network Configuration
On the Windows Server 2022 Domain Controller, update the network adapter settings. Ensure that the static IP address, subnet mask, default gateway, and DNS server (which should point to the local server IP) are configured correctly. This ensures that the server can be discovered by client machines on the same network.<br>
<br>
Why / How:
- Required for proper DNS resolution and domain join operations
- Ensures domain clients (like Windows 11 VM) can find and communicate with the Domain Controller<br>

<img src="https://github.com/user-attachments/assets/d35d01be-530f-4b0d-aa48-afe23e5b8e4f" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 2: Rename the Windows 11 VM for Domain Identification
Log in to the Windows 11 VM and search for "View your PC name" in system settings. Rename the device to WorkStation01 (WS01). This naming convention allows for easy identification of machines within Active Directory.

Why / How:
- Improves visibility and organization in Active Directory
- Enables administrators to quickly associate VMs with roles or users<br>  
<br>
<img src="https://github.com/user-attachments/assets/6c9a0935-3249-4c2c-ba54-1fdee5f49afe" width="1000">

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">

### Step 3: Configure Static IP on Windows 11 VM
Access the network settings of the Windows 11 VM. Set a static IP address on the same subnet as the Domain Controller. Ensure the default gateway matches the server’s, and point the DNS to the IP address of the Windows Server 2022 Domain Controller. This is essential for domain communication in a private lab environment.

Why / How:
- Static IP ensures consistent connectivity to the domain
- Necessary for DNS queries to resolve the domain name to the controller<br>
<br>

<img src="https://github.com/user-attachments/assets/ade9d7da-4f50-468e-b364-b7fd229a48d6" width="1000"><br>
<br>

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">

### Step 4: Join Windows 11 VM to the Domain
From Windows 11, open Access work or school settings and select Connect. At the bottom, click the link “Join this device to a local Active Directory domain.” Enter your domain name (e.g., DOOM.local) and proceed.

Why / How:
- Connects the machine to the domain for centralized authentication and management<br>
  <br>

<img src="https://github.com/user-attachments/assets/52ad5469-7bcf-42eb-b7d5-b5b669af00a3" width="1000"><br>
<br>

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">

### Step 5: Authenticate with Domain Credentials
Sign in using the Domain Administrator account credentials set up on the Domain Controller. Click Next, choose This device as a standard user, and allow the system to apply settings. Restart the computer to complete the domain join process.

Why / How:
- Domain credentials are required to authorize the join request
- A restart is necessary for the system to complete domain integration<br>
<br>

<img src="https://github.com/user-attachments/assets/2ac9532b-5636-4abf-bda6-a686e70ad0a8" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/bbc701bd-fc54-42bc-9d35-6ac0d6b7630c" width="1000">

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">

### Step 6: Confirm Domain Login on Windows 11 VM
After reboot, the login screen will now show the domain name (e.g., DOOM\administrator) at the bottom-left. Instead of logging in as administrator, select the test domain user bbarnes to confirm domain connectivity and user authentication.

Why / How:
- Confirms successful domain join
- Verifies domain user profiles can authenticate on the machine<br>
<br>
<img src="https://github.com/user-attachments/assets/ac783009-592c-4c62-be8e-c0b268a9c09c" width="1000">

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">

### Step 7: Verify Successful Login with Domain User
Log in to the Windows 11 VM using the domain user account bbarnes, which was created in Active Directory as Bucky Barnes. A successful login confirms that the user account is properly authenticated against the domain and that a new local profile is created for the domain user.

Why / How:
- Confirms the domain user account can authenticate on the client machine
- Validates that domain policies, permissions, and environment settings are being applied<br>
<br>
<img src="https://github.com/user-attachments/assets/ed2a0ed2-c6cb-4ada-855e-5d4f9094111c" width="1000"><br>
<br>

<hr style="border: 0.35px solid rgba(0, 0, 0, 0.05);">


### Step 8: Validate VM Registration in Active Directory
Log in to Windows Server 2022. Open Active Directory Users and Computers. Under the Computers container, confirm that WS01 appears as a joined machine. If multiple VMs were joined (e.g., WS02), they will also be listed here.

Why / How:
- Confirms that the VM was properly added to the domain
- Allows IT administrators to manage the device through Group Policy and AD<br>
<br>

<img src="https://github.com/user-attachments/assets/e8441c67-8a98-4bf8-a830-88fda9a88052" width="1000">



