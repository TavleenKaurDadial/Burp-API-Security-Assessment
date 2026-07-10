# Unauthenticated Access

## OWASP API Top 10

**API2:2025 – Broken Authentication**

**API2:2023 – Broken Authentication**

**CVSS v3.1:** 8.6 (High)

---

## Description

The API exposes sensitive order information without validating whether the request is authenticated. An attacker can directly access protected resources by sending a request without a valid JWT token.

---

## Business Impact

- Unauthorized disclosure of customer order information.
- Exposure of payment and transaction details.
- Increased risk of data harvesting and privacy violations.
- Weak authentication controls may enable further attacks.

---

## Evidence

### Challenge 14 – Find an endpoint that does not perform authentication checks for a user.

The **Authorization** header was removed from the request before sending it to the API. Despite the request being unauthenticated, the server responded with **HTTP 200 OK** and returned the complete order details, including customer, product, and payment information.

![Unauthenticated Access](../screenshots/Unauthenticated%20Access/unauthenticated_access.png)

---

## Remediation

- Enforce authentication on all protected API endpoints.
- Reject unauthenticated requests with **401 Unauthorized**.
- Validate JWT tokens before processing requests.
- Apply centralized authentication middleware across all APIs.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI