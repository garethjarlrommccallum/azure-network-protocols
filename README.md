<p align="center">
 
  ![image](https://github.com/user-attachments/assets/5eef274e-ec27-4f5e-a4b7-765a77f2fe2b)

<br />

<h1>Azure Virtual Machines and Networking</h1>


<h2>Objective</h2>
Creating two virtual machines and a network where I monitor network traffic with Wireshark. This is all done within Microsoft Azure while using Remote Desktop.
<br />


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b> 
- <b>Wireshark</b>
- <b>Various Network Protocols (ICMP, SSH, DHCP, DNS)</b>
- <b>Command-Line Tools</b>

<h2>Operating Systems Used </h2>

- <b>Windows 10</b>
- <b>Ubuntu 24.04</b>

<h2>Project Walk-through:</h2>

<p align="center">
Navigate to Microsoft Azure and create a resource group: <br/>

 ![Screenshot 2025-03-12 141630](https://github.com/user-attachments/assets/dc30ffa4-070d-43a9-89c2-9d250c684e38)
<br />
<br />
Create and Set up a Windows 10 virtual machine:  <br/>
![Screenshot 2025-03-12 142508](https://github.com/user-attachments/assets/3c613bc2-1679-4c5c-bc65-cbb2f8209b7d)
<br />
<br />
![Screenshot 2025-03-12 145552](https://github.com/user-attachments/assets/d5c6d3ea-deb2-4aa5-b0a1-8a1a8458cfc5)
<br />
<br />
Create and Setup a second VM using Linux:  <br/>
![Screenshot 2025-03-12 150315](https://github.com/user-attachments/assets/2dbfdf9d-613c-4d68-a541-7a272fc68481)
<br />
<br />
Ensure that both VM will be on the same virtual network. <br/>
![Screenshot 2025-03-13 102241](https://github.com/user-attachments/assets/9e365a94-06ea-4cc9-ba4d-d30c43184293)
![Screenshot 2025-03-13 102219](https://github.com/user-attachments/assets/0f6479c4-0457-4282-b755-762a859450c7)
<br />
- Use WinVM public IP and connect to it using RDP <br/>
- After I am connected to WinVM, I will download Wireshark on the VM< br/>
- Use Wireshark to observe network traffic <br/>
<img src="https://i.imgur.com/qCIJYSG.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
To filter for ICMP (Internet Control Message Protocol) traffic in Wireshark, type "ICMP" in the filter bar. To generate traffic, retrieve the private IP address of LinuxVm and ping it using PowerShell.  <br/>
<br />
<img src="https://i.imgur.com/MG6FzdI.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
I can configure the firewall to block ICMP traffic by running a perpetual ping command in PowerShell. <br/>
<br />
<img src="https://i.imgur.com/HGNy9PE.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
- I will create a high-priority inbound security rule in LinuxVM network security group to deny all ICMP traffic.  <br/>
- Returning to our VM, we observe that the ICMP echo requests no longer receive responses, confirming the effect of the security change.  <br/>
<br />
<img src="https://i.imgur.com/MoFJ39C.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
Next, I will filter to only show SSH (Secure Shell) traffic by typing SSH into the search bar at the top and I will SSH into my LinuxVm using PowerShell:  <br/>
<br />

![image](https://github.com/user-attachments/assets/c1dbcaf8-deb9-4828-9303-1d85d01e462e)
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
