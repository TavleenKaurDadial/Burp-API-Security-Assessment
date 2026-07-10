# Burp API Security Assessment

## Overview

This repository documents a practical API security assessment performed against **OWASP crAPI (Completely Ridiculous API)** using **Burp Suite Community Edition**.

The project demonstrates the identification and exploitation of common API security vulnerabilities by intercepting, modifying, and replaying HTTP requests. Each finding is mapped to the **OWASP API Security Top 10 (2023)** and the corresponding **OWASP API Security Top 10 (2025)** category where applicable.

Each vulnerability includes:

- Request and response evidence
- Burp Suite screenshots
- Vulnerability explanation
- Business impact
- CVSS v3.1 severity
- Remediation recommendations

---

## Objectives

- Perform hands-on API penetration testing using Burp Suite.
- Identify and validate common API security vulnerabilities.
- Map findings to the OWASP API Security Top 10.
- Demonstrate practical exploitation techniques.
- Document secure remediation practices.

---
## Project Architecture

![Architecture](/diagrams/architecture.png)

## Lab Setup

The vulnerable application used in this project is OWASP crAPI, deployed locally using Docker Desktop.

The environment simulates a modern microservices-based REST API application with multiple services and databases, making it suitable for testing authorization flaws such as BOLA, Broken Function Level Authorization, and Mass Assignment.

### Deployment

```bash
git clone https://github.com/OWASP/crAPI.git
cd crAPI/deploy/docker
docker compose up -d
```

The application was accessed locally at:

http://localhost:8888


## Technology Stack

| Technology | Purpose |
|------------|---------|
| Burp Suite Community Edition | API interception and manual security testing |
| OWASP crAPI | Deliberately vulnerable API application |
| Docker | Local deployment environment |
| HTTP/REST APIs | Target application |
| Git & GitHub | Version control and documentation |

---

## Repository Structure

```text
BURP-API-SECURITY-ASSESSMENT
│
├── findings/
│   ├── bola.md
│   ├── broken_authentication.md
│   ├── bfla.md
│   ├── mass_assignment.md
│   ├── excessive_data_exposure.md
│   ├── security_misconfiguration.md
│   ├── ssrf.md
|   ├── unauthenticated_access.md
│   └── unrestricted_resource_consumption.md
│
├── screenshots/
│
├── diagrams/
│
└── README.md
```

---

## Vulnerabilities Covered

| Vulnerability | OWASP API 2023 | OWASP API 2025 | Status |
|--------------|----------------|----------------|--------|
| Broken Object Level Authorization (BOLA) | API1 | API1 | ✅ |
| Broken Authentication | API2 | API2 | ✅ |
| Excessive Data Exposure | API3 | API3 | ✅ |
| Unrestricted Resource Consumption | API4 | API4 | ✅ |
| Broken Function Level Authorization (BFLA) | API5 | API5 | ✅ |
| Business Logic / Mass Assignment | API6 | API6 | ✅ |
| Server-Side Request Forgery (SSRF) | API7 | API7 | ✅ |
| Security Misconfiguration (NoSQL Injection) | API8 | API8 | ✅ |

---

## Skills Demonstrated

- API Security Testing
- Burp Suite Repeater
- HTTP Request Manipulation
- JWT Analysis
- Authorization Testing
- Business Logic Testing
- NoSQL Injection Testing
- Server-Side Request Forgery (SSRF)
- OWASP API Security Testing
- Docker-based Security Lab Setup
- Security Documentation & Reporting

---

## Reference

- OWASP crAPI
- OWASP API Security Top 10 (2023)
- OWASP API Security Top 10 (2025)

---

> **Disclaimer:** This project was conducted in a controlled laboratory environment using the intentionally vulnerable OWASP crAPI application for educational and defensive security purposes only.