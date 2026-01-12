Week 7 – Remote Monitoring Script
1. Script Creation

A Bash script was created to perform remote system monitoring using SSH. The script was designed to display basic performance metrics from a remote server, including CPU usage, memory usage, and disk usage.

The script begins with a shebang to specify Bash as the interpreter and prints a header message to confirm execution. It then attempts to establish an SSH connection to a remote server and run several monitoring commands.

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

<img width="3396" height="1662" alt="image" src="https://github.com/user-attachments/assets/4d8daa0e-8451-480a-bfc8-e1f11ab11543" />


(Script contents and initial execution attempt showing “Remote Server Monitoring” output)

2. Script Execution and Output

When the script was executed, the message “Remote Server Monitoring” was displayed, confirming that the script started successfully. However, the SSH connection did not complete.

The terminal output displayed the following messages:

Pseudo-terminal will not be allocated because stdin is not a terminal

ssh: Could not resolve hostname server_ip: Temporary failure in name resolution

These messages indicate that the script ran correctly but failed when attempting to connect to the remote server.

<img width="2758" height="667" alt="image" src="https://github.com/user-attachments/assets/2cf09df0-83ce-47cf-9b97-6138a39ec572" />

(Terminal output showing SSH execution attempt and hostname resolution error)

3. Analysis of SSH Error

The SSH error occurred because server_ip was used as a placeholder rather than a real hostname or IP address. As a result, the system was unable to resolve the hostname via DNS.

This issue is related to network configuration rather than a scripting error. The script logic itself was correct, but remote execution depends on valid hostnames, DNS resolution, and network connectivity.

<img width="3396" height="1662" alt="image" src="https://github.com/user-attachments/assets/a51383f2-5409-4ad2-8166-92494b88ed92" />

(Error message: “Could not resolve hostname server_ip”)

4. Automation and Security Considerations

Using SSH for remote monitoring provides a secure method of accessing and collecting system information from remote machines. SSH encrypts communication and supports authentication mechanisms such as passwords or SSH keys.

However, automation scripts rely on several external factors:

Correct hostnames or IP addresses

Proper SSH authentication

Network availability and DNS configuration

If any of these requirements are not met, scripts may fail even if they are written correctly.

<img width="3396" height="1662" alt="image" src="https://github.com/user-attachments/assets/7eeb6075-f061-4066-85a1-98027168a60d" />

(SSH-related output demonstrating failed remote connection)

5. Learning Outcome

This task demonstrated how a Bash script can be used to automate remote system monitoring tasks using SSH. It showed how multiple system performance commands can be executed remotely from a single script, improving efficiency and consistency.

The task also highlighted the importance of correct network configuration, particularly hostname resolution, when working with remote automation. Even when a script is logically correct, external factors such as DNS configuration and connectivity can prevent successful execution.

Overall, this exercise improved understanding of SSH-based automation, remote monitoring concepts, and basic troubleshooting techniques for common scripting and networking issues.
