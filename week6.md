Week 6 – Performance Testing and Optimisation
1. System Resource Monitoring

System resource monitoring was performed to observe CPU, memory, and disk utilisation under normal operating conditions. The top, free -h, and df -h commands were used to gather real-time system statistics.

The output showed low CPU usage with the majority of CPU time spent idle, indicating minimal background load. Memory usage was also low, with most RAM available and minimal swap usage. Disk usage indicated that the root filesystem had sufficient free space, although the mounted Windows drive (/mnt/c) showed high utilisation, which is expected in a WSL environment.

These results confirmed that the system was operating efficiently before stress testing.

 <img width="2529" height="2435" alt="image" src="https://github.com/user-attachments/assets/3f36ccf6-bef6-4a48-a4e3-46b907b212d0" />

Insert screenshot showing top, free -h, and df -h output

2. CPU Stress Testing

CPU performance was evaluated using the stress utility. The tool was configured to generate load across two CPU workers for a duration of 60 seconds.

The stress test completed successfully, indicating that the CPU was able to handle increased load without errors or instability. This confirmed that the system can sustain short periods of high CPU usage.

 <img width="3985" height="535" alt="image" src="https://github.com/user-attachments/assets/65d4d61f-4493-4e40-bd46-fcf2b3a4706e" />

Insert screenshot showing stress --cpu 2 --timeout 60 running and completing successfully

3. Memory Usage Verification

After CPU stress testing, memory usage was checked again using the free -h command. The output showed that memory consumption remained stable, with the majority of RAM still available and swap usage unchanged.

This demonstrated that the stress test did not cause memory exhaustion or abnormal memory behaviour.

 <img width="3857" height="560" alt="image" src="https://github.com/user-attachments/assets/edcee163-3e02-4691-90a8-d3d895932d70" />

Insert screenshot showing free -h output

4. Disk Performance Testing

Disk performance was tested using the dd command to write a 1GB file directly to disk. This simulated a high-throughput disk write operation.

The test completed quickly with a high write speed, indicating good disk I/O performance. No errors were encountered during the operation.

<img width="3788" height="549" alt="image" src="https://github.com/user-attachments/assets/7c390444-d577-4cd6-a268-af22d0cbb9a5" />

Insert screenshot showing dd if=/dev/zero of=testfile bs=1G count=1 oflag=direct output

5. Network Connectivity Testing

Network testing was attempted using the ping command with a placeholder hostname (server_ip). This resulted in a temporary failure in name resolution, indicating that the hostname was not valid or resolvable.

This outcome demonstrates correct system behaviour when invalid network targets are used and highlights the importance of proper DNS configuration.

 <img width="3303" height="346" alt="image" src="https://github.com/user-attachments/assets/01e62ee3-6fc1-40a2-b234-446f57406143" />

Insert screenshot showing ping -c 10 server_ip failure

6. Performance Summary

Overall system performance during testing remained stable. CPU load was handled efficiently, memory usage remained within acceptable limits, and disk write performance was strong. Network testing behaved as expected given the invalid hostname.

These results indicate that the system is well configured for typical workloads.

7. System Optimisation

To improve system efficiency, unnecessary background services were reviewed. The snapd service was disabled to reduce background resource usage.

Although the main snapd.service was disabled successfully, its socket trigger remained active. This behaviour is expected in systemd-managed systems and does not negatively impact performance.

Disabling unused services helps reduce system overhead and improves responsiveness.


<img width="3758" height="679" alt="image" src="https://github.com/user-attachments/assets/859bc8cf-5193-456d-b229-61637a787416" />

Insert screenshot showing sudo systemctl disable snapd output

8. Issues Encountered and Limitations

During the performance testing and optimisation tasks, several minor issues and limitations were encountered.

One limitation occurred during network testing when attempting to use a placeholder hostname (server_ip) with the ping command. This resulted in a temporary DNS resolution failure. This issue was expected and highlights the importance of using valid hostnames or IP addresses when conducting network diagnostics.

Another limitation was related to service management. While the snapd service was successfully disabled, the associated snapd.socket trigger remained active. This behaviour is expected within systemd-based systems, as socket activation can automatically restart services when required.

Additionally, stress testing was performed for a limited duration to avoid unnecessary strain on the system. Long-term performance impacts under sustained load were therefore not assessed.

9. Conclusion

This week focused on evaluating and optimising system performance through practical testing and service management. CPU, memory, disk, and network performance were successfully assessed using standard Linux utilities.

The system demonstrated stable behaviour under stress conditions, maintained low memory usage, and achieved high disk write speeds. Network testing confirmed correct error handling, and system optimisation was improved by disabling unnecessary background services.

Overall, these tasks strengthened practical skills in performance monitoring, benchmarking, and system optimisation, contributing to a more efficient and reliable operating system environment.
