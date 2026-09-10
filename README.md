# Enterprise Blue Team & Security Operations Lab

Hands-on defensive security work covering network hardening, IDS/IPS, centralized logging, incident handling, and security automation.

> **Academic context:** Completed as part of Computer Science / Cybersecurity engineering coursework at Amar Telidji University, Laghouat (2025-2026). This repository is intended as a technical portfolio of controlled university lab work.

## What this repository demonstrates

- Built a layered firewall/security gateway with OPNsense, Suricata IDS/IPS, Zenarmor, and ClamAV.
- Centralized Windows logs and investigated authentication and privilege-related events in the ELK Stack.
- Practiced incident case management with TheHive and modeled observable enrichment/analysis with Shuffle and Cortex.
- Hardened a Linux server with SSH keys, least privilege, ACLs, password policies, UFW, Fail2Ban, logging, and Lynis auditing.

## Tools & technologies

`OPNsense` · `Suricata` · `Zenarmor` · `ClamAV` · `ELK Stack` · `NXLog` · `TheHive` · `Shuffle` · `Cortex` · `Nmap` · `UFW` · `Fail2Ban` · `Lynis` · `Linux`

## Included lab reports

| # | Lab | Report |
|---:|---|---|
| 1 | Enterprise Blue Team Security Operations | [`docs/enterprise-blue-team-security-operations.md`](docs/enterprise-blue-team-security-operations.md) |
| 2 | Secure System Hardening And Auditing | [`docs/secure-system-hardening-and-auditing.md`](docs/secure-system-hardening-and-auditing.md) |

## Repository structure

```text
.
├── README.md
├── docs/        # GitHub text editions of the academic lab reports
└── src/         # Add original code/configs/scripts here when available
```

## Notes

The reports document the work actually completed in the university labs. For GitHub portability, the reports are included as searchable Markdown text editions; the original PDF screenshots and figures are not embedded in these conversions. The `src/` directory is intentionally left as a place to add original source code, configuration files, packet captures, notebooks, or scripts where those artifacts are available. No source code has been fabricated from the reports.

## Responsible use

Security techniques in this repository were performed in controlled academic environments. Use attack and exploitation techniques only on systems you own or have explicit authorization to test.
