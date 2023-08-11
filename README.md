<h2> Description</h2>

In the Network Traffic Analysis Lab, we embark on a comprehensive journey to explore the world of network traffic analysis within the context of Azure Virtual Machines. This tutorial not only provides insights into traffic patterns but also equips you with practical knowledge about managing security through Network Security Groups (NSGs). By leveraging a range of advanced tools, protocols, and environments, you'll gain hands-on experience in analyzing ICMP, SSH, DHCP, and DNS traffic. This process will enable you to understand, scrutinize, and manage network behavior effectively, ensuring robust security and optimal operational performance within the Azure ecosystem.


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1> 

<h2>High-Level Steps</h2>

- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="        " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Observe ICMP Traffic</h3>

- Use Remote Desktop to connect to your Windows 10 Virtual Machine
- Within your Windows 10 Virtual Machine, Install Wireshark
- Open Wireshark and filter for ICMP traffic only
- Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM
   - Observe ping requests and replies within WireShark
- From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark
- Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
   - Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
   - Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
   - Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using
   - Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
   - Stop the ping activity

</p>
<br />

<p>
<img src="      " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Observe SSH Traffic</h3>

- Back in Wireshark, filter for SSH traffic only
- From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)
   - Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark
   - Exit the SSH connection by typing ‘exit’ and pressing [Enter]

</p>
<br />

<p>
<img src=".       " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Observe DHCP Traffic</h3>

- Back in Wireshark, filter for DHCP traffic only
- From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
   - Observe the DHCP traffic appearing in WireShark

</p>
<br />

<p>
<img src=".         " height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<h3>Observe DNS Traffic</h3>

- Back in Wireshark, filter for DNS traffic only
- From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are
   - Observe the DNS traffic being show in WireShark

