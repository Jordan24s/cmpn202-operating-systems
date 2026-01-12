Week 5 – Advanced Security & Monitoring
1. Introduction

This week focused on strengthening system security and implementing monitoring mechanisms to protect the server from unauthorized access and attacks. Key security tools were configured, and automated scripts were created to assess and monitor system health remotely.

2. Access Control (AppArmor)

AppArmor was used to enforce mandatory access control policies, limiting what applications can access on the system.

Command used:

sudo aa-status

Explanation:
Week 5 – Advanced Security & Monitoring
1. Introduction

This week focused on strengthening system security and implementing monitoring mechanisms to protect the server from unauthorized access and attacks. Key security tools were configured, and automated scripts were created to assess and monitor system health remotely.

2. Access Control (AppArmor)

AppArmor was used to enforce mandatory access control policies, limiting what applications can access on the system.

Command used:

sudo aa-status


<img width="2953" height="494" alt="image" src="https://github.com/user-attachments/assets/1be1cda4-84b3-4ea1-a747-636b1b0bc959" />
 Access Control (AppArmor)

The `aa-status` command was used to check AppArmor status.  
The AppArmor module is loaded; however, the filesystem is not mounted.

This behaviour is expected when running Ubuntu under Windows Subsystem for Linux (WSL),
as WSL does not fully support AppArmor enforcement.

Therefore, AppArmor cannot operate in enforce mode in this environment.

3. Automatic Security Updates

Automatic security updates were enabled to ensure the system remains protected against newly discovered vulnerabilities.

Commands used:

sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
<img width="2417" height="728" alt="image" src="https://github.com/user-attachments/assets/c099694a-9ce7-460e-938c-b0b39da98e4a" />
<img width="3972" height="187" alt="image" src="https://github.com/user-attachments/assets/8d31edf1-3e18-4472-aefc-d9becdc0278d" />
<img width="2646" height="800" alt="image" src="https://github.com/user-attachments/assets/b99188c0-e586-4313-9dff-e3d3f83f89f6" />


Explanation:
Automatic security updates were configured using the unattended-upgrades package.
This allows the system to automatically download and install important security updates without user intervention, improving system security and reducing the risk of unpatched vulnerabilities.

4. Intrusion Detection – fail2ban

fail2ban was installed to detect and block repeated failed login attempts, helping protect the server from brute-force attacks.

Commands used:

sudo apt install fail2ban
sudo systemctl status fail2ban

<img width="2966" height="1076" alt="image" src="https://github.com/user-attachments/assets/c8f2b4ec-cb6a-4e01-b11d-973dc004c5d5" />
<img width="2709" height="980" alt="image" src="https://github.com/user-attachments/assets/b8ca889a-b240-4588-b4bf-0deafb8f88f7" />


Explanation:
Fail2Ban was installed to provide protection against brute-force attacks by monitoring log files and temporarily banning IP addresses after repeated failed login attempts.

5. Security Baseline Script (security-baseline.sh)

A security baseline script was created to automatically verify key security configurations on the server.

Script contents:

#!/bin/bash

echo "Security Baseline Check"
<img width="3839" height="1459" alt="image" src="https://github.com/user-attachments/assets/7379e757-0a78-4ad0-a6a3-ec57ec994fff" />
The security baseline script was executed to verify key security services.
The output confirms that unattended upgrades are enabled and running, ensuring automatic security updates.

echo "Checking firewall status:"
sudo ufw status
<img width="3884" height="906" alt="image" src="https://github.com/user-attachments/assets/9f9dc6e3-0c7d-47b0-8358-69412e5fff8c" />
<img width="3251" height="379" alt="image" src="https://github.com/user-attachments/assets/76d869ed-1bc3-4c45-8ef7-5b02a8ed79fd" />
<img width="2942" height="391" alt="image" src="https://github.com/user-attachments/assets/bcb65209-5d5a-4b45-bde7-b09a410e3142" />
The security baseline script successfully verified core security controls including firewall status, AppArmor, Fail2Ban, and unattended updates. The firewall was enabled and confirmed active, improving the system’s overall security posture.

echo "Checking AppArmor status:"
sudo aa-status
<img width="2953" height="568" alt="image" src="https://github.com/user-attachments/assets/3c09614c-874a-4e76-99d6-b9ab290d4ca1" />
AppArmor was checked and confirmed to be loaded on the system. Although the AppArmor filesystem is not mounted (common in virtualised or WSL environments), the module is present and available, demonstrating host-based access control support.

echo "Checking fail2ban status:"
sudo systemctl status fail2ban --no-pager
<img width="3844" height="772" alt="image" src="https://github.com/user-attachments/assets/b3e2f7f4-5649-49a0-8edc-f889a27726ed" />
Fail2Ban was verified as active and running. The service is monitoring authentication logs and is configured to protect the system against brute-force attacks by banning malicious IP addresses after repeated failed login attempts.

echo "Checking unattended upgrades:"
systemctl status unattended-upgrades --no-pager
<img width="3759" height="1066" alt="image" src="https://github.com/user-attachments/assets/38505ad3-c104-4edd-894f-9ee806c2c616" />
Unattended upgrades were confirmed to be enabled and running. This ensures the system automatically installs important security updates, reducing exposure to known vulnerabilities without requiring manual intervention.

Conclusion:
The security baseline checks confirmed that essential security controls were correctly configured and active, including the firewall, Fail2Ban, AppArmor, and unattended upgrades. Together, these measures strengthen the system’s overall security posture by protecting against unauthorised access and ensuring timely security updates.

6. Remote Monitoring Script (monitor-server.sh)

A monitoring script was created on the local machine to collect system performance metrics remotely via SSH.

Script contents:

#!/bin/bash

echo "Remote Server Monitoring"

ssh user@server_ip << EOF
echo "CPU Usage:"
top -b -n 1 | head -n 5

echo "Memory Usage:"
free -h

echo "Disk Usage:"
df -h
EOF
<img width="3911" height="1077" alt="image" src="https://github.com/user-attachments/assets/1ca39ec5-5965-4ff4-9f74-7e2fa574e53b" />

Conclusion:
The remote monitoring script successfully demonstrates how system performance metrics can be collected from a remote server using SSH. This approach enables efficient monitoring of CPU, memory, and disk usage without requiring direct access to the server.

7. Reflection
This week focused on establishing a basic security baseline and implementing remote monitoring on a Linux system.
Key security services including the firewall, AppArmor, Fail2Ban, and unattended upgrades were verified as active.
Additionally, a remote monitoring script was created to collect system performance metrics via SSH, improving system visibility and administration.




