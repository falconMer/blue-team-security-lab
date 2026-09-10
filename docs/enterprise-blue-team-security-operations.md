# Enterprise Blue Team Security Operations

> Portfolio write-up derived from the original university cybersecurity lab report provided by Smail Mersad. The original report contains screenshots and UI evidence; this GitHub edition uses only results from that report and does not invent additional assets.

**Academic context:** Amar Telidji University, Computer Science / Cybersecurity Engineering, 2025-2026.

## Scope

This was the broadest defensive-security lab in the academic portfolio. It covered reconnaissance, data protection, credential security, firewall/IDS/IPS deployment, centralized logging, Windows event analysis, incident handling, and security automation.

## 1. Network reconnaissance and exposure analysis

Nmap was used against a controlled Ubuntu target to identify exposed services and perform service/version and vulnerability-oriented scanning. The observed target exposed FTP, SSH, Telnet, and Elasticsearch. The report discusses attack-surface reduction, especially disabling insecure/unnecessary services such as Telnet and restricting sensitive services with firewall policy.

## 2. Data protection and concealment

The lab used `ccencrypt/ccrypt` to encrypt and decrypt a test file and discussed the importance of strong key handling. A separate steganography exercise used `steghide` to place a text file inside an image and recover it later, demonstrating why apparently normal media can carry concealed data.

## 3. Password security

Several credential-security controls were tested:

- KeePassXC vault creation and generated passwords.
- Linux `pwquality` complexity policy through PAM.
- Password aging with `chage`.
- A Bash script that used the Have I Been Pwned k-anonymity-style hash-prefix workflow to check test passwords against breach data without sending the complete password hash.

## 4. Hidden-service analysis

A local onion service was scanned with OnionScan. The scan completed without reported findings in the observed exercise. The report uses the exercise to discuss metadata leakage and operational-security considerations around hidden services.

## 5. Layered OPNsense security gateway

OPNsense was extended with multiple defensive layers:

### Suricata IDS/IPS

Suricata was configured on the WAN side in IPS mode. Threat-intelligence rules included abuse.ch feeds and matching traffic was configured to be dropped.

### Zenarmor

Zenarmor was enabled on the LAN side for application-aware inspection and reporting of client traffic.

### ClamAV

ClamAV services were installed and enabled, with proxy/ICAP integration used to add antivirus inspection for web traffic and transferred files.

Together, these controls turned the base firewall into a layered security gateway combining network filtering, intrusion prevention, application visibility, and malware scanning.

## 6. Centralized logging with the ELK Stack

Elasticsearch, Logstash, and Kibana were installed and tested. Generated logs were ingested through Logstash, indexed in Elasticsearch, and reviewed in Kibana Discover.

This demonstrated the value of centralized telemetry for correlation and investigation compared with leaving logs isolated on individual endpoints.

## 7. Windows log forwarding and anomaly detection

NXLog was used to forward Windows Security/System logs over Syslog to the Linux analysis machine. The pipeline was:

```text
Windows -> NXLog -> Syslog/rsyslog -> Logstash -> Elasticsearch -> Kibana
```

The report specifically identified:

- **Event ID 4625** — failed logon activity.
- **Event ID 4672** — special privileges assigned to a new logon.

These were used as examples of authentication- and privilege-related indicators that can be centralized and investigated in a SIEM-style workflow.

## 8. Incident handling and case management

The lab used TheHive to demonstrate incident-case documentation, assignment, tracking, accountability, and traceability as part of an organized security-operations workflow.

## 9. SOAR / observable enrichment

Cortex was configured as an analysis platform for observables such as IP addresses and file hashes. A Shuffle workflow represented the automation path for sending observables to analysis actions.

The exercise demonstrates the SOAR concept: automate repetitive enrichment and analysis so analysts can receive context faster instead of manually checking each observable.

## Main technologies

`Nmap` · `KeePassXC` · `pwquality` · `chage` · `OnionScan` · `OPNsense` · `Suricata` · `Zenarmor` · `ClamAV` · `Elasticsearch` · `Logstash` · `Kibana` · `NXLog` · `TheHive` · `Cortex` · `Shuffle`

## Portfolio takeaway

The value of this lab is not any one tool in isolation. It demonstrates a defense-in-depth workflow spanning discovery, prevention, endpoint/network telemetry, centralized analysis, incident management, and automation — the same categories of work that appear in SOC and blue-team environments.
