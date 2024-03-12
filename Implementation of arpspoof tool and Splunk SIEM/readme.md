# Implementation of Arpspoof tool and Splunk SIEM Tool with cracking password

## Use the arpspoof tool to perform the following attacks [10 Marks] 
  ### a. Use ARP packets to perform the DNS spoofing attack. Whatever the website the user types, it should navigate to http://testphp.vulnweb.com/login.php as a part of the attack.








  ### b. Use ICMP Packets to perform only DDOS attacks over the victim. 








## 2. Use Splunk to answer the following questions:
  ### a. Capture these above attacks using Splunk in an active or passive method. (10 Marks)











  
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









  
