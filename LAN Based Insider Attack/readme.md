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

### How does DNS Spoofing 

>> When the DNS spoofing plugin is enabled in ettercap, it intercepts DNS queries from the victim and responds with a fake DNS response that contains a fake IP address. This fake IP address is the IP address of the attacker's machine or any other IP address that the attacker wants the victim to visit. The ettercap DNS spoofing plugin listens for DNS requests made by the victim. Once a request is captured, the plugin sends a fake DNS response to the victim's machine, which contains the IP address of the attacker's machine or any other IP address specified by the attacker.

This manipulation of the DNS response allows the attacker to redirect the victim's traffic to any website or web page of their choice. Once the victim's traffic is redirected to the attacker's website, the attacker can then perform various malicious activities

As like the previous attack,we have to repeat steps

- Scan for hosts
- Add hosts as target (only the target ip & not the gateway ip)
- Start arp poisoning the victim.
- Then search for dns_attack plugin and start it

Open the ettercap config file which is located at /etc/ettercap/etter.conf

Change the following values to 0

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b5d337eb-911d-4a2a-8bd7-a9a9e54bbd34)

Uncomment the following lines in the same file

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/90514ca5-600a-4bf8-862c-a253f9868d1e)

Open the etter.dns file which is located at `/etc/ettercap/etter.dns`.

>> etter.dns file is the hosts file and is responsible for redirecting specific DNS requests. Basically, if the target enters facebook.com they will be redirected to Facebook's website, but this file can change

Add line www.amrita.edu A 192.168.80.164  where 192.168.80.164 is the attacker ip

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d9e3f3f4-c1d8-4ec2-b0a8-d77b68bd3bb3)

In a real life scenario, an attacker would use this attack to redirect traffic to their own machine for data sniffing. This is done by starting an Apache server on the Kali machine and changing the default homepage to a clone of, let's say facebook.com so that when the victim visits those websites, after being redirected to the attacker machine they will see the clones of the aforementioned sites. This will probably fool the unsuspecting user into entering their credentials where they really shouldn't.

We setup a fake login page . Start the apache2 server

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0f03d88f-8579-4745-b9bc-01b8ba6f9f86)

Activate the `dns_spoof` plugin by going to plugins -> manage plugins

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7384c91a-2fb1-41a7-8782-d841f38d7b09)


![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e7275ef6-6de8-4096-8ffc-1a3114d103a6)


In Victim, On by specifying www.amrita.edu we get our debian page.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4590da38-2925-4e68-b042-d3df0c8ab998)

Our login page also we can open
 
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7081e689-7b89-4f5a-9285-db6969a0fd50)

Ettercap shows 
 
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/a75bfe87-f97d-4714-aa67-25f28384c737)
