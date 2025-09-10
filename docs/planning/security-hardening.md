# Security Hardening Project (July 2025)

| Phase | Task | SubTasks | Estimate Hour | Goal | Impact | Priority | Status | Report | Start Date | End Date |
|-------|------|----------|---------------|------|--------|----------|--------|--------|------------|----------|
| **0 - Credential & Asset Data Collection** | | | | | | | | | | |
| | Inventory All Credentials | Mikrotik, Bare Metal, VM, RDP, Portal | 6 | Map all current accounts and reduce unknowns | | High | Done | List Password Andal 23 Juni 2025.xlsx | - | - |
| | Collect Stored Keys & Secrets | Audit [ssh] /authorized_keys on all servers<br/>Check credential storage systems<br/>Identify hardcoded credentials | 6 | Identify reused, weak, or stale credentials | | High | Done | Report - Collect Stored Keys & Secrets | 2 Juli 2025 | 2 Juli 2025 |
| | Centralize & Encrypt Collected Data | Store findings in encrypted vault<br/>Tag each with rotation status | 4 | Secure sensitive info while enabling analysis | | High | Cancelled | Sudah implementasi ZTNA | - | - |
| | Identify Orphaned & Unused Accounts | Look for last login timestamps<br/>Disable accounts unused for 90+ days | 4 | Reduce attack surface by removing dormant accounts | Someone may lose access | Medium | Done | Last Login Timestamps VM Colo | 3 Juli 2025 | 3 Juli 2025 |
| **1 - Evidence Preservation** | | | | | | | | | | |
| | Preserve Evidence | Connect to MikroTik<br/>Run /export file=backup.rsc | 3 | Retain configuration and system evidence | | High | Done | Report - Preserve Evidence Mikrotik2 | 4 Juli 2025 | 4 Juli 2025 |
| **2 - Compromise & Backdoor Scanning** | | | | | | | | | | |
| | Scan for known Linux rootkits & backdoors | Run chkrootkit, rkhunter, YARA, etc. | 8 | | | | Done | velociraptor - scan_results | 4 Juli 2025 | 7 Juli 2025 |
| | Inspect unusual system binaries | Hash critical binaries and compare to known-good | 6 | | | | Done | velociraptor - analzye | 7 Juli 2025 | 8 Juli 2025 |
| | Audit crontabs, rc.local, systemd, startup scripts | Look for unauthorized jobs or persistence | 6 | | | | Done | | 7 Juli 2025 | 8 Juli 2025 |
| | Network backdoor check | Use ss, netstat, lsof, Wireshark/tcpdump, Nmap scans | 6 | | | | Done | network_backdoor_check - OneDrive | 9 Juli 2025 | 11 Juli 2025 |
| | Review backdoor scan results | | 16 | | | | | | 14 Juli 2025 | 14 Juli 2025 |
| **3 - Secure Rebuild & Hardening** | | | | | | | | | | |
| | Mikrotik Service Minimization | Disable telnet, ftp, www, api, api-ssl<br/>Allow Winbox/SSH only from jump host | 4 | Reduce attack surface | Loss of legacy service access | High | Done | | 15 Juli 2025 | 15 Juli 2025 |
| | Mikrotik Firewall Hardening | First rule: drop invalid connections<br/>Explicit allow rules only<br/>Block remote mgmt from public | 8 | Control ingress/egress precisely | Risk of lockout or service drop | High | Done | | 15 Juli 2025 | 15 Juli 2025 |
| | Mikrotik SSH Security | Enforce SSH key auth<br/>Disable root login<br/>Enable strong crypto | 6 | Prevent brute-force & privilege escalation | SSH with password not available | High | Done | | 16 Juli 2025 | 16 Juli 2025 |
| | Mikrotik Secure Logging | Configure remote syslog to Wazuh/Logstash | 8 | Enable centralized visibility | | High | Done | | 17 Juli 2025 | 17 Juli 2025 |
| | Infrastructure Fresh Reinstall | Reimage all systems from known-good ISOs | 16 | Eliminate rootkits/backdoors | Downtime | High | Cancelled | belum memungkinkan melakukan karena kurang dokumentasi | 10 Juli 2025 | |
| | Infrastructure Patch Management | Register all systems to update service | 8 | Prevent exploits via known CVEs | | High | Planned | | 14 Juli 2025 | |
| | VLAN Segmentation | Define VLANs: mgmt, web, app, db, office | 16 | Limit lateral movement | Communication breaks likely | High | Cancelled | berisiko network breaks | 15 Juli 2025 | |
| | WireGuard Full Mesh VPN | Deploy WireGuard Server in internal cluster | 16 | Secure site-to-site transport | Current connections might be disturbed | High | Cancelled | https://teleport-cluster.test.andalsoftware.com/ | 17 Juli 2025 | |
| | ZTNA for Remote Access | Deploy Cloudflare Access or Tailscale | 8 | No network exposure; app-level trust | | High | Cancelled | sudah implementasi ZTNA teleport | 18 Juli 2025 | |
| **4 - Monitoring, IAM, and Operations** | | | | | | | | | | |
| | Deploy Wazuh SIEM | Install Wazuh Indexer, server and dashboard<br/>Upgrade version<br/>Set up SSL certificates | 24 | Full visibility and alerting | | High | Done | https://wazuh.andalsoftware.com | 3 Juli 2025 | 7 Juli 2025 |
| | MikroTik Log Forwarding | /system logging to send logs to Logstash | 6 | Central log analysis | | High | Done | https://kibana.andalsoftware.com | 17 Juli 2025 | 17 Juli 2025 |
| | Alerting Rules Setup | Failed logins, abnormal geolocation<br/>FIM triggers, privilege escalation | 8 | Timely breach detection | | High | Planned | | 23 Juli 2025 | |
| | Deploy FreeIPA Cluster | Install HA FreeIPA<br/>Harden root/admin access | 16 | Unified user directory | | High | Cancelled | sudah implementasi ZTNA teleport | 25 Juli 2025 | |
| | FreeIPA Group Policies | Define groups by role<br/>HBAC access rules | 8 | Role-based access control | Restriction enforcement | High | Cancelled | sudah implementasi ZTNA teleport | 29 Juli 2025 | |
| | MikroTik RADIUS Integration | Set up FreeRADIUS<br/>Configure /radius login | 8 | Central login and auditing | | High | Cancelled | | 30 Juli 2025 | |
| | SSH Hardening Across Servers | SSSD + FreeIPA + MFA<br/>Disable password SSH logins | 16 | Central key control & MFA enforcement | | High | Cancelled | akses SSH sudah disable semua ke mikrotik | 31 Juli 2025 | |


---
*Last Updated: September 10, 2025*