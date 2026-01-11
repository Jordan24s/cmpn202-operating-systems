Week 3 – Application Selection for Performance Testing
Selected Applications

Two applications were selected to represent different system workloads:

stress – CPU-intensive workload generator

iperf3 – Network-intensive performance testing tool

These tools were chosen to demonstrate how different types of workloads affect system resources.

Installation

The applications were installed inside an Ubuntu Linux environment running under Windows Subsystem for Linux (WSL2) using the system package manager.
WSL2 allows Linux tools to run natively on Windows with minimal overhead.

Expected Resource Usage

stress is expected to significantly increase CPU usage during execution.

iperf3 is expected to increase network activity during bandwidth testing.

These tools allow observation of CPU, memory, process, and disk behaviour under load.

Reflection

Simple and lightweight tools were selected to clearly observe operating system behaviour without additional configuration complexity. Using WSL2 provided a convenient Linux environment while still running on a Windows host system.
## Evidence (Screenshots)

### Ubuntu / WSL Installation (Kernel Information)
Screenshot showing Ubuntu running inside WSL2 and Linux kernel information using `uname -a`.
<img width="3914" height="150" alt="image" src="https://github.com/user-attachments/assets/6c5eaaa1-0d7b-41a9-8e1f-afbe95da4291" />

### Linux Distribution Information
Screenshot showing the Linux distribution name, version, and codename using `lsb_release -a`.
<img width="2818" height="632" alt="image" src="https://github.com/user-attachments/assets/841280d9-f5ca-442d-992c-3eabc5b10e05" />

### Running Processes
Screenshot showing active system processes in Linux using `ps aux`.
<img width="3857" height="776" alt="image" src="https://github.com/user-attachments/assets/cfb872f6-e713-4f74-94da-88532c2cda0c" />

### Disk Usage and Mounted Filesystems
Screenshot showing disk usage and mounted filesystems using `df -h`.
<img width="3190" height="1234" alt="image" src="https://github.com/user-attachments/assets/6f001864-933c-45b8-9282-33976a8c375b" />
<img width="2332" height="1362" alt="image" src="https://github.com/user-attachments/assets/dcff3ba9-3e46-46bc-828a-1084951fff40" />

### Summary
All screenshots demonstrate a correctly configured Ubuntu Linux environment running under WSL2.  
The system shows active processes, valid disk mounts, and confirmed distribution and kernel information, indicating readiness for performance testing using CPU- and network-intensive applications.
environment running under WSL2. The system is ready for performance testing using CPU- and network-intensive applications.
