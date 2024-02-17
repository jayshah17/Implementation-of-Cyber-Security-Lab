## 1. Perform ICMP Redirect 

### What is ICMP Redirect? 

>> ICMP Redirect is a message that a router sends to a computer on a network, telling it to use a different route for sending packets to a specific destination. It's like getting a suggestion from a router saying, "Hey, instead of going through me to reach that place, go directly to this other router; it's faster."

- Attacker's IP Address: 192.168.80.218
- Gateway IP Address: 192.168.80.207
- Victim's IP Address: 192.168.80.164

- Add Target T1 is Victim ip Address and Add Target T2 is Gateway ip Address

Start ARP Cache Poisoning First.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d91a5f87-17da-4295-8554-af38f148ea6d)

then start ICMP Redirect as it 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/9e18b5b3-a6f8-4ba0-9720-823298a57778)

 Add Gateway IP Address and MAC Address

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e3e198d0-e392-4612-89b8-9e5dfe2d62a3)

Simultaneously we need to start wireshark for capturing traffic analysis.
Here we can see the ICMP Redirect Messages in Wireshark.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7e4e5c4d-67c6-4a86-ab6d-357617f80468)

### 2. Performing DNS Spoofing Attack using ICMP Redirect 

This manipulation of the DNS response allows the attacker to redirect the victim's traffic to any website or web page of their choice. Once the victim's traffic is redirected to the attacker's website, the attacker can then perform various malicious activities

As like the previous attack,we have to repeat steps

- Scan for hosts
- Add hosts as target (only the target ip & not the gateway ip)
- Start arp_poisoning the victim.
- Start ICMP_Redirect Messag
- Then search for dns_attack plugin and start it
  
Open the ettercap config file which is located at /etc/ettercap/etter.conf

Change the following values to 0

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/c402efa0-d913-4213-9989-ac2f4ec7d0a9)

Uncomment the following lines in the same file

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/3d7d4086-7dbe-46b6-a08a-9b5c43fae33c)

Open the etter.dns file which is located at /etc/ettercap/etter.dns.

>> etter.dns file is the hosts file and is responsible for redirecting specific DNS requests. Basically, if the target enters facebook.com they will be redirected to Facebook's website, but this file can change

- Add line www.amrita.edu A 192.168.80.164 where 192.168.80.164 is the attacker ip

We setup a fake login page . Start the apache2 server
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/d9395fa5-142f-4cc3-99ae-13a65284131d)

Activate the `dns_spoof` plugin by going to plugins -> manage plugins

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/5cb9b7c1-ef4e-42f7-a8a4-5712a0c80f48)

As soon as we start dns_spoof, it will show that the website is spoofed to attacker IP Address.Here its showing like www.amrita.edu is spoofed to `192.168.80.164`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/f343d3f7-c8ab-44b5-a88a-90c9c4c247df)

So In Real Life Scenario, If Victim will search a particular website then it will show a spoofed website which is kept by Attacker
Attack is Successfull as spoofed website is visible  

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/11c18b81-59eb-44ff-8547-b08f11bd354a)

## 3. Performing Dos Spoofing using ICMP redirect 

### Concept of DOS Attack

>> The DoS (Denial of Service) attack plugin in ettercap is used to flood a target system or network with an overwhelming amount of traffic to disrupt the normal functioning of the system or network. The purpose of this attack is to make the target system or network unavailable to legitimate users. The DoS attack plugin in ettercap works by generating a large amount of network traffic towards the target. The legitimate traffic may include HTTP requests, DNS queries, or other network requests.

As like the previous attack,we have to repeat steps

- Scan for hosts
- Add hosts as target (only the target ip & not the gateway ip)
- Start arp_poisoning the victim.
- Start ICMP_Redirect Message.
- Then search for `dos_attack` plugin and start it

  ![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/06dc37ac-4155-4a9a-9659-03ef158d38b3)

It will ask to insert Victim IP Address

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0e84f25c-bcf1-4d4d-a46a-725f8d388b52)

It will also ask for any unused IP Address

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/274e2eb9-cd93-4ea3-a4fb-a687249049b6)

Start dos_attack extension, then we can see that packets are also redirected and www.amrita.edu website will not be loaded.

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/fa2de79e-d912-4cfe-8afc-1a752f55dc21)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/9807a8f5-c083-463e-9dcd-d4e4a70d1c9d)

Attack got successfull as wesites are taking more amount of time to load.


