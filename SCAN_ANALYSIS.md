# Security Scan Analysis - [14/12/2025]

## DAST Results (ZAP Baseline)
- Total URLs scanned: 3
- PASS: 61 checks
- WARN-NEW: 8 warnings
- FAIL-NEW: 0 failures

### Warning Summary
WARN-NEW: X-Content-Type-Options Header Missing [10021] x 1 
WARN-NEW: Server Leaks Version Information via "Server" HTTP Response Header Field [10036] x 3 
WARN-NEW: Content Security Policy (CSP) Header Not Set [10038] x 2 
WARN-NEW: Storable and Cacheable Content [10049] x 3 
WARN-NEW: Permissions Policy Header Not Set [10063] x 3 
WARN-NEW: Modern Web Application [10109] x 1 
WARN-NEW: Insufficient Site Isolation Against Spectre Vulnerability [90004] x 3 
WARN-NEW: Sec-Fetch-Dest Header is Missing [90005] x 12 

## SCA Results (Dependency Check)
- High severity: 0
- Medium severity: 0
- Low severity: 0

### Vulnerable Packages

## SAST Results (CodeQL)
- Total issues: 1
- By type: Running a Flask application with debug mode enabled may allow an attacker to gain access through the Werkzeug debugger.

## Recommendations
Based on the ZAP reports , medium level threats should be handled first such as Missing anti clickjacking header or setting CSP header first before moving on to the other warnings . the SAST result given by CODEQL should also be handled quickly as it could take a few days before an attacker gains access .

### ZAP findings

|Code|Issue|Risk|Affected|Why It Matters|
|:----|:-----|:----|:--------|:--------------|
|10038|CSP Header Not Set|Medium|http://localhost:5000|Prevents XSS and Data Injection Attacks|
|10106|HTTP Only Site|Medium|http://localhost:5000|Vulnerable to Man in the middle attacks|
|10020|Missing Anti-clickjacking Header|Medium|http://localhost:5000|Site is vulnerable to Clickjacking attacks.|
|10021|X-Content-Type-Options Header Missing|Low|http://localhost:5000|Prevents MIME Sniffing|
|10036|Server Leaks Version Information|Low|http://localhost:5000|Helps attackers find known vulnerabilities based on patches|
|10063|Permissions Policy Header Not Set|Low|http://localhost:5000|Can help enhance user security and privacy|
|10038|Insufficient Site Isolation Against Spectre|Low|http://localhost:5000|Mitigation header against side-channel attacks like Spectre|


# Scanner Comparison

## Only CodeQL (SAST) Found
- Flask app running in Debug Mode

## Only ZAP (DAST) Found
- Missing Security Headers (CSP, Anti-clickjacking, X-Content-Type-Options, Permissions Policy)
- Runtime Configuration Issues (HTTP Only Site, Server version leakage)
- API Endpoint Vulnerabilities (The scan suggests a modern web application with API calls, e.g., /calculate)

## Only Dependency-Check (SCA) Found
- No known dependencies found


