Lab: Web Vulnerability Scanning with OWASP ZAP

Objective: To conduct an automated vulnerability assessment of a web application to identify security flaws, categorized by threat level, using OWASP ZAP.
Tools Used:
•	OWASP ZAP 2.13.0: An open-source web application security scanner.
•	Damn Vulnerable Web Application (DVWA): A PHP/MySQL web application that is intentionally vulnerable for security testing.
•	Kali Linux: The operating system used to host the security tools.

1. Tool Initialization and Target Setup
The process began by launching the OWASP ZAP application and navigating to the Automated Scan interface. The target URL in this case, the DVWA instance at http://172.17.0.2/dvwa/ was entered into the "URL to attack" field.
 
 Screenshots3/Tool Initialization and Target Setup.png

2. Executing the Automated Attack
ZAP utilized a Traditional Spider to crawl the website, mapping out all accessible pages and directories. Once the mapping was complete, it initiated an active scan (the "Attack") to probe the identified URLs for vulnerabilities.
 
 Screenshots3/2. Executing the Automated Attack.png
 
3. Vulnerability Analysis and Categorization
The scan results were populated in the Alerts tab, where vulnerabilities were categorized by threat level using color-coded flags:
•	Red Flag: High Risk (Critical vulnerabilities).
•	Orange Flag: Medium Risk.
•	Yellow Flag: Low Risk.
•	Blue Flag: Informational.

Screenshots3/3. Vulnerability Analysis and Categorization.png
 
Key Findings & Observations
One of the most critical findings identified during the scan was a Remote Code Execution (RCE) vulnerability (CVE-2012-1823).
•	Vulnerability: Remote Code Execution - CVE-2012-1823.
•	Risk Level: High.
•	Description: Certain PHP versions, when configured to run using CGI, do not correctly handle query strings that lack an unescaped "=" character. This allows an attacker to pass command-line arguments to the PHP binary, leading to arbitrary code execution on the web server.
•	Proposed Solution: Upgrade to the latest stable version of PHP or configure the web server's mod_rewrite module to filter out malicious requests using specific RewriteCond and RewriteRule directives.
 
Screenshots3/Key Findings & Observations.png



