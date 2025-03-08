<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create Virtual Machines
- Observe ICMP Traffic
- Configuring a Firewall
- Observe SSH, DHCP, DNS, and RDP traffic

<h2>Actions and Observations</h2>

<h3>Create Virtual Machines</h3>

![image](https://github.com/user-attachments/assets/d6287013-d59a-47b5-9a9e-b18f2bf93710)
 
<p>
https://portal.azure.com/
(Create our Virtual Machines)
Create a Resource Group
Create a Windows 10 Virtual Machine (VM)
While creating the VM, select the previously created Resource Group
While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet
</p>

![image](https://github.com/user-attachments/assets/a894a7fd-da40-402f-a648-0d1cf90af8f0)
![image](https://github.com/user-attachments/assets/5eb2450f-fbf8-4230-ada5-03421015c768)
![image](https://github.com/user-attachments/assets/15ff4751-9af5-4613-8a75-2e3c69e82488)

<p>
Create a Linux (Ubuntu) VM
While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.
Authentication type: Username/Password
Ensure both VMs are in the same Virtual Network / Subnet

</p>
<br />

<h3>Observe ICMP Traffic</h3>

![image](https://github.com/user-attachments/assets/3fa21bdc-f398-4f08-befd-01948e59d675)

<p>
Use Remote Desktop to connect to your Windows 10 Virtual Machine.
 
Within your Windows 10 Virtual Machine, Install Wireshark.

Open Wireshark and start packet capture.

Within Wireshark, filter for ICMP traffic only.

Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM.

Observe ping requests and replies within WireShark.

</p>
<br />
<h3> Configure a Firewall</h3>

![image](https://github.com/user-attachments/assets/1875ddc5-da30-4581-ac5c-68f1fa806f9c)
![image](https://github.com/user-attachments/assets/4ac13b13-6e33-4ab2-86f3-630d1ca4ddae)

<p>
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity
Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)
Stop the ping activity

</p>
<br />
