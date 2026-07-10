# Server-Side Request Forgery (SSRF)

## OWASP API Top 10

**A01:2025 Broken Access Control**

**API7:2023 – Server Side Request Forgery**

**CVSS v3.1:** 8.6 (High)

---

## Description

Server-Side Request Forgery (SSRF) occurs when an application fetches resources from a user-controlled URL without proper validation. An attacker can force the server to initiate requests to external or internal systems, potentially exposing sensitive services and data.

---

## Business Impact

- Unauthorized access to internal services.
- Information disclosure from trusted backend systems.
- Potential lateral movement within internal networks.
- Increased risk of cloud metadata and infrastructure compromise.

---

## Evidence

### Challenge 11 – Make crAPI Send an HTTP Request

The attacker modified the **`mechanic_api`** parameter in the **Contact Mechanic** request to point to:

```text
https://www.google.com
```

The application processed the supplied URL and returned **Google's HTTP response** within the API response. This confirms that the backend server performed the outbound request on behalf of the attacker, demonstrating a Server-Side Request Forgery vulnerability.

![SSRF](../screenshots/Server%20Side%20Request%20Forgery/ssrf.png)

---

## Remediation

- Maintain an allowlist of trusted outbound destinations.
- Reject user-controlled URLs whenever possible.
- Restrict outbound network access from backend services.
- Validate URL schemes, hosts, and IP ranges before making requests.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI