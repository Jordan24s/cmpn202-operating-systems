<img width="2362" height="931" alt="image" src="https://github.com/user-attachments/assets/62957ec0-cd46-4624-a717-882b6967cbf6" /><img width="2651" height="735" alt="image" src="https://github.com/user-attachments/assets/8b11e68f-fc45-4bd6-a1ee-a9d473a3c456" /># Week 4 – Performance Monitoring and Stress Testing
## Tools Used

The following tools were used to monitor and test system performance:

top – real-time CPU and memory monitoring

stress – CPU stress testing

iperf3 – network performance testing

## System Monitoring
The `top` command was used to observe system performance under normal conditions.
At this stage, no stress-testing tools were running.

The output shows:
- Low CPU usage
- Normal memory consumption
- No abnormal or resource-intensive processes

This baseline is used for comparison with later stress-testing results.
<img width="2875" height="1048" alt="image" src="https://github.com/user-attachments/assets/7d0a01d2-f549-4168-906b-88d154edfbfb" />

## Installing Performance Tools

The required tools were installed using the system package manager.

Command used:

sudo apt update
sudo apt install stress iperf3 -y
<img width="2646" height="474" alt="image" src="https://github.com/user-attachments/assets/b70850d9-5b9a-40eb-8635-96c3b8d8f38f" />
<img width="2891" height="954" alt="image" src="https://github.com/user-attachments/assets/f4f1663e-7fc6-4a4b-99ad-948bcbd5fba2" />
<img width="2907" height="752" alt="image" src="https://github.com/user-attachments/assets/4170b856-a71b-4375-8faa-b529f8ad5119" />
<img width="2651" height="735" alt="image" src="https://github.com/user-attachments/assets/4d75145f-baef-46f7-b874-cc0a5c7f2f6d" />


## CPU Stress Test
The stress tool was used to generate CPU load and observe system behavior under stress.

Command used:
stress --cpu 2 --timeout 30

During the test, CPU usage increased significantly, confirming that the stress tool successfully generated a CPU-intensive workload.
<img width="3001" height="1266" alt="image" src="https://github.com/user-attachments/assets/eb2d70cc-e925-4617-9f51-3ae79ee46486" />
<img width="2362" height="931" alt="image" src="https://github.com/user-attachments/assets/066219ab-5e42-4644-b57e-ed358578d77a" />
The stress tool was used to generate CPU load using two CPU workers for 30 seconds.
During the test, CPU usage increased significantly as observed in the `top` output.
After the test completed, CPU usage returned to normal levels.


