<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Analyzing Network Traffic Between Azure Virtual Machines</h1>
In this hands-on lab project, we delve into the intricacies of network traffic within Microsoft Azure by creating and configuring virtual machines (VMs). Utilizing Wireshark, we will capture and analyze various protocols—ICMP, SSH, DHCP, DNS, and RDP—while implementing Network Security Groups (NSGs) to manipulate traffic flows. Join me as we uncover how these protocols interact and how security configurations can impact network behavior. <br />

<h2>Technologies and Tools</h2>

- Cloud Platform: Microsoft Azure
- Protocol Analyzer: Wireshark
- Operating Systems: Windows 10 (21H2), Ubuntu Server 20.04
- Protocols Analyzed: ICMP, SSH, DHCP, DNS, RDP
- Remote Access Tool: Microsoft Remote Desktop

<h2>Part 1: Setting Up the Environment</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Access Azure Portal: Azure Portal
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Resource Group Creation: Set up a new Resource Group to organize resources effectively.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Windows 10 VM Setup:

- Create a Windows 10 Virtual Machine within the newly created Resource Group.
- Enable the creation of a new Virtual Network (VNet) and Subnet during setup.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ubuntu VM Setup:
  
- Spin up a Linux (Ubuntu) Virtual Machine, ensuring it's part of the same Resource Group and VNet as the Windows VM.
- Choose Username/Password for authentication.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Network Configuration: Confirm that both VMs are residing in the same VNet/Subnet.
</p>
<br />

<h2>Part 2: ICMP Traffic Observation</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Remote Desktop Access:

- If on a Mac, install Microsoft Remote Desktop.
- Connect to the Windows 10 VM using Remote Desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Wireshark Installation: Install Wireshark within the Windows 10 VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Packet Capture: Launch Wireshark and filter to capture only ICMP traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ping Ubuntu VM:

- Retrieve the private IP address of the Ubuntu VM and ping it from the Windows 10 VM.
- Analyze the ping requests and responses in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Public Website Ping: Use the command line to ping a public site (e.g., www.google.com) and observe the traffic in Wireshark.
</p>
<br />

<h2>Part 3: Network Security Group Configuration</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Continuous ICMP Pings: Initiate a non-stop ping from the Windows 10 VM to the Ubuntu VM.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Modify NSG Settings: Access the Network Security Group associated with the Ubuntu VM and disable incoming ICMP traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Traffic Observation: Monitor the impact of this change in Wireshark and the command line output.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Re-enable ICMP Traffic: Revert the NSG settings to allow ICMP traffic again and observe the restoration of ping functionality.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Stop Pinging: End the continuous ping process.
</p>
<br />

<h2>SSH Traffic Analysis</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
SSH Traffic Capture: Start a new Wireshark capture session, filtering for SSH traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
SSH Connection:

- Establish an SSH connection to the Ubuntu VM using its private IP address.
- Execute commands (username, pwd, etc.) and watch the SSH traffic flow in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Exit SSH: Terminate the SSH session by typing exit.
</p>
<br />

<h2>DHCP Traffic Analysis</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Capture DHCP Traffic: Filter for DHCP traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Renew IP Address:

- From the Windows 10 VM, request a new IP address with ipconfig /renew.
- Observe the DHCP interactions in Wireshark
</p>
<br />

<h2>DNS Traffic Analysis</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Capture DNS Traffic: Filter for DNS traffic in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
DNS Lookup:

- Use nslookup to resolve IP addresses for google.com and disney.com from the command line.
- Analyze the DNS query and response packets in Wireshark.
</p>
<br />

<h2>RDP Traffic Analysis</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Capture RDP Traffic: Filter for RDP traffic (tcp.port == 3389) in Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Continuous RDP Stream: Notice the ongoing flow of traffic, which results from the RDP protocol constantly transmitting data to maintain a live session. This includes regular updates, even without direct user interaction.
</p>
<br />

<h2>Conclusions</h2>

<p>
Through this project, we explored the dynamic network interactions between two Azure Virtual Machines while employing Wireshark for deep traffic analysis. By configuring Network Security Groups, we gained valuable insights into how security measures affect the flow of ICMP traffic and other protocols. This exercise enhanced our understanding of network behavior in cloud environments and showcased the importance of effective security configurations.
</p>
<br />
