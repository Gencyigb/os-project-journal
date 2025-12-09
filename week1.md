Week 1 – System Planning & Distribution Selection

Week 1 establishes the foundation for the entire project. This includes designing the system architecture, choosing an appropriate Linux distribution, configuring the workstation, documenting network settings, and capturing baseline system information using the command line.


1. System Architecture Diagram

The project uses a dual-system architecture where the Linux server is administered remotely from a workstation.


|                     Workstation System                   |
|                    (iMac – macOS Terminal)               |
|----------------------------------------------------------|
| • Used for remote administration                         |
| • Runs SSH client and monitoring scripts                 |
| • Stores project documentation and evidence              |
+----------------------- SSH over LAN ---------------------+

                           

|                Server System (Ubuntu Server VM)          |
|----------------------------------------------------------|
| • Headless Ubuntu Server (no GUI)                        |
| • All administration performed via SSH                   |
| • Runs workloads, services, security tools and tests     |




	•	![VirtualBox VM screenshot](images/week1-vm.png)
  
	•	![Ubuntu Server console](images/week1-console.png)


2. Distribution Selection & Justification

I selected Ubuntu Server (LTS) as the operating system for this project.

Reasons for choosing Ubuntu Server:

	•	Stable and widely used in real-world server environments
  
	•	Long-Term Support (LTS) provides predictable updates and security patches
  
	•	Strong community support and extensive documentation
  
	•	Simple package management with apt
  
	•	Excellent compatibility with required tools such as:
  
	•	UFW firewall
  
	•	AppArmor security modules
  
	•	Fail2ban

	•	Lynis auditing
  
	•	stress-ng, fio, iperf3, nginx


### Alternatives Considered and Rejected

| Distribution | Advantages | Reason Rejected |
|-------------|------------|-----------------|
| **Debian** | Very stable, minimal, reliable | Older package versions; less up-to-date software compared to Ubuntu Server |
| **Rocky Linux / CentOS** | Enterprise-style environment, commonly used in servers | Uses RPM/YUM ecosystem which adds complexity for this coursework |
| **Fedora Server** | Cutting-edge features, modern tooling | Short support cycle; updates too frequent for a stable coursework environment |


Conclusion:
Ubuntu Server offers the best balance of stability, simplicity, modern tools, and professional relevance.

Workstation Configuration: iMac (macOS)

The workstation used throughout this project is an Apple iMac running macOS.

Reasons for choosing macOS as the workstation:

	•	Built-in Terminal application with full OpenSSH client
  
	•	No extra installation needed for remote access
  
	•	Stable environment for scripting, monitoring, and documentation
  
	•	Mirrors realistic system administration workflows
  
	•	Supports file management and screenshot capture for evidence


![macOS Terminal ready for SSH](images/week1-terminal.png)


 4. Network Configuration Documentation

The Ubuntu Server VM is hosted inside VirtualBox, configured in Bridged Adapter mode.

This ensures that the VM receives its own IP address on the same local network as the workstation.

### Example Network Setup

| Device               | Example IP Address | Purpose                         |
|----------------------|--------------------|---------------------------------|
| **iMac Workstation** | 192.168.1.20       | Used for SSH access to server   |
| **Ubuntu Server VM** | 192.168.1.50       | Target system for configuration |
| **Router / Gateway** | 192.168.1.1        | Default network gateway         |


Why Bridged Adapter is used:
	•	Allows direct SSH access between the workstation and the VM
	•	Simulates a realistic server environment on a local network
	•	Necessary for performance tests (e.g., iperf3 network throughput)


	•	![VirtualBox network configuration](images/week1-network-settings.png)
	•	![ip addr output showing server IP](images/week1-ip-addr.png)



5. Baseline System Specification (CLI Documentation)

To capture the initial system state, I used several key Linux commands.
These provide baseline information for later performance and security comparisons.

uname -a
free -h
df -h
ip addr
lsb_release -a

What each command reveals:
	•	uname -a
Shows kernel version, architecture, and system build. Useful for confirming system environment.
	•	free -h
Displays memory usage in human-readable format. Helps establish baseline RAM availability.
	•	df -h
Provides disk usage and capacity. Useful for checking available space before installing workloads.
	•	ip addr
Shows network interfaces and assigned IPs. Used to confirm correct network configuration.
	•	lsb_release -a
Displays the exact Linux distribution version (e.g., Ubuntu 22.04 LTS).


	•	![uname output](images/week1-uname.png)
	•	![free output](images/week1-free.png)
	•	![df output](images/week1-df.png)
	•	![lsb_release output](images/week1-lsb-release.png)



6. Week 1 Reflection

Week 1 established the technical foundation for the entire coursework. I designed a realistic server–workstation architecture and justified the operating system choice based on stability, security, and real-world relevance. Documenting baseline system information ensures I have reference data to compare against future changes in performance and configuration.

This week also introduced the importance of remote management, network planning, and clear documentation, which directly support later learning outcomes involving security assessment, CLI proficiency, and critical system evaluation.


  
