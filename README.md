<p align="center">
<img src="https://i.imgur.com/VvEfgCC.jpeg" height="80%" width="80%" alt="Setting Up in Azure"/>
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
Ensure that both VM will be on the same virtual network. 
![Screenshot 2025-03-13 102241](https://github.com/user-attachments/assets/9e365a94-06ea-4cc9-ba4d-d30c43184293)
![Screenshot 2025-03-13 102219](https://github.com/user-attachments/assets/0f6479c4-0457-4282-b755-762a859450c7)
<br />
- Use WinVM public IP and connect to it using RDP
- After I am connected to WinVM, I will download Wireshark on the VM
- Use Wireshark to observe network traffic
<img src="https://i.imgur.com/qCIJYSG.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
To filter for ICMP (Internet Control Message Protocol) traffic in Wireshark, type "ICMP" in the filter bar. To generate traffic, retrieve the private IP address of VM2 and ping it using PowerShell.  <br/>
<br />
<img src="https://i.imgur.com/MG6FzdI.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
I can configure the firewall to block ICMP traffic by running a perpetual ping command in PowerShell.  <br/>
<img src="https://i.imgur.com/HGNy9PE.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, I will go to VM2's network security group and create a new inbound security rule denying all ICMP traffic making sure to put its priorty highest, so it will take precedence before all other rules:  <br/>
<img src="https://i.imgur.com/H2zVFyt.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Going back to our VM we can see that the ICMP echo requests aren't getting any responses due to the security change:  <br/>
<img src="https://i.imgur.com/MoFJ39C.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
To revert the change I can either switch the inbound rule to "Allow" instead of "Deny" or delete the rule:  <br/>
<img src="https://i.imgur.com/4tetl2l.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now ICMP echo requests are back to getting responses:  <br/>
<img src="https://i.imgur.com/FPXmXdY.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now I will filter to only show SSH (Secure Shell) traffic by typing SSH into the bar at the top and I will SSH into VM2 using PowerShell:  <br/>
<img src="https://i.imgur.com/blrFX07.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
I can type commands like pwd (print working directory) and observe the traffic:  <br/>
<img src="https://i.imgur.com/Corgjvn.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
After filtering for DHCP (Dynamic Host Configuration Protocol) traffic, I attempted to get a new IP address by using the ipconfig /renew command:  <br/>
<img src="https://i.imgur.com/Zq7X1Zv.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Filtering for DNS (Domain Name System) traffic, I can use nslookup to find IP addresses for domain names like "www.google.com" and "www.amazon.com":  <br/>
<img src="https://i.imgur.com/3cGR7xZ.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Finally, I'll observe RDP (Remote Desktop Protocol) traffic by typing in "tcp.port == 3389" in the top bar. You'll notice there is traffic happening without us doing anything. This is because I used RDP to connect to this machine from my own computer and RDP shows us a constant live stream of whats happening:  <br/>
<img src="https://i.imgur.com/0eQAkky.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
