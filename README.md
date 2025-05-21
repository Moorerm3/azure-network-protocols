<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04
  

<h2>Actions and Observations</h2>

![image](https://github.com/user-attachments/assets/6c21a9a7-3176-47e0-aac4-d60d29c7ad69)

Go to Wireshark and download the Windows x64 Installer. Click Next on everything until Wireshark is downloaded. Choose the Ethernet setting and Filter for *ICMP* Traffic.

![image](https://github.com/user-attachments/assets/7f2e0f43-9590-43b8-a6f9-4694bb3e684d)

After you set the filter to ICMP, open up Windows PowerShell and ping the private address of the Linux virtual machine Private Address. You will now be able to see the ping traffic through Wireshark.

![image](https://github.com/user-attachments/assets/293d5d62-09b0-4121-842e-ee8122031bd9)

Using PowerShell ping "*google.com*", you can now see the traffic through Wireshark.

![image](https://github.com/user-attachments/assets/13f98e64-8617-4104-8fe4-c2164d0182f5)

Initiate a perpetual ping on Windows PowerShell, using "*ping *Private IP Address* -t*"

![image](https://github.com/user-attachments/assets/d5ec111e-95b4-4042-953b-598ce1f87653)

Open the Network Security Group that your Ubuntu VM is using, Linux-VM -> Networking ->Network settings -> Rules, and disable incoming (inbound) ICMP traffic.

![image](https://github.com/user-attachments/assets/4a55df10-22ac-4bc7-90b6-92a5c8dc5812)

In the Windows 10 VM, observe the ICMP traffic in Wireshark and the command line Ping activity.

![image](https://github.com/user-attachments/assets/34d7d3c7-191c-413b-94b2-0a1bf7866c48)

Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is on by deleting the security rule, which will allow traffic through the Virtual Network.

![image](https://github.com/user-attachments/assets/18b3e8cb-a263-4219-aae4-9196cc303b3e)

In the Windows 10 VM, observe the ICMP traffic in Wireshark and the command line Ping activity (should start working). Use Ctrl-C through PowerShell to stop the ping.
