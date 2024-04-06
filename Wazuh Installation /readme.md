# Detecting XZ Utils Vulnerability 

### Make wazuh server configuration
```
- Enable the Vulnerability Detector module by modifying the Wazuh server configuration file at /var/ossec/etc/ossec.conf.
Set the value for the <enabled> tag to yes for the Vulnerability Detector module and for every operating system you intend to scan.
```

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/0ca72d9d-41d0-435b-b389-6a64ef35ee28)

Add Vulnerability Detector Code in config file 

```
<vulnerability-detector>
    <enabled>yes</enabled>
    <interval>5m</interval>
    <min_full_scan_interval>6h</min_full_scan_interval>
    <run_on_start>yes</run_on_start>

    <!-- Ubuntu OS vulnerabilities -->
    <provider name="canonical">
      <enabled>yes</enabled>
      <os>trusty</os>
      <os>xenial</os>
      <os>bionic</os>
      <os>focal</os>
      <os>jammy</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Debian OS vulnerabilities -->
    <provider name="debian">
      <enabled>yes</enabled>
      <os>buster</os>
      <os>bullseye</os>
      <os>bookworm</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- RedHat OS vulnerabilities -->
    <provider name="redhat">
      <enabled>yes</enabled>
      <os>5</os>
      <os>6</os>
      <os>7</os>
      <os>8</os>
      <os>9</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Amazon Linux OS vulnerabilities -->
    <provider name="alas">
      <enabled>yes</enabled>
      <os>amazon-linux</os>
      <os>amazon-linux-2</os>
      <os>amazon-linux-2022</os>
      <os>amazon-linux-2023</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- SUSE OS vulnerabilities -->
    <provider name="suse">
      <enabled>yes</enabled>
      <os>11-server</os>
      <os>11-desktop</os>
      <os>12-server</os>
      <os>12-desktop</os>
      <os>15-server</os>
      <os>15-desktop</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Arch OS vulnerabilities -->
    <provider name="arch">
      <enabled>yes</enabled>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Alma Linux OS vulnerabilities -->
    <provider name="almalinux">
      <enabled>yes</enabled>
      <os>8</os>
      <os>9</os>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Windows OS vulnerabilities -->
    <provider name="msu">
      <enabled>yes</enabled>
      <update_interval>1h</update_interval>
    </provider>

    <!-- Aggregate vulnerabilities -->
    <provider name="nvd">
      <enabled>yes</enabled>
      <update_interval>1h</update_interval>
    </provider>

  </vulnerability-detector>
```


![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/59992d3b-22d3-4c07-956e-e6c6cdfcced3)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/7358b111-1d35-49bb-9ff7-a6c9d0e41eda)


Updating Vulnerability Database to our wazuh-server like National Vulnerability Database

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/b5457dc8-d01b-4625-ae5d-f1fe257712f9)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/77b9b3f7-bc51-42a9-ad53-1d0f8a1f131e)

![image](https://github.com/jayshah17/Implementation-of-Cyber-Security-Lab/assets/76842630/4c4a05b7-8e74-4831-9a01-e8f5162aa0d8)

