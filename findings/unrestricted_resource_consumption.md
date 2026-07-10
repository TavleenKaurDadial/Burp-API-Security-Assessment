# Unrestricted Resource Consumption

## OWASP API Top 10

**API4:2025 – Unrestricted Resource Consumption**

**API4:2023 – Unrestricted Resource Consumption**

**CVSS v3.1:** 6.5 (Medium)

---

## Description

Although not an official crAPI challenge, this test demonstrates how APIs that perform resource-intensive operations without proper rate limiting or request validation can be abused. Repeated requests to expensive endpoints may lead to excessive server resource consumption and denial-of-service conditions.

---

## Business Impact

- Increased CPU and memory utilization.
- Degraded API performance for legitimate users.
- Potential denial-of-service through request flooding.
- Increased infrastructure and operational costs.

---

## Evidence

### Contact Mechanic API Resource Consumption Test

The **Contact Mechanic** endpoint was repeatedly invoked using valid requests. Each request triggered backend processing and generated a new mechanic report while returning **HTTP 200 OK**. Since no request throttling or rate limiting was enforced, the endpoint could be repeatedly abused to consume backend resources.

![Unrestricted Resource Consumption](../screenshots/Unrestricted%20Resource%20Consumption/unrestricted_resource_consumption.png)

---

## Remediation

- Implement API rate limiting and request throttling.
- Restrict repeated requests from the same user or IP.
- Apply quotas for resource-intensive operations.
- Monitor abnormal request patterns and trigger alerts.
- Introduce CAPTCHA or cooldown periods where appropriate.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI