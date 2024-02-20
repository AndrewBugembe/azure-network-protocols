<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security and Inspecting Traffic Between Azure Virtual Machines</h1>
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

- Windows 11 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

-	Create two VMs, Windows and Linux on Microsoft Azure
-	Connect to the Windows VM using RDC.
-	Install network protocol analyzer (WIRESHACK)
-	Monitor ICMP
-	Block ICMP on Ubuntu/LINUX vm
-	Connect to Ubuntu vm and monitor ssh protocol.
-	Monitor dns, dhcp and rdc protocols


<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/m588Flx.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a windows VM on azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/G2rN4FL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create an Ubuntu Linux VM on azure.
</p>
<br />

<p>
<img src="https://i.imgur.com/OcwWJgi.png" width="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Connect the windows VM through Remote Desk Connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/yBDEyzf.png" alt="Disk Sanitization Steps"/>
</p>
<p>
•	Download and Install network protocol analyzer (WIRESHACK)
</p>
<br />

<p>
<img src="https://i.imgur.com/Dv8owsM.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Enter ICMP in the wireshack monitor tab to analyze ICMP traffic using the ping command and VM2 private ip address.
</p>
<br />

<p>
<img src="https://i.imgur.com/sv77IhR.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Analyze and monitor wireshack displaying the ICMP traffic activity.
</p>
<br />

<p>
<img src="https://i.imgur.com/t73JPGP.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Using the '-t' option in the ping command, initialize a continuous ping to VM2 while monitoring ICMP traffic on wireshack.
</p>
<br />

<p>
<img src="https://i.imgur.com/tVzxJFe.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Add new inbound rule on Linux VM blocking ICMP traffic:access the linux VM through the azure portal, click the networking tab and then click 'add inbound port rule'.
</p>
<br />

<p>
<img src="https://i.imgur.com/f9r9liU.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Monitor and analyze changes in ICMP traffic both in the cmd terminal and wireshack dashboard after blocking ICMP traffic on the Linux VM. You will notice after the newly configured inbound port rule on the linux vm, ICMP traffic is blocked and does not return any data packets from the vm.
</p>
<br />

<p>
<img src="https://i.imgur.com/IQ051Y4.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Using a private key downloaded from the ubuntu linux vm, connect to the vm using ssh command, its ip address and full path to the private key on the local machine. Enter and monitor ssh traffic through the wireshack dashboard either typing ssh or tcp.port == 22.(ssh command: ssh -i <full path to the private key> user@vm-ipaddress)
</p>
<br />

<p>
<img src="https://i.imgur.com/ASuUXAQ.png" alt="Disk Sanitization Steps"/>
</p>
<p>
After connecting and logging into the Linux VM, monitor the ssh traffic on wireshack.
</p>
<br />

<p>
<img src="https://i.imgur.com/aqWOaaA.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
With every command executed in the linux vm terminal, wireshack monitors and reflects the activity .
</p>
<br />

<p>
<img src="https://i.imgur.com/U6mSjql.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Enter dns in the wireshack monitoring tab to monitor dns traffic. You will notice ongoing traffic being captured especially if you have open webpages in the background which use dns(domain name system) to resolve domain names into ip addresses.
</p>
<br />

<p>
<img src="https://i.imgur.com/jPboTLc.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Using a command like 'nslookup www.google.com' will task the dns to resolve and return the ip address of the domain name. Wireshack tracks and monitors the activity as dns is resolving the domain name .
</p>
<br />

<p>
<img src="https://i.imgur.com/3rt69fv.png" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
DHCP(dynamic host configuration protocol) can be monitored by wireshack using cli commands like ipconfig, ipconfig /all and ipconfig /renew as it assigns new ip addresses to the server.
</p>
<br />

<p>
<img src="https://i.imgur.com/omSKV4d.png" alt="Disk Sanitization Steps"/>
</p>
<p>
Wireshack monitors dhcp activity as it assigns a new ip address.
</p>
<br />

<p>
<img src="https://i.imgur.com/KNTceQC.png" alt="Disk Sanitization Steps"/>
</p>
<p>
RDP/RDC; remote desktop protocol (port 3389) is used to connect and access servers remotely. It can be monitored using wireshack to analyze any traffic.
</p>
<br />

