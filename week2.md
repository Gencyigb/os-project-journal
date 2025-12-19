# 🔐 Week 2 – Security Planning & Testing Methodology

Week 2 focused on defining the security requirements for the server and planning the performance testing approach. This preparation ensured that the configuration and evaluation work performed in later weeks would be systematic, measurable, and aligned with best practices.

---

## Security Planning

A structured security plan was created to identify all safeguards required to protect the server. This included authentication controls, network restrictions, privilege management, intrusion detection, and system hardening mechanisms.

Key security objectives established for the system:

- Enforce key-based SSH access  
- Disable root login and password authentication  
- Restrict SSH access to a trusted workstation  
- Implement firewall rules with default-deny policies  
- Apply mandatory access control using AppArmor  
- Enable automatic security updates  
- Deploy intrusion detection with fail2ban  
- Maintain clear visibility through logs and monitoring tools  

These objectives shaped the configuration tasks implemented in Week 4 and Week 5.



---

## Threat Model

A threat model was developed to identify potential risks and document appropriate mitigation strategies. This provided a foundation for evaluating whether the selected security controls were adequate.

```markdown
| Threat ID | Description | Impact | Mitigation Strategy |
|-----------|-------------|--------|----------------------|
| **T1** | Brute-force SSH attempts | Unauthorised access | Key-based authentication, fail2ban, restricted SSH access |
| **T2** | Unnecessary open ports | Increased attack surface | Firewall hardening, service minimisation |
| **T3** | Privilege escalation | Full system compromise | Least-privilege accounts, sudo restrictions, AppArmor confinement |
| **T4** | Unpatched vulnerabilities | Remote exploitation | Automatic security updates, regular package maintenance |
| **T5** | Lack of monitoring | Undetected breaches | Security verification scripts, log reviews, remote monitoring |
```



---

## Performance Testing Strategy

A performance testing methodology was created to ensure consistent and comparable results across CPU, memory, disk, network, and service workloads. This plan defined the metrics, tools, and monitoring techniques that would be used during Week 6.

### Performance Metrics

- CPU utilisation and load averages  
- Memory consumption and swap activity  
- Disk throughput, latency, and I/O patterns  
- Network bandwidth and packet retransmissions  
- Web service responsiveness under light load  

### Tools Selected

- **stress-ng** – CPU stress generation  
- **memtester** – memory allocation testing  
- **fio** – disk performance benchmarking  
- **iperf3** – network throughput measurement  
- **nginx** – lightweight service for response testing  
- **top, vmstat, iostat, ss, free** – real-time monitoring utilities  

These tools were chosen for their reliability, command-line compatibility, and ability to generate quantifiable output.



---

## Monitoring and Measurement Approach

Monitoring was planned to occur simultaneously with workload execution to capture real-time system behaviour. This ensured that the data collected reflected accurate system responses under stress.

Monitoring commands included:

```bash
top -bn1 | head -n 5
vmstat 1 5
iostat -xz 1 5
free -h
ss -s
ping -c 5 SERVER_IP
```

These metrics would later be compared against the results recorded during Week 6.



---

## Reflection

Week 2 established the strategic direction for the project by defining security objectives, identifying realistic threat scenarios, selecting appropriate performance tools, and outlining a structured testing methodology. This planning phase ensured that later configuration, monitoring, and evaluation tasks were systematic, justified, and aligned with the module learning outcomes rather than ad hoc experimentation.

Developing a threat model at this stage helped prioritise security controls and informed decisions around access management, service exposure, and update policies in later weeks. Similarly, defining the performance evaluation approach early improved the consistency and comparability of results gathered during testing. Overall, this week highlighted the importance of upfront planning in producing rigorous, defensible system analysis.
