

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In the Network Traffic Analysis Lab, we embark on a comprehensive journey to explore the world of network traffic analysis within the context of Azure Virtual Machines. This tutorial not only provides insights into traffic patterns but also equips you with practical knowledge about managing security through Network Security Groups (NSGs). By leveraging a range of advanced tools, protocols, and environments, you'll gain hands-on experience in analyzing ICMP, SSH, DHCP, and DNS traffic. This process will enable you to understand, scrutinize, and manage network behavior effectively, ensuring robust security and optimal operational performance within the Azure ecosystem.





<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Protocol (RDP)
- Various Command-Line Tools
- Diverse Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>Prerequisites</h2>

- Create Windows 10 (21H2) and Ubuntu Server 20.04 virtual machines on Microsoft Azure.

<h2>High-Level Steps</h2>

1. **Observe ICMP Traffic**
2. **Observe SSH Traffic**
3. **Observe DHCP Traffic**
4. **Observe DNS Traffic**
5. **Observe RDP Traffic**

<h2>Actions and Observations</h2>

### Observe ICMP Traffic

<p>
<img src="" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 1: Use Remote Desktop to Connect to Windows 10 VM</h3>
- Launch the Remote Desktop application.
- Enter the public IP address of your Windows 10 VM.
- Click "Connect" and provide your RDP credentials to access the Windows 10 VM.

<h3>Step 2: Install Wireshark Within Windows 10 VM</h3>
- Open a web browser on the Windows 10 VM.
- Visit the official Wireshark website and download the installer.
- Install Wireshark by running the downloaded installer.

<h3>Step 3: Open Wireshark and Filter ICMP Traffic</h3>
- Launch Wireshark from the Start Menu.
- Click on "Capture" and then "Interfaces."
- Select the network interface corresponding to your internet connection.
- Click "Start" to begin capturing traffic.
- In Wireshark's main window, apply a filter for capturing ICMP traffic.

<h3>Step 4: Retrieve Private IP of Ubuntu VM and Ping</h3>
- Log in to your Azure portal and navigate to your Ubuntu VM's overview page.
- Note down the private IP address of the Ubuntu VM.
- Return to the Windows 10 VM's command prompt.
- Ping the Ubuntu VM using its private IP.

<h3>Step 5: Observe Ping Requests and Replies in Wireshark</h3>
- Monitor the Wireshark interface to observe the ping requests and replies.

<h3>Step 6: Perform External Ping to www.google.com</h3>
- Open a new command prompt in the Windows 10 VM.
- Type `ping www.google.com` and press Enter.
- Analyze the corresponding traffic in the Wireshark interface.

<h3>Step 7: Initiate Continuous Ping and Manipulate NSG</h3>
- Open a new command prompt in the Windows 10 VM.
- Type `ping -t <Ubuntu_Private_IP>` and press Enter.
- In the Azure Portal, navigate to your Ubuntu VM's "Networking" section.
- Temporarily disable inbound ICMP traffic for the Ubuntu VM in its NSG settings.
- Monitor the changes in both the command prompt and Wireshark.
- Re-enable inbound ICMP traffic in the NSG settings and observe the restored ping functionality.
- Stop the continuous ping by pressing Ctrl+C in the command prompt.

</p>
<br />

### Observe SSH Traffic

<p>
<img src="https://" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 1: Filter Wireshark for SSH Traffic</h3>
- Return to Wireshark's main window.
- In the "Display Filter" field, enter `ssh` and press Enter.

<h3>Step 2: Establish SSH Connection</h3>
- Open a new command prompt in the Windows 10 VM.
- Type `ssh <Ubuntu_Private_IP>` and press Enter to initiate the SSH connection.
- Provide the required credentials to establish the connection.

<h3>Step 3: Observe SSH Traffic</h3>
- Observe the packets displayed in Wireshark as you interact with the SSH connection.

<h3>Step 4: Terminate SSH Session</h3>
- In the SSH session, type `exit` and press Enter to terminate the connection.

</p>
<br />

### Observe DHCP Traffic

<p>
<img src="https://" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 1: Filter Wireshark for DHCP Traffic</h3>
- Return to Wireshark's main window.
- In the "Display Filter" field, enter `dhcp` and press Enter.

<h3>Step 2: Request New IP</h3>
- Open a new command prompt in the Windows 10 VM.
- Type `ipconfig /release` and press Enter.
- Then type `ipconfig /renew` and press Enter to request a new IP.

<h3>Step 3: Observe DHCP Traffic</h3>
- Observe the DHCP-related packets in Wireshark as the IP renewal process takes place.

</p>
<br />

### Observe DNS Traffic

<p>
<img src="https:/" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<h3>Step 1: Filter Wireshark for DNS Traffic</h3>
- Return to Wireshark's main window.
- In the "Display Filter" field, enter `dns` and press Enter.

<h3>Step 2: Use nslookup</h3>
- Open a new command prompt in the Windows 10 VM.
- Type `nslookup google.com` and press Enter to retrieve Google's IP address.
- Repeat the process with `nslookup disney.com`.

<h3>Step 3: Analyze DNS Traffic</h3>
- Observe the DNS-related packets in Wireshark corresponding to the nslookup commands.

</p>
<br />


