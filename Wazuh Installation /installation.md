# Wazuh - Open Source Security Platform

We have installed an .OVA file which contains wazuh server

## Installation of Wazuh - Server

Download Ova file in host os and load it in any hypervisor manager

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/78a1fb9e-35ce-4ad4-bdcf-1e5892608a2a)

Start it with required configuration but with 2 GB RAM also it works

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/6ea3e968-b366-4600-baaa-eb6ae45b0152)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/83b84bba-9e03-4adf-bfaf-591797394fbe)

- We can verify that our Wazuh-indexer is working or not

`systemctl status wazuh-indexer`

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/5154ec2a-9619-42d0-b202-39a03228d9ec)


## Inastallation of Wazuh - Agent 
```
Ip Address of Wazuh Server - 192.168.166.57
Ip Address of Wazuh Agent - 192.168.231.128
```

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/e7633eab-7853-445a-904b-6bbae9824117)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/beb43ee7-51c6-4b9a-87df-b504769ca83c)

- In Wazuh Manager we have to add the ip of wazuh server

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/46df3a09-845f-460b-92d0-5d07df958fed)

- Start the wazuh agent in kali 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/9847df2e-e2d9-4bac-b29d-584e6d01941e)

- Status of wazuh Agent 

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/60fdd888-8e30-4506-8f34-2fc5e149dea5)

- In Wazuh Dashboard / Wazuh Manager

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/61aa4bff-2bbe-4fde-aed4-30ceaec865d8)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4b5d7034-4b66-4a6c-9760-8fef1326c737)

