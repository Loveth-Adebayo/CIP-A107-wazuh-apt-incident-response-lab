# CIP-A107-wazuh-apt-incident-response-lab
A SOC Level 3 lab demonstrating the detection, analysis, and containment of a simulated Advanced Persistent Threat (APT) using Wazuh SIEM, MITRE ATT&amp;CK mapping, custom detection rules, and vulnerability management.

Project Overview
This repository contains the technical documentation and incident report for an Advanced Persistent Threat (APT) simulation named Operation Crimson Dawn. The project demonstrates the capabilities of the Wazuh SIEM in detecting multi-stage attacks, correlating logs across Linux and Windows endpoints, and utilizing Active Response for automated threat containment.

Architecture
The lab environment consists of three main components:
Wazuh Manager and Indexer: Hosted on an Ubuntu Server VM. Acts as the central brain for log collection, rule matching, and alerting.
Ubuntu Web Server (ubuntu-dvwa): The initial point of compromise. Monitored by a Wazuh agent.
Windows Endpoint (DESKTOP-ADDFGV1): The target of lateral movement and data exfiltration. Monitored by a Wazuh agent.

Key Phases and Capabilities Demonstrated
Phase 1: Reconnaissance
Detected port scanning and SSH brute-force attempts against the Web Server using Wazuh authentication failure rules (MITRE T1595, T1110).

Phase 2: Persistence and Exploitation
Utilized File Integrity Monitoring (FIM) to detect the creation of a disguised payload (update.pdf.exe). Detected the creation of a malicious cron job designed to maintain persistence (MITRE T1053.003, T1036).

Phase 3: Lateral Movement
Correlated Windows Security Event IDs (4624, 4625) to detect an SMB lateral movement attempt from the Web Server to the Windows ADMIN$ share (MITRE T1021.002).

Phase 4: Data Exfiltration
Monitored process creation and command-line arguments to catch PowerShell staging and exfiltrating sensitive data to a simulated Command and Control (C2) server (MITRE T1560.001, T1041).

Phase 5: Threat Intelligence and Containment
Developed a custom Wazuh rule (Rule ID 100002) to trigger Level 12 alerts on traffic matching the known C2 IP address (10.79.147.91).
Configured Wazuh Active Response to automatically drop the attacker's IP at the firewall for 600 seconds.

Repository Contents
Screenshots/: Contains all the visual evidence collected during the lab, mapped to specific phases (Phase 1 through Phase 5).
Incident_Report.pdf: The complete CISO and Board-level incident report, including the attack timeline, business impact assessment, and answers to the strategic analysis questions.

Author
Loveth Adebayo
Cybersecurity Analyst

