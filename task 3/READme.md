Vulnerability Assessment Process Summary

OpenVAS Installation & Setup:

-> Installed Greenbone Vulnerability Management (GVM) and OpenVAS on Kali Linux (sudo apt install gvm).

-> Initiated the core setup (sudo gvm-setup) to configure services and download vulnerability feeds.

Service Troubleshooting:

-> Diagnosed gvmd failures: Used sudo systemctl status gvmd and journalctl -u gvmd to identify that the Greenbone Vulnerability Manager daemon was not running.

-> Resolved PostgreSQL issues: Addressed instances where the PostgreSQL database (essential for GVM) was inactive or reported an "Assertion failed" error during startup. This involved:

-> Updating package lists and adding the PostgreSQL repository.

-> Attempting to start PostgreSQL service using sudo systemctl start postgresql and sudo pg_ctlcluster 15 main start.

-> Performing a full reinstallation of PostgreSQL and GVM when persistent issues arose (sudo apt purge postgresql* gvm openvas, sudo apt install postgresql-15 gvm).

-> Re-creating the PostgreSQL database cluster (sudo pg_createcluster 15 main).

-> Managed GVM services: Consistently used sudo gvm-stop and sudo gvm-start to restart the entire GVM suite after troubleshooting.

Web Interface Access & Scan Configuration:

-> Successfully accessed the OpenVAS web interface at https://127.0.0.1:9392, including troubleshooting browser cache issues by using a private browsing window.

-> Created a new Scan Target for your local machine (127.0.0.1 or localhost).

-> Created a new Scan Task, linking it to your target, and selecting "OpenVAS Default" as the scanner.

-> Configured the Scan Config to "Full and fast" (after ensuring scanner selection made this option accessible).

-> Launched the vulnerability scan from the "Tasks" dashboard.

Report Analysis & Vulnerability Remediation:

-> Monitored the scan status until completion.

-> Accessed the detailed scan report, reviewing findings by severity.

-> Identified the "Allowed HTTP Methods Enumeration" (medium severity) as a key vulnerability.

Troubleshot Apache Port Conflict:

-> Attempted to restart Apache, which failed due to "Address already in use: AH00072: make_sock: could not bind to address 0.0.0.0:80".

-> Used sudo lsof -i :80 to identify the gsad process as the conflicting service.

-> Killed the conflicting gsad process (sudo kill -9 <PID>).

-> Successfully restarted Apache (sudo systemctl restart apache2).

Documentation:

-> Researched simple fixes and mitigations for identified vulnerabilities.

-> Captured various screenshots throughout the process, including scan summaries, detailed vulnerability reports, and the specific commands used for the Apache port conflict resolution.

-> Prepared a comprehensive report documenting all phases of the vulnerability assessment, findings, and remediation steps.