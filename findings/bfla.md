# Broken Function Level Authorization (BFLA)

## OWASP API Top 10

**A01:2025 – Broken Access Control**

**API5:2023 – Broken Function Level Authorization**

**CVSS v3.1:** 8.8 (High)

---

## Description

Broken Function Level Authorization (BFLA) occurs when an API fails to enforce authorization checks on privileged functions. An attacker with a low-privileged account can directly invoke administrative endpoints and perform actions that should be restricted to administrators.

---

## Business Impact

- Unauthorized execution of administrative functions.
- Deletion or modification of resources belonging to other users.
- Loss of data integrity and availability.
- Increased risk of privilege escalation and administrative account abuse.

---

## Evidence

### Challenge 7 – Delete Another User's Video

The **Alpha** user intercepted a request in Burp Suite and directly accessed the **admin-only** endpoint:

```http
DELETE /identity/api/v2/admin/videos/7
```

Although the video belonged to **Beta**, the API accepted the request using Alpha's authenticated session and returned **HTTP 200 OK**, successfully deleting another user's video. This demonstrates that the endpoint lacked proper function-level authorization checks.

![Delete Video](../screenshots/Broken%20function%20level%20authorization/delete_video.png)

---

## Remediation

- Enforce role-based access control (RBAC) on all privileged endpoints.
- Validate user roles on the server before executing administrative functions.
- Deny access to non-administrative users with **403 Forbidden**.
- Regularly review and test authorization rules for privileged API endpoints.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI