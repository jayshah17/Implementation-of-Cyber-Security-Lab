# LAN Based Insider Attack

Making use of Ettercap tool to perform ARP Cache Poisoning and ICMP Redirect based attacks in a LAN environment:

## 1. Perform ARP Cache Poisoning 

We can steal password from usecured websites as it will be in plain text so it can be retrieved

### How ARP Poisoning works ?

>> ARP (Address Resolution Protocol) cache poisoning is a technique used by attackers to intercept network traffic between two hosts on a local network. In the context of ettercap, a popular network sniffing and MITM (Man-in-the-Middle) tool, the ARP cache poisoning plugin is used to perform this attack. When the ARP cache poisoning plugin is enabled in ettercap, it sends fake ARP messages to the hosts on the local network, which causes them to update their ARP cache with a fake MAC address for a particular IP address. This allows the attacker to intercept network traffic between two hosts on the local network by redirecting the traffic to their own machine.
For this Attack we have to consider 2 system VM

- Attacker Machine: 192.168.80.164

- Victim Machine: 192.168.80.218

By opening ettercap tool on Attacker side

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e87a1a81-be71-4fd0-bc02-c36b44e28e7a)

Add Victim Mcahine IP Address to Target T1

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/ccb021de-82c9-400e-b842-72f22b505584)

we have to find a gateway of local area network

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/76e1553b-05ee-44a2-922a-ca46d090c470)

Add default gateway to target T2

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/54d835e2-7e5c-404f-98e6-18c73d04bd79)

Start ARP Poisoning

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e7199888-83e4-44bc-8ae4-ad2778766d48)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/f6dcaefb-0763-4269-a3ff-b7afead455cb)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/1a76acc5-cb36-421c-922e-3b29c4d34808)

Attack ARP Cache Poisoning is successfull and we can get to know what ever victim add as username and password in unsecured website.

## 2. Performing DOS Attack using ARP Cache Poisoning

### What is DOS Attack?

>> The DoS (Denial of Service) attack plugin in ettercap is used to flood a target system or network with an overwhelming amount of traffic to disrupt the normal functioning of the system or network. The purpose of this attack is to make the target system or network unavailable to legitimate users. The DoS attack plugin in ettercap works by generating a large amount of network traffic towards the target. The legitimate traffic may include HTTP requests, DNS queries, or other network requests.

As like the previous attack,we have to repeat steps

- Scan for hosts
- Add hosts as target (only the target ip & not the gateway ip)
- Start arp poisoning the victim.
- Then search for dos_attack plugin and start it

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4a6e7159-901f-4c4f-b421-cabf39953af8)

It will ask for Victim's IP Address 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/efe79c85-7a4e-44a4-a661-a282ed3308a7)

It will also ask for any unused IP Address

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7be04922-5053-4b9b-a46c-cc4e641c1731)

Start Attack for DOS Attack using ARP Cache Poisoning

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/dffda618-5361-42c0-ac37-363f2aee4180)

Once we activate the plugin , the target(attacker) ip sends hundreads of packets to victim, causing the victim's port will have a bottle neck situation which leads to delay. So any web search made by victim just keeps on loading.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/18891b8a-05ad-4b8b-a4a8-112ad28a9a01)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4d9b0bf2-400e-44e3-8392-310b6ead56a7)

## 3. Perform DNS Spoofing attack using ARP Cache Poisoning attacks

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b5d337eb-911d-4a2a-8bd7-a9a9e54bbd34)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/90514ca5-600a-4bf8-862c-a253f9868d1e)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d9e3f3f4-c1d8-4ec2-b0a8-d77b68bd3bb3)

Create a login html file
and start apache service

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0f03d88f-8579-4745-b9bc-01b8ba6f9f86)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7384c91a-2fb1-41a7-8782-d841f38d7b09)


![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e7275ef6-6de8-4096-8ffc-1a3114d103a6)


In Victim, On by specifying www.amrita.edu we get our debian page 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4590da38-2925-4e68-b042-d3df0c8ab998)

our login page also we can open
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7081e689-7b89-4f5a-9285-db6969a0fd50)

Ettercap shows 
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/a75bfe87-f97d-4714-aa67-25f28384c737)
