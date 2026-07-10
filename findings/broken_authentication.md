# Broken Authentication

## OWASP API Top 10

**A07:2025 – Authentication Failures**

**API2:2023 – Broken Authentication**

**CVSS v3.1:** 9.1 (Critical)

---

## Description

Broken Authentication occurs when an API improperly validates a user's identity or authentication process, allowing attackers to impersonate other users or gain unauthorized access. In this challenge, the password reset workflow failed to securely validate user ownership before allowing a password change.

---

## Business Impact

- Unauthorized account takeover.
- Compromise of user credentials.
- Loss of confidentiality and account integrity.
- Increased risk of privilege escalation and unauthorized access.

---

## Evidence

### Challenge 3 – Reset Another User's Password

**Password Reset Request**

Using Burp Suite, the password reset request was intercepted and modified to target **Beta's** account. By supplying the victim's email address, a valid OTP, and a new password, the API accepted the request without enforcing sufficient ownership validation.

**Response**

The server returned **HTTP 200 OK** with the message **"OTP verified"**, confirming that the password reset request was successfully processed and the victim's password was changed.

![Password Reset](../screenshots/Broken%20Authentication/reset_password.png)

---

## Remediation

- Bind password reset tokens and OTPs to the intended user session.
- Ensure password reset requests can only be completed by the legitimate account owner.
- Generate cryptographically secure, single-use OTPs with short expiration times.
- Implement rate limiting and account lockout for repeated reset attempts.
- Log and monitor password reset events for suspicious activity.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI