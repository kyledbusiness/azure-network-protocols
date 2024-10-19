<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Analyzing Network Traffic Between Azure Virtual Machines</h1>
In this hands-on lab project, we delve into the intricacies of network traffic within Microsoft Azure by creating and configuring virtual machines (VMs). Utilizing Wireshark, we will capture and analyze various protocols—ICMP, SSH, DNS, and RDP—while implementing Network Security Groups (NSGs) to manipulate traffic flows. Join me as we uncover how these protocols interact and how security configurations can impact network behavior. <br />

<h2>Technologies and Tools</h2>

- Cloud Platform: Microsoft Azure
- Protocol Analyzer: Wireshark
- Operating Systems: Windows 10 Pro, Ubuntu Server 22.04
- Protocols Analyzed: ICMP, SSH, DNS, RDP
- Remote Access Tool: Microsoft Remote Desktop

<h2>Part 1: Setting Up the Environment</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 03 31 PM" src="https://github.com/user-attachments/assets/1f7e7fa0-a2b3-4aa5-841f-0ea058828f30">
</p>
<p>
Access Azure Portal

Set up a new Resource Group to organize resources effectively.

Create a Windows 10 Virtual Machine within the newly created Resource Group.

Enable the creation of a new Virtual Network (VNet) and Subnet during setup.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 11 44 PM" src="https://github.com/user-attachments/assets/6913065a-a751-4afa-9855-68429bd77bc2">
</p>
<p>
Spin up a Linux (Ubuntu Server) Virtual Machine, ensuring it's part of the same Resource Group and VNet as the Windows VM.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 29 31 PM" src="https://github.com/user-attachments/assets/ecd57e83-1258-4a1e-9842-9a8af23ded87">
</p>
<p>
If on a Mac, install Microsoft Remote Desktop.

Connect to the Windows 10 VM on Remote Desktop using the Public IP Address.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 33 32 PM" src="https://github.com/user-attachments/assets/cd09df62-0886-4731-92f9-39f124c7c7f7">
</p>
<p>
Wireshark Installation: Install Wireshark within the Windows 10 VM.
</p>
<br />

<h2>Part 2: ICMP Traffic Observation</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 41 24 PM" src="https://github.com/user-attachments/assets/9e6ad769-2fa1-4c7f-b292-95a320d85575">
</p>
<p>
Packet Capture: Launch Wireshark and filter to capture only ICMP traffic.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 43 18 PM" src="https://github.com/user-attachments/assets/3f528183-8ebc-4ab0-8084-81dec947d0ef">
</p>
<p>
Retrieve the private IP address of the Ubuntu VM and ping it from the Windows 10 VM.

Analyze the ping requests and responses in Wireshark.
</p>
<br />

<h2>Part 3: Network Security Group Configuration</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 51 22 PM" src="https://github.com/user-attachments/assets/8fc78528-f540-40e8-8c52-a7ad531ccef6">
</p>
<p>
Continuous ICMP Pings: Initiate a non-stop ping from the Windows 10 VM to the Ubuntu VM.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 53 30 PM" src="https://github.com/user-attachments/assets/000f4240-84fb-409f-a00a-dbc80ff57872">
</p>
<p>
Modify NSG Settings: Access the Network Security Group associated with the Ubuntu VM and disable incoming ICMP traffic.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 56 34 PM" src="https://github.com/user-attachments/assets/c8589e90-99f1-4a17-b5a4-bc0dad62297c">
</p>
<p>
Traffic Observation: 

Monitor the impact of this change in Wireshark and the command line output: "Request timed out" in PowerShell and only "Request" packets being retrieved.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 56 52 PM" src="https://github.com/user-attachments/assets/41ba3a59-1530-4c75-8fdb-bdadf800278d">
</p>
<p>
Revert the NSG settings to allow ICMP traffic again.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 7 57 50 PM" src="https://github.com/user-attachments/assets/f2daa0ef-0e0f-4445-8dd1-dab2851e6a01">
</p>
<p>
Observe the restoration of ping functionality and end the continuous ping.
</p>
<br />

<h2>SSH Traffic Analysis</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 8 03 09 PM" src="https://github.com/user-attachments/assets/fcb0bf0e-2b73-42ad-a010-2fe9b7a7553c">
</p>
<p>
SSH Traffic Capture: Start a new Wireshark capture session, filtering for SSH traffic.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 8 07 26 PM" src="https://github.com/user-attachments/assets/d0b7fd70-19df-46b8-871f-7f0f531ad13b">
</p>
<p>
Establish an SSH connection to the Ubuntu VM using its private IP address.

Execute commands (username, pwd, etc.) and watch the SSH traffic flow in Wireshark.
</p>
<br />

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 8 11 40 PM" src="https://github.com/user-attachments/assets/77a2f5da-effd-453f-95ba-f39b96a5f1ec">
</p>
<p>
Exit SSH: Terminate the SSH session by typing exit.
</p>
<br />

<h2>DNS Traffic Analysis</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 8 25 54 PM" src="https://github.com/user-attachments/assets/426f5753-3c82-4309-8725-e98b859ee4b9">
</p>
<p>
Capture DNS Traffic: Filter for DNS traffic in Wireshark.

Use nslookup to resolve IP addresses for sites like google.com and disney.com from the command line.

Analyze the DNS query and response packets in Wireshark.
</p>
<br />

<h2>RDP Traffic Analysis</h2>

<p>
<img width="2056" alt="Screenshot 2024-10-16 at 8 30 01 PM" src="https://github.com/user-attachments/assets/606fb75a-ca3e-4dbb-9dea-5f14af38e901">
</p>
<p>
Capture RDP Traffic: Filter for RDP traffic (tcp.port == 3389) in Wireshark.

Notice the ongoing flow of traffic, which results from the RDP protocol constantly transmitting data to maintain a live session. This includes regular updates, even without direct user interaction.
</p>
<br />

<h2>Conclusions</h2>

<p>
Through this project, we explored the dynamic network interactions between two Azure Virtual Machines while employing Wireshark for deep traffic analysis. By configuring Network Security Groups, we gained valuable insights into how security measures affect the flow of ICMP traffic and other protocols. This exercise enhanced my understanding of network behavior in cloud environments and showcased the importance of effective security configurations.
</p>
<br />
