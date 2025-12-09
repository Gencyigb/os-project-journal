Week 2 – Security Planning & Testing Methodology

Week 2 focuses on planning the security controls and defining the performance testing methodology before applying any system changes. This planning ensures that all configuration and hardening decisions later in the project are structured, justified, and measurable.



1. Security Configuration Checklist

This checklist outlines the required security controls that will be implemented in Weeks 4 and 5.

SSH Security

	•	Disable password authentication
  
	•	Enforce SSH key-based login
  
	•	Disable direct root login
  
	•	Restrict SSH access to the iMac workstation’s IP
  
	•	Optionally change default SSH port for defence-in-depth

Firewall (UFW)

	•	Deny all inbound traffic by default
  
	•	Allow SSH only from trusted IP
  
	•	Log denied attempts
  
	•	Confirm firewall persists across reboots

User & Privilege Management

	•	Create non-root admin account
  
	•	Ensure correct sudo group permissions
  
	•	Disable or lock unnecessary accounts

Mandatory Access Control

	•	Enable AppArmor on the server
  
	•	Verify key services run under AppArmor profiles
  
	•	Review profiles in enforce vs complain mode

Automatic Updates

	•	Install & enable unattended security upgrades
  
	•	Confirm update logs and schedules

Network Security

	•	Identify all listening ports
  
	•	Remove or disable unnecessary services

	•	Plan later validation using nmap


[Security checklist notes](images/week2-checklist.png)



2. Performance Testing Strategy

Before implementing changes, it is important to define what will be tested and how.

Metrics to Measure

	•	CPU utilisation
  
	•	Memory consumption
  
	•	Disk read/write performance
  
	•	Network throughput
  
	•	Latency and responsiveness
  
	•	Impact of security controls on performance

Tools Planned for Use

	•	top / htop – real-time CPU and memory
  
	•	vmstat – system behaviour overview
  
	•	iostat – disk I/O activity
  
	•	df -h – disk capacity during tests
  
	•	ping – basic latency
  
	•	iperf3 – network throughput test
  
	•	stress-ng, memtester, fio, nginx – workload tools (selected in Week 3)


[performance testing notes](images/week2-performance-plan.png)



3. Threat Model (Paste-Ready Table)

Use this table directly in your GitHub Page — it is formatted for professional presentation and high marks.
