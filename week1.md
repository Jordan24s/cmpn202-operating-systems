Week 1 – System Planning and Distribution Selection
1. Overview

The aim of Week 1 was to plan the operating system deployment and justify all technical decisions before implementation. This week focused on selecting an appropriate Linux server distribution, designing the system architecture, deciding on a workstation configuration, and outlining the initial network approach. Planning these elements in advance helps reduce configuration errors and ensures the system can be secured and managed effectively in later weeks.

2. System Architecture Description

The system is designed using a dual-machine architecture consisting of a workstation and a headless Linux server. The workstation is used for administration tasks, while the server hosts the operating system being configured and secured.

All administration is performed remotely using SSH from the workstation. The server runs without a graphical user interface, enforcing command-line-only management. This approach reflects real-world server administration practices and supports the learning objectives of the module.

Architecture Overview

Workstation:

SSH client

Used for remote administration and monitoring

Server:

Ubuntu Server (headless)

OpenSSH server enabled

Firewall configured to allow SSH access only

This separation improves security and encourages correct privilege management.

3. Linux Distribution Selection
Selected Distribution

Ubuntu Server 24.04 LTS

Justification

Ubuntu Server 24.04 LTS was selected due to its long-term support lifecycle, stability, and extensive documentation. As an LTS release, it receives security updates for several years, making it suitable for server environments.

Ubuntu Server provides strong community support and includes native security features such as OpenSSH, AppArmor, and compatibility with automated security updates. The default headless installation aligns with the coursework requirement for command-line-only system administration.

4. Comparison with Alternative Distributions

Several alternative Linux distributions were considered:

Debian: Very stable but often provides older package versions, which may limit access to newer features.

CentOS Stream / RHEL-based systems: Enterprise-focused but less suitable for rapid coursework setup.

Arch Linux: Highly customisable but too complex and time-consuming for this coursework.

Ubuntu Server provides the best balance between stability, usability, and learning value for this project.

5. Workstation Configuration Decision
Selected Option

Host machine as workstation

Justification

The host machine was selected as the workstation to reduce system complexity and resource usage. Using the host operating system as the administration workstation allows SSH access to the server while maintaining a clear separation between the server environment and the user environment.

This configuration reflects real-world practice where administrators manage servers remotely rather than directly accessing them.

6. Network Configuration Plan

The server will operate on a private network configuration that allows communication between the workstation and the server while limiting external exposure. SSH will be used for remote access, operating on port 22.

IP addressing will be documented once the server is running to ensure consistent and identifiable network configuration. This approach supports secure remote administration and simplifies troubleshooting.

7. Reflection

This week highlighted the importance of careful planning before system configuration begins. Selecting an appropriate operating system, defining a clear architecture, and planning the network layout provide a strong foundation for security hardening and performance evaluation in later weeks. Establishing a headless, SSH-based administration model reinforces professional operating system management practices that will be developed further throughout the coursework.
