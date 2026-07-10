# Excessive Data Exposure

## OWASP API Top 10

**API3:2023 – Broken Object Property Level Authorization**

**CVSS v3.1:** 6.5 (Medium)

---

## Description

Excessive Data Exposure occurs when an API returns more information than is required by the client. Instead of filtering sensitive properties on the server, the API exposes internal or confidential data that may assist an attacker in reconnaissance or further exploitation.

---

## Business Impact

- Disclosure of sensitive user information.
- Exposure of internal application properties.
- Increased attack surface through information leakage.
- Potential privacy and regulatory compliance issues.

---

## Evidence

### Challenge 4 – Sensitive User Information Disclosure

The community posts endpoint returned detailed author information, including the user's **email address**, **vehicle identifier**, **profile picture reference**, and additional internal metadata. This information is unnecessary for displaying public posts and increases the amount of sensitive data exposed to other users.

![Sensitive Data Exposure](../screenshots/Excessive%20Data%20Exposure/sensitive-user-data.png)

---

### Challenge 5 – Internal Video Property Disclosure

The video API exposed the internal **`conversion_params`** property used by the backend video processing pipeline. Internal processing parameters should remain server-side and never be returned to clients, as they reveal implementation details that may aid further attacks.

![Internal Video Property](../screenshots/Excessive%20Data%20Exposure/internal-video-property.png)

---

## Remediation

- Return only the fields required by the client.
- Use response DTOs instead of exposing internal objects.
- Remove internal application properties from API responses.
- Apply server-side response filtering based on user permissions.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI