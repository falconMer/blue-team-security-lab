# Enterprise Blue Team & Security Operations Lab

Hands-on defensive security work covering network hardening, IDS/IPS, centralized logging, incident handling, Windows telemetry, and security automation.

> **Academic context:** Computer Science / Cybersecurity engineering coursework at Amar Telidji University, Laghouat (2025-2026).

## What this repository demonstrates

- Built a layered OPNsense security gateway with Suricata IDS/IPS, Zenarmor, and ClamAV.
- Centralized system and Windows logs with the ELK Stack and investigated authentication/privilege-related events.
- Used TheHive for incident case management and modeled observable-analysis automation with Shuffle and Cortex.
- Hardened an Ubuntu server with SSH keys, least privilege, Unix permissions/ACLs, password policy, UFW, Fail2Ban, logging, and Lynis.
- Performed practical reconnaissance, password-security, encryption, steganography, and hidden-service analysis exercises.

## Tools & technologies

`OPNsense` · `Suricata` · `Zenarmor` · `ClamAV` · `Elasticsearch` · `Logstash` · `Kibana` · `NXLog` · `TheHive` · `Shuffle` · `Cortex` · `Nmap` · `UFW` · `Fail2Ban` · `Lynis` · `Linux`

## Included academic work

| # | Lab | Portfolio write-up | Original PDF |
|---:|---|---|---|
| 1 | Enterprise Blue Team Security Operations | [`docs/enterprise-blue-team-security-operations.md`](docs/enterprise-blue-team-security-operations.md) | [PDF report](docs/enterprise-blue-team-security-operations.pdf) |
| 2 | Secure System Hardening & Auditing | [`docs/secure-system-hardening-and-auditing.md`](docs/secure-system-hardening-and-auditing.md) | [PDF report](docs/secure-system-hardening-and-auditing.pdf) |

## Repository structure

```text
.
├── README.md
└── docs/
    ├── *.md   # GitHub-friendly lab write-ups
    └── *.pdf  # Original lab reports (privacy-redacted where noted)
```

The Markdown write-ups and supplied PDF reports form the complete available portfolio evidence. Screenshots, diagrams, and tool output are preserved inside the reports; standalone source code, captures, notebooks, and other artifacts are included only if supplied.

## Evidence policy

This repository uses only the academic reports and evidence actually supplied for the portfolio. The original reports contain screenshots and tool output, but no additional screenshots, source files, configurations, packet captures, or results are claimed here unless they were present in the supplied work. The write-ups preserve negative and incomplete findings rather than inventing cleaner outcomes.

## Responsible use

Security techniques in this repository were performed in controlled academic environments. Use attack and exploitation techniques only on systems you own or have explicit authorization to test.
