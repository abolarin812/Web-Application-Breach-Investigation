# Network Forensics: Web Application Breach Investigation

## Overview
This repository contains the incident report for a network forensics training exercise based on a simulated web server compromise. The objective was to analyze a packet capture file, reconstruct the full attack sequence, and document findings in a formal SOC incident report.

## Scenario
A production web server at bookworldstore.com was compromised through a SQL injection vulnerability in the site's search functionality. The attacker enumerated the database, exfiltrated credentials and customer PII, authenticated to the admin panel using stolen credentials, and deployed a PHP reverse shell to establish persistent access.

## Investigation Objectives
- Identify the attacker's IP address and geographic origin
- Determine the exploited endpoint and full SQL injection URI
- Reconstruct the database exfiltration method and identify compromised tables
- Identify the hidden directory discovered and accessed by the attacker
- Determine the credentials used to gain unauthorized access
- Identify the malicious script uploaded to maintain persistence

## Tools Used
- Wireshark (packet analysis and traffic extraction)

## Key Findings
- Attack origin: Shijiazhuang, Hebei Province, China (111[.]224[.]250[.]131)
- Technique: UNION-based SQL injection via sqlmap
- Exploited endpoint: /search.php
- Data exfiltrated: admin credentials (plaintext) and full customer PII records
- Hidden directory: /admin (discovered via automated directory brute-force)
- Credentials used: admin / admin123! (extracted from database dump)
- Web shell: NVri2vhp.php uploaded to /admin/uploads/ — PHP reverse shell on port 443
- Full compromise achieved in under 47 minutes

## Files
- 📄 Full SOC incident report — [View the Operation Silent Intrusion Incident Report](./SOC_Incident_Report_OperationSilentIntrusion.docx)

## Disclaimer
This is a training exercise conducted in a controlled environment. The packet capture was provided as part of an independent forensics program. No real systems were involved.
