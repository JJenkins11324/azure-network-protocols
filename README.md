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

- Create Resources
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic
- Cleanup

<h2>Actions and Observations</h2>

<p>
<img src="https://imgur.com/CSP8BO5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<img src="https://imgur.com/G6XvObR.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
First, create a resource group in the azure portal (portal.azure.com). Next, create a Windows VM, selecting the previously created resource group. Set and remember your Username and Password. Allow it to create its own vnet and subnet. While the first VM is deploying, create an Ubuntu VM and select the previously created resource group and vnet. Be sure to remember the login information for this VM as well.
</p>
<br />

<p>
<img src="https://imgur.com/YXn2FMm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, use remote desktop to login to your windows VM. When logged in, install Wireshark. This will allow us to monitor traffic that is sent and received between the two VMs. Open Wireshark and filter traffic to ICMP only. Attempt to ping the Ubuntu VM by obtaining the private IP address and using the command "ping (ip address)" in the command prompt.
</p>
<br />

<p>
<img src="https://imgur.com/YptTCx0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now, go back to wireshark and filter by SSH traffic. Open powershell and "SSH into" VM2 using the following command: ssh (username)@(private ip address). It will prompt you to continue anyways, and select yes. Then, enter the password to establish the connection. Note: The password will be hidden while you type it, but backspace does work if you mess up typing in the password. Observe the lines of traffic populating in wireshark. End the ssh connection to VM2 by typing exit and hitting enter.
</p>
<br />

<p>
<img src="https://imgur.com/gPhCZMo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in wireshark, filter to DHCP traffic only. From VM1, attempt to issue a new ip address using the command "ipconfig /renew" in command prompt. Note that this will end your remote session. After you reconnect, observe the traffic in wireshark.
</p>
<br />

<p>
<img src="https://imgur.com/WDhevho.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Back in Wireshark, filter for DNS traffic only. From your Windows 10 VM within a command line, use "nslookup" to see what google.com's ip address is. Observe the traffic in wireshark.
</p>
<br />

<p>
Back in Wireshark, filter for RDP traffic only using tcp.port == 3389. Note that traffic is constantly coming through, instead of just when a command is executed. This is because RDP is showing a live stream of traffic from one computer to another, therefore traffic is always being transmitted.
</p>
<br />

<p>
When you are done, be sure to delete both VMs and all resource packs in azure to prevent any excess charges.
</p>
<br />

<h2>🤳Connect with me:</h2>

[<img align="left" alt="Joseph | LinkedIn" width="22px" src="https://imgur.com/yJ22BHw.png" />][linkedin]
[<img align="left" alt="Joseph | Instagram" width="22px" src="https://imgur.com/JnlEgDK.png" />][instagram]
[<img align="left" alt="Joseph | Discord" width="22px" src="https://imgur.com/YGezWPR.png" />][discord]


[instagram]: https://www.instagram.com/jenkins5937/
[linkedin]: https://www.linkedin.com/in/joseph-jenkins-521a49241
[discord]: https://www.discordapp.com/users/262825628695396352
