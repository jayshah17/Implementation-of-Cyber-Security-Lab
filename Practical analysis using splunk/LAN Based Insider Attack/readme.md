## Lan Based Insider Attack

Making use of Ettercap/arpspoof tool to perform ARP Cache Poisoning based attacks in a LAN environment:

### 1. Password Stealing using ARP Cache Poisoning attacks

High-Level Summary

> ARP (Address Resolution Protocol) cache poisoning is a technique used by attackers to intercept network traffic between two hosts on a local network. In the context of ettercap, a popular network sniffing and MITM (Man-in-the-Middle) tool, the ARP cache poisoning plugin is used to perform this attack.

Recommendations	

> In Victim we will start Splunk Universal Forwarder and Collector will collect the logs of http

Methodologies	

> When the ARP cache poisoning plugin is enabled in ettercap, it sends fake ARP messages to the hosts on the local network, which causes them to update their ARP cache with a fake MAC address for a particular IP address. This allows the attacker to intercept network traffic between two hosts on the local network by redirecting the traffic to their own machine.

Information Gathering

>  For this attack, we have to take 2 VM Machine
  - Kali (Attacker) : 192.168.1.116
  - Kali (Victim) : 192.168.1.115

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/437fc4e3-149a-42af-9f8f-36818f619c94)

Splunk SIEM is used to capture the logs of Firewall

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/941e2cd0-b80f-4b8c-912b-5667c5898727)


Service Enumeration

> N.A.	

Penetration	

> Attacker will start ettercap tool to perform arp poisoning

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/17582768-91fe-410a-8642-10b5bc50cb24)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/f6230892-e922-4048-bf48-d42a4dfb8596)

It will scan all hosts in that network

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4c4edc3f-00d4-4812-bcbe-19ae9b1047e3)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/ed86e8ca-fa00-4f39-8a27-636c84b10ae0)

Add Victim's IP-address as Target 2

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b2cdcab4-8733-47ea-9db0-7aedcaca1e76)

Start Arp Cache Poisoning

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/661e456c-e17c-47e5-aa33-f937bf2f9701)

In Victim Side, Open an http web page which will be in unencrypted format 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/6a8fb5a0-f231-41e8-96e5-6d0155b3dbe7)

If victim enters username and password in http web page so attacker will be able to detect the username and password.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0e4df768-923d-41bd-98da-950f193e6ca0)

Report – House Cleaning

> Clean up was conducted after assessment of each target to remove any artifacts from the penetration test. The removals included any user accounts created and any files uploaded to the targets. Additionally, any configuration changes made were reverted to their original state. 


   
