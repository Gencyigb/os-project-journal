# 🛡️ Week 4 – Initial System Configuration & Security Implementation

Week 4 focused on applying the core security foundations required to protect the server. This included configuring SSH securely, enforcing firewall restrictions, establishing controlled user privileges, and validating secure remote access. These actions formed the baseline security posture on which later hardening and monitoring were built.

---

## Secure SSH Configuration

SSH was configured to ensure authenticated, encrypted, and restricted remote access. Key-based authentication was enabled, password login was disabled, and root login was prevented to reduce attack surface. The SSH configuration file was reviewed and updated accordingly.

```bash
sudo nano /etc/ssh/sshd_config
```

Key configuration rules:

```text
PermitRootLogin no
PasswordAuthentication no
PubkeyAuthentication yes
LogLevel VERBOSE
```

Following these changes, the SSH service was reloaded.

```bash
sudo systemctl restart ssh
```

![SSH config screenshot](images/week4-ssh-config.png)

---

## Firewall Configuration (UFW)

A restrictive firewall policy was applied to ensure that only essential connections reached the server. Incoming traffic was denied by default, and SSH access was limited to the workstation’s IP address to prevent unauthorised access attempts.

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow from 192.168.1.20 to any port 22
sudo ufw enable
sudo ufw status verbose
```

![Firewall configuration](images/week4-ufw-status.png)

---

## User and Privilege Management

A dedicated administrative account was created to avoid using the root account for routine tasks. This account was granted appropriate privileges through group membership, supporting least-privilege principles.

```bash
sudo adduser adminuser
sudo usermod -aG sudo adminuser
groups adminuser
```

![User creation screenshot](images/week4-user-management.png)

This ensured that administrative actions were traceable and isolated from the root account.

---

## Verification of Secure SSH Access

Secure access to the server was validated by connecting from the workstation using SSH keys. The login banner and prompt confirmed that the correct non-root user was authenticated.

```bash
ssh adminuser@SERVER_IP
who
last
```

![SSH login verification](images/week4-ssh-login.png)

This confirmed that remote management was functional while preserving security restrictions.

---

## Firewall Rule Review

The active firewall rules were reviewed to ensure that no unnecessary services were exposed externally. UFW’s numbered rule list helped validate that the workstation-specific SSH rule was in place.

```bash
sudo ufw status numbered
```

![UFW numbered rules](images/week4-ufw-numbered.png)

---

## Configuration File Documentation

Several configuration files were modified or reviewed during this week to implement security controls. Documenting these ensured clarity and supported later audit work.

```markdown
| File                   | Purpose                              | Summary of Change                                     |
|------------------------|---------------------------------------|--------------------------------------------------------|
| **/etc/ssh/sshd_config** | SSH security configuration            | Disabled password login, root login; enabled key auth |
| **/etc/ufw/user.rules**   | Firewall rule definitions            | Restricted SSH access to workstation IP               |
| **/etc/sudoers** (reviewed) | Privilege management               | Confirmed correct sudo permissions                    |
```

![Config file review](images/week4-config-review.png)

---

## Reflection

Week 4 established a secure, well-structured server environment capable of supporting further hardening and performance analysis. SSH hardening prevented unauthorised access, the firewall restricted network exposure, and controlled user privileges reinforced the principle of least privilege. These steps built the foundation for the more advanced security and monitoring measures introduced in Week 5 and contributed directly to developing secure administration practices and command-line proficiency.
