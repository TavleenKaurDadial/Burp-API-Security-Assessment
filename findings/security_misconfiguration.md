# Security Misconfiguration (NoSQL Injection)

## OWASP API Top 10

**A02:2025 Security Misconfiguration / A05:2025 Injection**

**API8:2023 – Security Misconfiguration**

**CVSS v3.1:** 8.6 (High)

---

## Description

Security Misconfiguration occurs when an application accepts untrusted input without proper validation or securely configured database queries. In this challenge, the API was vulnerable to a NoSQL Injection that allowed arbitrary database operators to be supplied in place of the expected coupon code.

---

## Business Impact

- Unauthorized disclosure of valid coupon codes.
- Potential financial loss through unauthorized coupon redemption.
- Exposure of sensitive business data.
- Increased risk of further database enumeration.

---

## Evidence

### Challenge 12 – Retrieve Valid Coupon Codes using NoSQL Injection

The attacker replaced the expected string value for **`coupon_code`** with the NoSQL operator:

```json
{
  "coupon_code": {
    "$ne": null
  }
}
```

Instead of rejecting the malformed input, the API returned **HTTP 200 OK** along with a valid coupon code (**TRAC075**) and its associated value, demonstrating a successful NoSQL Injection.

![NoSQL Injection](../screenshots/Security%20misconfiguration%20injection/nosql-injection.png)

---

## Remediation

- Validate and sanitize all user input.
- Reject NoSQL operators supplied by clients.
- Use parameterized database queries or ORM protections.
- Apply strict input schema validation.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI