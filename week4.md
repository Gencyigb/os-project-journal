Week 4 - Initial System Configuration & Security Implementation

Week 4 focuses on applying foundational security controls to the Ubuntu Server. All configuration was performed exclusively via SSH from the iMac workstation, following the module’s requirement that the server remains headless.

This week implements SSH hardening, firewall protection, user management, and baseline validation steps.


1. Configure SSH With Key-Based Authentication

SSH keys improve security by removing password login risks and eliminating brute-force vulnerabilities.

# On workstation (iMac)

ssh-keygen -t ed25519

# Copy public key to Ubuntu Server

ssh-copy-id username@SERVER_IP

# Test login without password

ssh username@SERVER_IP

Server-side SSH configuration:

sudo nano /etc/ssh/sshd_config

The following settings were applied:
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
LogLevel VERBOSE

Then SSH was restarted:

sudo systemctl restart ssh


Screenshot:

	•	[SSH keygen output](images/week4-ssh-keygen.png)
  
	•	[SSH config file](images/week4-sshd-config.png)
  
	•	[Successful key-based login](images/week4-ssh-login.png)



 2. Configure Firewall (UFW) to Allow SSH Only From the Workstation

UFW was enabled to enforce a default-deny firewall policy.



Commands executed:

sudo ufw default deny incoming
sudo ufw default allow outgoing



# Allow SSH ONLY from workstation IP
sudo ufw allow from 192.168.1.20 to any port 22

sudo ufw enable
sudo ufw status verbose

Additional Hardening:

	•	Root login disabled in SSH (already done in section 1)
  
	•	Password policies reviewed
  
	•	Unnecessary accounts checked using:

cat /etc/passwd


Screenshot:

	•	[adduser command output](images/week4-adduser.png)
  
	•	[groups adminuser output](images/week4-groups.png)


 4. SSH Access Evidence (Connection Verification)

A successful login using the non-root user and SSH key confirms that access control is correctly configured.

Expected terminal prompt:

adminuser@hostname:~$

Additional verification:

who

last



Screenshot:

	•	[SSH login proof](images/week4-ssh-proof.png)



 5. Configuration Files (Before & After Evidence)

### Files Modified in Week 4

| File | Purpose | Change Made |
|------|---------|-------------|
| **/etc/ssh/sshd_config** | SSH security configuration | Disabled password login, disabled root login, enabled key-based authentication |
| **/etc/ufw/user.rules** | Firewall ruleset | Added allow rule for SSH only from workstation IP |
| **/etc/sudoers** (checked only) | Privilege management | Verified correct sudo permissions for admin user; no changes made |



Screenshot:

	•	[sshd_config before](images/week4-before-ssh.png)
  
	•	[sshd_config after](images/week4-after-ssh.png)

 6. Firewall Documentation (Complete Rule Set)



### UFW Rules Applied

| Rule | Description |
|------|-------------|
| deny incoming | All inbound traffic blocked by default |
| allow outgoing | All outbound traffic allowed |
| allow from 192.168.1.20 to any port 22 | Only the workstation can SSH into the server |


To display all rules:

sudo ufw status numbered

Screenshot:


	•	[UFW numbered output](images/week4-ufw-numbered.png)


 7. Remote Administration Evidence

All administrative actions in Week 4 were executed via SSH, as required.

Commands demonstrated:

ls -l

sudo apt update

sudo nano /etc/ssh/sshd_config

sudo ufw status

Screenshot:

	•	[Remote admin commands](images/week4-remote-admin.png)

 Week 4 Reflection

Week 4 was critical in transforming the server from a default installation into a secure, hardened system appropriate for real-world deployment. Implementing SSH key authentication, firewall restrictions, privilege separation, and configuration reviews significantly improved the system’s security posture.

These actions directly support:

	•	LO3: Security implementation and assessment
  
	•	LO4: CLI proficiency demonstrated through full remote management
  
	•	LO5: Understanding configuration trade-offs (e.g., stricter SSH controls vs. usability)

The secure baseline established in this week is essential for the additional hardening and monitoring introduced in Week 5.













