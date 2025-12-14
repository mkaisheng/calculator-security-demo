# Security Scanning

## Overview
This repository uses three types of security scanning:

### SAST (Static Analysis with CodeQL)
- Scans source code for vulnerabilities
- Runs on push to main branch
- Checks for:
1.The language used for the source code
2.If one of the code fails ,request for developer to manually build it
- Artifacts: See GitHub Security tab

### SCA (Dependency Check)
- Scans Python packages for known CVEs
- Runs on push to main branch
- Runs the OWASP Dependency check
- Checks for: 1. Checks for Vulnerabilites in dependencies 2. Shows the Vulnerability score 3. Outdated /Known vulnerabilities inside the code
- Artifacts: sca-reports

### DAST (Live Application with ZAP)
- Tests running application for vulnerabilities
- Runs on push to main branch
- Checks for: Injections or data manipulation , Authenthication or session issues  , configuration or Environmental issues like Headrrs
- Artifacts: zap-baseline-reports, zap-fullscan-reports

## Understanding Results
The results can be interpreted based on how high the level of threat is based on the score.
It can also be interpreted by whether it has passed, Warn-new,warn-inprog,fail-new,fail-inprog and appriopriate action should be taken based on the affected warnings and fails

## Reporting Vulnerabilities
Please email security@example.com
