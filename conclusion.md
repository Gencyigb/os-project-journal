# 🧾 Conclusion – Final Evaluation of System Security and Performance

This project involved the full lifecycle of configuring, securing, monitoring, and evaluating a Linux server environment using command-line administration. Across seven weeks, the system evolved from a basic Ubuntu Server installation into a hardened and well-monitored environment capable of sustaining performance workloads while maintaining a strong security posture. The following conclusion summarises the key achievements and the overall effectiveness of the configuration.

---

## Security Posture Evaluation

The implemented security controls collectively formed a robust and layered defence. SSH hardening ensured that only authorised users could access the system using key-based authentication. The firewall restricted inbound traffic to a single trusted source, aligning with the principle of minimal exposure. AppArmor provided mandatory access control by confining services and reducing the impact of potential compromise. Automatic security updates ensured timely patching, while fail2ban added active intrusion prevention against repeated login attempts.

The verification script reinforced system integrity by providing consistent audit checks. These combined measures demonstrated strong alignment with security best practices and supported a defence-in-depth approach suitable for a production environment.

---

## Performance Behaviour Under Workload

Performance testing in Week 6 showed that the system responded predictably under stress. CPU workloads produced expected utilisation patterns, memory tests demonstrated stable handling of allocation and release, disk I/O behaved consistently with the server’s virtualised environment, and network throughput remained stable across repeated iperf3 tests.

Importantly, the applied security controls did not introduce any significant performance degradation. AppArmor and fail2ban operated efficiently, and firewall rules imposed negligible overhead. This demonstrated that strong security can coexist with reliable performance when implemented correctly.

---

## Learning Outcomes Achieved

The project achieved the intended learning outcomes:

- **LO3 – Security Implementation & Assessment:**  
  Security measures were implemented systematically and evaluated through logs, audits, and verification scripts. The final system showed strong resistance to common attack vectors.

- **LO4 – Command-Line Proficiency:**  
  All configuration, monitoring, and testing were performed via the command line, demonstrating competence with Linux administration and scripting.

- **LO5 – Critical Evaluation:**  
  The interaction between system security and performance was analysed using quantitative metrics. This enabled a balanced evaluation of operational efficiency and protection levels.

These outcomes reflect a clear progression of technical and analytical skills across the project.

---

## Future Improvements

If this system were extended further, several enhancements could improve its resilience and observability:

- Implementing centralised log management (e.g., ELK stack)  
- Adding automated alerting for security events  
- Integrating configuration management tools such as Ansible  
- Deploying additional services to evaluate multi-process performance  
- Introducing redundancy or load-balancing configurations  

These improvements would build on the existing foundation and support more advanced operational environments.

---

## Final Summary

The system developed throughout this project demonstrates a secure, efficient, and well-documented Linux environment. Through structured weekly work, the server was transformed into a hardened platform capable of sustaining real-world performance workloads. The combination of security controls, monitoring tools, and performance evaluation provided a comprehensive understanding of system behaviour. The project successfully met its objectives and delivered a complete overview of secure Linux system administration.
