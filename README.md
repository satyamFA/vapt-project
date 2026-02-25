# 🔐 Vulnerability Assessment Report — testphp.vulnweb.com

> **Future Interns Cybersecurity Track — Task 1 (2026)**  
> A professional, read-only passive security audit of a deliberately vulnerable web application.

---

## 📋 Project Overview

This repository contains the complete deliverable for a **Vulnerability Assessment** conducted as part of the Future Interns Cybersecurity internship program. The assessment follows ethical guidelines — no exploitation, no brute force, no unauthorized access was performed.

| Field              | Details                                       |
|--------------------|-----------------------------------------------|
| **Target Website** | http://testphp.vulnweb.com                    |
| **Target Type**    | Deliberately vulnerable demo site (Acunetix)  |
| **Assessment Date**| February 24–25, 2026                         |
| **Scope**          | Public-facing pages only — Read-Only          |
| **Methodology**    | OWASP WSTG — Passive Scanning                |

---

## 🎯 Why This Target?

`testphp.vulnweb.com` is a **legally safe practice target** created by Acunetix specifically for security learners and testers. It intentionally contains vulnerabilities like SQL Injection, XSS, and misconfigured headers — making it ideal for learning without risking legal or ethical issues.

**⚠️ Never test a real website without explicit written permission from the owner.**

---

## 🔍 Findings Summary

| ID      | Vulnerability                              | Severity   |
|---------|--------------------------------------------|------------|
| VUL-01  | SQL Injection (GET Parameter)              | 🔴 HIGH    |
| VUL-02  | Cross-Site Scripting (Reflected XSS)       | 🔴 HIGH    |
| VUL-03  | Verbose Error Messages (Info Disclosure)   | 🔴 HIGH    |
| VUL-04  | Outdated Apache Version Disclosed          | 🔴 HIGH    |
| VUL-05  | Missing Content-Security-Policy Header     | 🟡 MEDIUM  |
| VUL-06  | Missing X-Frame-Options Header             | 🟡 MEDIUM  |
| VUL-07  | Session Cookie Missing Secure/HttpOnly     | 🟡 MEDIUM  |
| VUL-08  | Directory Listing Enabled                  | 🟢 LOW     |
| VUL-09  | HTTP Used Instead of HTTPS                 | ℹ️ INFO    |

**Total: 9 findings | 4 HIGH | 3 MEDIUM | 1 LOW | 1 INFO**

---

## 🛠️ Tools Used

| Tool               | Purpose                              | Version         |
|--------------------|--------------------------------------|-----------------|
| **OWASP ZAP**      | Passive vulnerability scanning       | v2.15.0         |
| **Nmap**           | Port scanning & service detection    | v7.94           |
| **Browser DevTools** | Header & cookie inspection         | Chrome v122     |
| **Wappalyzer**     | Technology stack identification      | Browser Extension |

---

## 📁 Repository Structure

```
📦 vapt-project/
├── 📄 README.md                          ← This file
├── 📋 Vulnerability_Assessment_Report.docx  ← Full professional report
├── 📁 evidence/
│   ├── 📄 nmap_scan_output.txt           ← Raw Nmap results
│   ├── 📄 http_headers_analysis.txt      ← HTTP response headers
│   └── 📄 zap_passive_scan_findings.txt  ← OWASP ZAP findings log
```

---

## 🔬 Nmap Scan Command Used

```bash
nmap -sV -p 80,443,8080,21,22,3306 testphp.vulnweb.com
```

**Results:**
```
PORT     STATE  SERVICE  VERSION
80/tcp   open   http     Apache httpd 2.0.54 ((Linux))
443/tcp  closed https
8080/tcp open   http     Apache httpd 2.0.54
```

---

## 🔎 Key Security Header Issues Found

```
HTTP/1.1 200 OK
Server: Apache/2.0.54 (Linux)          ← SERVER VERSION EXPOSED ❌
Set-Cookie: PHPSESSID=abc123            ← NO HttpOnly FLAG ❌
                                        ← NO Secure FLAG ❌

MISSING HEADERS:
Content-Security-Policy: NOT PRESENT   ❌
X-Frame-Options: NOT PRESENT           ❌
Strict-Transport-Security: NOT PRESENT ❌
X-Content-Type-Options: NOT PRESENT    ❌
```

---

## ✅ Ethical Statement

This assessment was conducted:
- ✔ On a **deliberately vulnerable demo site** created for security testing
- ✔ Using **read-only, passive techniques only**
- ✔ Without any **exploitation, login bypass, or data modification**
- ✔ In compliance with **OWASP ethical testing guidelines**
- ✔ As part of a **supervised educational internship program**

---

## 📚 Learning Resources Used

- [OWASP Web Security Testing Guide (WSTG)](https://github.com/OWASP/www-project-web-security-testing-guide)
- [OWASP ZAP Documentation](https://www.zaproxy.org/docs/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [Mozilla Web Security Guidelines](https://infosec.mozilla.org/guidelines/web_security)

---

## 👤 Author

**Future Interns — Cybersecurity Track**  
Program: Cybersecurity Internship 2026  
Task: Vulnerability Assessment Report (Task 1)

---

*This project is for educational purposes only. Always get written authorization before testing any website.*
