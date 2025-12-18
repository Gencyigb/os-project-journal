# 📘 Week 1 – System Planning & Distribution Selection

Week 1 focused on designing the system architecture, selecting a suitable Linux distribution, configuring the workstation environment, documenting network settings, and collecting baseline system information. These activities established the foundation for all later configuration, security, and performance work.

---

## System Architecture Overview

The project uses a two-system architecture consisting of a workstation (iMac) and a headless Ubuntu Server virtual machine. All administration is performed remotely through SSH, reflecting realistic server management practice.

```text
+------------------------------+            +------------------------------+
|      Workstation System      |  SSH over  |         Server System        |
|        (iMac – macOS)        | <--------> |     Ubuntu Server (VM)       |
| - Terminal for SSH access    |   LAN      | - Headless configuration     |
| - Monitoring and scripts     |            | - Workload & security tools  |
+------------------------------+            +------------------------------+
```


---

## Distribution Selection

Ubuntu Server (LTS) was selected as the operating system for its stability, long-term support, extensive documentation, and compatibility with the security and performance tools used later in the project.

### Alternatives Considered

```markdown
| Distribution | Advantages | Reason Rejected |
|-------------|------------|-----------------|
| **Debian** | Stable, minimal environment | Older package versions and slower release cycle |
| **Rocky / CentOS** | Enterprise-grade environment | RPM/YUM ecosystem adds unnecessary complexity |
| **Fedora Server** | Modern, frequent updates | Short support cycle unsuitable for this project |
```

Ubuntu Server provided the best balance of security, maintainability, and tool support.

---

## Workstation Configuration

The workstation for this project is an iMac running macOS. It provided:

- A built-in SSH client  
- Reliable terminal environment  
- Easy access to files, screenshots, and documentation  

This system acted as the administrative console throughout the project.


---

## Network Configuration

The server was configured as a VirtualBox VM using a bridged adapter, giving it a direct presence on the local network. This enabled reliable SSH access from the workstation and supported performance testing in later weeks.

### Network Setup

```markdown
| Device               | Example IP Address | Purpose                         |
|----------------------|--------------------|---------------------------------|
| **iMac Workstation** | 192.168.1.20       | Remote SSH access               |
| **Ubuntu Server VM** | 192.168.1.50       | Target system for configuration |
| **Router / Gateway** | 192.168.1.1        | Network gateway                 |
```

Network validation:

```bash
ip addr
ping 192.168.1.50
```



---

## Baseline System Information

Baseline information was collected to document system specifications prior to applying configuration and security controls. These values provide reference points for future performance comparisons.

```bash
uname -a
free -h
df -h
ip addr
lsb_release -a
```



---

## Reflection

Week 1 established the structural foundation for the entire project. Selecting Ubuntu Server ensured compatibility with forthcoming security and performance tasks, while documenting system architecture and network configuration created a clear operational framework. Collecting baseline system information provided essential reference data for later evaluation and analysis. These activities supported the development of planning, documentation, and command-line proficiency skills.
