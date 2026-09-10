# Secure System Hardening And Auditing

> Portfolio write-up derived from the original university lab report provided by Smail Mersad. The original report contains screenshots; this GitHub edition uses only results from that report and does not invent additional assets.

**Academic context:** Amar Telidji University, Computer Science / Cybersecurity Engineering, 2025-2026.

## Part 1 — Secure system fundamentals

### SSH key authentication

The lab began by configuring SSH public-key authentication for remote administration, reducing dependence on password-only access.

### Attack-surface review

Open services were reviewed and the host showed only SSH (`22/tcp`) as required for administration. The report notes that unnecessary services should be disabled when present.

### Least-privilege user administration

Separate `admin`, `staff1`, and `guest` users were created. `staff1` was placed in a shared `office` group and given narrowly scoped `sudo` permissions for selected commands rather than unrestricted administrative access. Tests confirmed that allowed commands worked while broader administration was denied.

### Unix permissions and ACLs

A shared directory and confidential file were protected with ownership/group configuration and `chmod 640`. ACLs were also tested to demonstrate per-user permission control beyond the normal owner/group/other model.

### Password and authentication policy

Password aging and complexity controls were configured. The report used a 90-day maximum age, a one-day minimum change interval, a seven-day warning period, and PAM password-quality rules. Weak test passwords were rejected while policy-compliant examples were accepted.

## Part 2 — Hardening and auditing

### System hardening

The server already had a minimal service footprint: attempted removal of desktop-oriented services such as CUPS and Avahi showed they were not installed. Unattended security updates were enabled and direct root login was locked so administrative activity would flow through controlled privilege escalation.

### UFW firewall

A restrictive UFW policy was configured:

- deny incoming by default;
- allow outgoing by default;
- explicitly allow SSH only.

Verification with UFW status and Nmap showed only the required SSH service reachable.

### Logging and auditing

Authentication failures were investigated through `systemd-journald` / `journalctl` because the tested system did not have a traditional `/var/log/auth.log` path populated by rsyslog.

### Fail2Ban

Fail2Ban was installed and the `sshd` jail enabled. Password authentication was temporarily re-enabled solely to generate failed-login test events. Repeated failures triggered the jail and `fail2ban-client` confirmed that the source was detected and banned.

### Lynis audit

A Lynis security audit produced a hardening score of **66** in the lab run. The report recorded recommendations including:

- enable `auditd` for richer security auditing;
- tighten SSH options such as `MaxAuthTries`, `AllowTcpForwarding`, and `X11Forwarding`;
- consider a rootkit/malware scanner as an additional hardening layer.

## Tools & technologies

`SSH` · `sudo` · Unix permissions · `ACL` · `PAM` · `chage` · `UFW` · `journalctl` · `Fail2Ban` · `Lynis` · Ubuntu Server

## Takeaway

The lab treats system security as layered configuration rather than a single tool: reduce exposed services, use stronger authentication, apply least privilege, protect files, automate patching, restrict network access, retain useful logs, automatically react to repeated authentication failures, and continuously audit the resulting system.
