
# Delta Steel — Penetration Testing Assessment

<p align="center">
  <strong>A Hands-On Cybersecurity Assessment of a Deliberately Vulnerable Linux Lab Environment</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Domain-Cybersecurity-0A66C2?style=for-the-badge" alt="Cybersecurity">
  <img src="https://img.shields.io/badge/Assessment-Penetration%20Testing-red?style=for-the-badge" alt="Penetration Testing">
  <img src="https://img.shields.io/badge/Environment-Isolated%20Lab-success?style=for-the-badge" alt="Isolated Lab">
  <img src="https://img.shields.io/badge/Status-Assessment%20Completed-brightgreen?style=for-the-badge" alt="Assessment Completed">
</p>

## Overview

**Delta Steel** is a cybersecurity penetration testing project that evaluates the security posture of a deliberately vulnerable **Metasploitable 2 virtual machine** in an isolated laboratory environment.

The assessment demonstrates a structured penetration testing workflow, from network reconnaissance and service enumeration to vulnerability analysis, controlled exploitation, impact assessment, and remediation planning.

Using **Kali Linux, Nmap 7.95, and the Metasploit Framework**, the project investigates how outdated software, exposed network services, insecure configurations, default credentials, and intentionally installed backdoors can create practical paths to system compromise.

The project is documented in a penetration testing assessment report prepared as part of a cybersecurity programme.

> **Project objective:** Demonstrate practical penetration testing skills, validate selected vulnerabilities in an authorized lab, document evidence, assess risk, and recommend actionable security improvements.

## Table of Contents

- [Project Objectives](#project-objectives)
- [Problem Statement](#problem-statement)
- [Scope and Rules of Engagement](#scope-and-rules-of-engagement)
- [Key Features](#key-features)
- [Tools and Technologies](#tools-and-technologies)
- [Assessment Methodology](#assessment-methodology)
- [Key Findings](#key-findings)
- [Installation and Lab Setup](#installation-and-lab-setup)
- [Usage](#usage)
- [Results and Deliverables](#results-and-deliverables)
- [Recommendations](#recommendations)
- [Repository Structure](#repository-structure)
- [Limitations](#limitations)
- [Contributing](#contributing)
- [References](#references)
- [Author](#author)
- [License](#license)

## Project Objectives

The primary objectives of this assessment were to:

- Perform authorized reconnaissance and enumerate exposed TCP services.
- Identify service versions and investigate associated security weaknesses.
- Map relevant findings to known CVEs and CVSS severity ratings where supported by evidence.
- Validate selected vulnerabilities through controlled exploitation.
- Document successful and unsuccessful exploitation attempts.
- Evaluate the potential impact of the access obtained during testing.
- Develop prioritized remediation recommendations.
- Apply recognized penetration testing and security assessment methodologies.
- Demonstrate the importance of patch management, secure configuration, and network segmentation.

## Problem Statement

Legacy systems and poorly secured network services can expose organizations to significant security risks. Outdated software, default credentials, unencrypted remote access, and unnecessary service exposure may allow attackers to gain unauthorized access or compromise a system.

This project investigates these risks through a controlled assessment of a deliberately vulnerable Linux virtual machine.

The assessment addresses the following questions:

1. Which network services are exposed on the target host?
2. Which identified services present potential security risks?
3. Can selected vulnerabilities be validated through authorized testing?
4. What level of access can a successful exploitation attempt establish?
5. Which remediation measures should be prioritized to reduce the attack surface?

The findings illustrate how multiple weaknesses can combine to create several independent paths to system compromise.

## Scope and Rules of Engagement

| Parameter | Details |
|---|---|
| Project | Delta Steel Penetration Testing Assessment |
| Assessment date | 12 October 2025 |
| Target | Metasploitable 2 virtual machine |
| Target address in the original lab | `10.0.2.9` |
| Scope | Single host (`10.0.2.9/32`) |
| Attacker environment | Kali Linux |
| Primary scanning tool | Nmap 7.95 |
| Exploitation framework | Metasploit Framework |
| Network environment | Isolated host-only or NAT-configured lab network |
| Assessment type | Authorized internal penetration test |

### Rules of Engagement

- Testing was restricted to the designated laboratory target.
- Explicit authorization was established for the assessment.
- Production systems and real user data were outside the testing environment.
- Destructive attacks, data modification, and denial-of-service testing were prohibited.
- Exploitation attempts and their outcomes were documented.

**Important:** The target IP address is specific to the original lab configuration. Use the IP address assigned to your own isolated virtual machine when reproducing the assessment.

## Key Features

### 1. Network Reconnaissance

Used Nmap to identify exposed TCP ports, detect running services, and collect version information across the target's TCP port range.

### 2. Service Enumeration and Vulnerability Analysis

Investigated legacy services, exposed administrative interfaces, insecure remote access protocols, and database configuration weaknesses. Relevant findings were mapped to CVE or CWE references where applicable.

### 3. Controlled Exploitation

Conducted three targeted exploitation attempts using the Metasploit Framework:

- Samba `usermap_script` command injection.
- PostgreSQL exploitation involving default credentials.
- Apache Tomcat Manager WAR upload.

The report records two successful attempts and one unsuccessful attempt.

### 4. Evidence-Based Reporting

Documented the assessment scope, identified services, findings, exploitation outcomes, screenshots, severity classifications, and remediation recommendations.

### 5. Risk Assessment and Prioritization

Organized findings by severity and proposed remediation actions according to urgency, potential impact, and exposure.

### 6. Remediation Planning

Developed recommendations covering patch management, credential security, service hardening, network access restrictions, monitoring, and follow-up testing.

## Tools and Technologies

| Tool or Technology | Purpose |
|---|---|
| Kali Linux | Penetration testing operating environment |
| Nmap 7.95 | Network scanning and service/version enumeration |
| Metasploit Framework | Controlled validation of selected vulnerabilities |
| Metasploitable 2 | Deliberately vulnerable Linux target |
| CVE / NVD | Vulnerability identification and reference lookup |
| CVSS 3.1 | Vulnerability severity assessment |
| PTES | Penetration testing methodology |
| OWASP Testing Guide | Guidance for relevant web-service and authentication testing |
| NIST SP 800-115 | Technical security testing and assessment guidance |

## Assessment Methodology

The assessment followed a structured workflow informed by the Penetration Testing Execution Standard (PTES), the OWASP Testing Guide, and NIST SP 800-115.

### Phase 1 — Reconnaissance

Identified the target host and established the scope of the assessment.

### Phase 2 — Scanning and Enumeration

Performed service and version detection to identify exposed services and build an inventory of the target's attack surface.

### Phase 3 — Vulnerability Analysis

Reviewed the identified service versions and configurations against relevant vulnerability references. Findings were classified according to available evidence and severity information.

### Phase 4 — Controlled Exploitation

Selected three test cases to validate the exploitability of identified weaknesses. Each attempt was recorded as successful or unsuccessful.

### Phase 5 — Reporting and Remediation

Consolidated the findings, assessed potential impact, and prepared prioritized recommendations for reducing the identified risks.

Post-exploitation activity was limited to session confirmation and impact assessment. Destructive actions, credential exfiltration, and persistence deployment were not performed.

## Key Findings

The original report identified **23 open TCP services**, including high-numbered RPC-related ports, and documented 12 unique security findings.

### Finding Summary

| Severity | Count | Recommended Response |
|---|---:|---|
| Critical | 4 | Immediate remediation |
| High | 5 | Address within 7 days |
| Medium | 3 | Address within 30 days |
| Low | 0 | No low-severity findings recorded |
| **Total** | **12** | Prioritize critical and high findings |

### Selected Findings

| Finding | Reference | Severity | Assessment Outcome |
|---|---|---|---|
| Metasploitable root bind shell | By design | Critical | Confirmed |
| vsftpd 2.3.4 backdoor | CVE-2011-2523 | Critical | Vulnerable version identified |
| Samba `usermap_script` command injection | CVE-2007-2447 | Critical | Exploitation successful |
| PostgreSQL default credentials | Configuration weakness | Critical | Exploitation successful |
| UnrealIRCd 3.2.8.1 backdoor | CVE-2010-2075 | High | Vulnerable version identified |
| Telnet and legacy remote access exposure | CWE-312 / CWE-311 | High | Exposure observed |
| NFS and database service exposure | CWE-552 / CWE-306 | High | Exposure observed |
| VNC remote desktop exposure | CWE-306 | Medium | Exposure observed |
| Apache HTTP, Tomcat, and AJP services | Multiple references | Medium | Further validation recommended |

*Severity labels and validation statuses reflect the original assessment report. Some classifications represent exposure or configuration risks rather than independently confirmed exploitation. CVSS values should be interpreted in the context of the specific finding and its supporting evidence.*

### Exploitation Results

| Test Case | Result | Significance |
|---|---|---|
| Samba `usermap_script` | Successful | A command shell session was established on the target. |
| PostgreSQL payload | Successful | A Meterpreter session was established using the documented default credentials. |
| Apache Tomcat Manager WAR upload | Unsuccessful | The management interface was inaccessible or the required authentication was not obtained. |

The unsuccessful Tomcat attempt does **not** establish that the Tomcat service is secure. Further configuration and vulnerability assessment would be required.

## Installation and Lab Setup

This repository documents a penetration testing assessment rather than a standalone software application. Reproducing the work therefore requires a suitable laboratory environment.

### Prerequisites

- A computer capable of running virtual machines.
- Kali Linux with Nmap and the Metasploit Framework.
- A Metasploitable 2 virtual machine.
- Virtualization software capable of creating an isolated virtual network.
- Permission to conduct all testing against the designated target.

### Step 1 — Prepare the Laboratory

Set up Kali Linux and Metasploitable 2 as separate virtual machines.

Configure a host-only or otherwise appropriately isolated laboratory network. Verify that the target is not exposed to untrusted networks.

### Step 2 — Verify Connectivity

From Kali Linux, confirm that the target is reachable:

```bash
ping <LAB_TARGET_IP>
```

Replace `<LAB_TARGET_IP>` with the address assigned to your Metasploitable 2 VM. Some targets may not respond to ICMP, so a failed ping alone does not establish that the host is unavailable.

### Step 3 — Verify the Tools

Check that Nmap and Metasploit are available:

```bash
nmap --version
msfconsole --version
```

The original assessment used Nmap 7.95. Tool versions in a reproduced assessment may differ.

### Step 4 — Obtain the Project Documentation

Clone the repository after replacing the placeholder with the actual repository URL:

```bash
git clone <REPOSITORY_URL>
cd <REPOSITORY_DIRECTORY>
```

The commands above assume that the repository has been published and that its directory structure matches the values supplied.

## Usage

The following steps outline the documented assessment workflow. They are intended for authorized testing in an isolated laboratory.

### 1. Enumerate TCP Services

Perform service and version detection across the target's TCP ports:

```bash
nmap -sV -p- <LAB_TARGET_IP>
```

This scan helps identify reachable TCP ports and fingerprint the services running on them.

To retain the output for later analysis:

```bash
nmap -sV -p- -oN nmap-results.txt <LAB_TARGET_IP>
```

Review the output and record the service names, detected versions, ports, and any relevant uncertainty in the results.

### 2. Research Potential Vulnerabilities

Compare the identified service versions and configurations with trusted vulnerability references:

- [National Vulnerability Database](https://nvd.nist.gov/)
- [MITRE CVE Program](https://www.cve.org/)
- [Common Vulnerability Scoring System v3.1](https://www.first.org/cvss/v3.1/)

Do not assume that a detected version alone proves a vulnerability is exploitable. Consider configuration, available evidence, and the applicability of the relevant advisory.

### 3. Validate Selected Findings

Use the Metasploit Framework only for authorized, in-scope validation. The original project assessed Samba, PostgreSQL, and Apache Tomcat.

Record the selected test case, prerequisites, target service, observed outcome, and supporting evidence. Keep testing confined to the designated lab host.

### 4. Assess Impact

Document the access level and potential security implications demonstrated by each successful test. Clearly distinguish observed results from potential impacts that were not directly tested.

### 5. Prepare the Assessment Report

Consolidate the service inventory, vulnerability references, severity ratings, screenshots, test outcomes, limitations, and prioritized remediation actions.

## Results and Deliverables

The original assessment produced a 34-page penetration testing report containing:

- Assessment objectives, scope, and rules of engagement.
- Laboratory configuration and testing methodology.
- Nmap service enumeration results.
- Vulnerability analysis and severity classifications.
- Evidence of the Samba and PostgreSQL exploitation outcomes.
- Documentation of the unsuccessful Tomcat exploitation attempt.
- Post-exploitation impact assessment.
- Consolidated security findings.
- Prioritized remediation recommendations.
- References to relevant vulnerability databases and security frameworks.

**Report:** [View the full assessment report](<REPORT_FILE_OR_URL>)

Replace the placeholder with the report's actual path in the repository or a link to an appropriately sanitized copy.

### Screenshots and Evidence

If approved for public release, place selected, sanitized screenshots in the repository and link them here.

Suggested evidence to include:

- Network scanning and service enumeration results.
- Service version identification.
- Successful test outcomes with sensitive information redacted.
- The unsuccessful Tomcat test and its documented limitation.
- A summary of the findings and remediation priorities.

Example Markdown for a screenshot once it has been added:

```markdown
![Nmap service enumeration results](docs/images/nmap-results.png)
```

The image path is a placeholder; add the corresponding image before using it.

## Recommendations

The report prioritizes the following improvements:

### Immediate Priorities

- Isolate or disable the pre-installed root bind shell.
- Replace or remediate the vulnerable vsftpd service.
- Patch Samba and address the `usermap_script` vulnerability.
- Replace default PostgreSQL credentials with strong, unique credentials.
- Restrict access to database and administrative services.

### High-Priority Improvements

- Disable Telnet, `rlogin`, `rsh`, and `rexec` where unnecessary.
- Restrict NFS exports and remote database access.
- Remove or secure unnecessary FTP and IRC services.
- Review authentication and access controls across exposed services.

### Longer-Term Improvements

- Establish recurring patch management and vulnerability assessments.
- Apply network segmentation and least-privilege access controls.
- Centralize security logging and improve detection capabilities.
- Conduct follow-up validation to verify remediation effectiveness.

These recommendations were developed for the assessed environment. Remediation decisions for other systems should be based on their own configurations, operational requirements, and risk assessments.

## Repository Structure

The exact repository structure was not included in the supplied report. The following is a suggested layout for publishing the project:

```text
delta-steel-pentest/
├── README.md
├── docs/
│   └── images/
│       ├── nmap-results.png
│       ├── samba-test-evidence.png
│       └── postgres-test-evidence.png
├── reports/
│   └── <SANITIZED_ASSESSMENT_REPORT>
└── references/
    └── <SUPPORTING_DOCUMENTATION>
```

Only include files and directories that actually exist in the repository. Avoid publishing unredacted evidence or sensitive exploitation details.

## Limitations

- The assessment covered a single deliberately vulnerable virtual machine, not an entire enterprise network.
- Findings reflect the target configuration and observations made during the October 2025 assessment.
- Only three targeted exploitation attempts were documented.
- The Tomcat Manager exploitation attempt was unsuccessful; this does not prove that the service is secure.
- Post-exploitation activity was limited and did not establish the full impact of every identified weakness.
- Service exposure and potential vulnerabilities should not automatically be interpreted as confirmed, exploitable findings.

The results are intended to demonstrate assessment techniques and security lessons in a controlled lab, not to establish the security posture of a production organization.

## Contributing

Contributions that improve the documentation, reproducibility, evidence organization, and clarity of the assessment are welcome.

1. Fork the repository.
2. Create a branch for your proposed change.
3. Make your changes and verify that commands, references, and file paths are accurate.
4. Submit a pull request explaining the change and its purpose.

Please ensure that contributions:

- Preserve the distinction between confirmed findings and potential risks.
- Use credible sources for vulnerability references.
- Redact credentials, sensitive data, and identifying information.
- Do not include evidence obtained without authorization.
- Keep all testing instructions limited to systems that the tester owns or is explicitly authorized to assess.

## References

The following resources informed the original assessment:

- [Nmap — Network Mapper](https://nmap.org/)
- [Metasploit Framework — Rapid7](https://www.metasploit.com/)
- [Metasploitable](https://github.com/rapid7/metasploitable3)
- [CVE-2007-2447 — Samba usermap_script](https://nvd.nist.gov/vuln/detail/CVE-2007-2447)
- [CVE-2011-2523 — vsftpd 2.3.4 backdoor](https://nvd.nist.gov/vuln/detail/CVE-2011-2523)
- [CVE-2010-2075 — UnrealIRCd backdoor](https://nvd.nist.gov/vuln/detail/CVE-2010-2075)
- [Penetration Testing Execution Standard (PTES)](http://www.pentest-standard.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [NIST SP 800-115 — Technical Guide to Information Security Testing and Assessment](https://csrc.nist.gov/pubs/sp/800/115/final)
- [CVSS v3.1 Specification](https://www.first.org/cvss/v3.1/specification-document)

## Author

**Adewale J Bhadmus**

Cybersecurity | Penetration Testing | Vulnerability Assessment

- GitHub: [@YOUR_GITHUB_USERNAME](https://github.com/YOUR_GITHUB_USERNAME)
- LinkedIn: [YOUR_LINKEDIN_PROFILE](<LINKEDIN_PROFILE_URL>)
- Email: [YOUR_PUBLIC_CONTACT_EMAIL](mailto:<PUBLIC_CONTACT_EMAIL>)

*Replace the profile and contact placeholders with the details you wish to make public.*

## License

No license was specified in the supplied assessment report.

If you intend to publish the documentation or supporting materials as an open-source project, add an appropriate `LICENSE` file and update this section. Do not assume that third-party software, screenshots, or assessment evidence can be redistributed without checking their applicable terms.

---

**Disclaimer:** This project documents an authorized penetration testing exercise against a deliberately vulnerable laboratory virtual machine. It is provided for educational and defensive security purposes. Do not scan, exploit, or attempt to access systems without explicit authorization. Never expose a Metasploitable virtual machine to the public internet.
