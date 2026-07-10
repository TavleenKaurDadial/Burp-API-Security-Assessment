# Business Logic Flaw using Mass Assignment

## OWASP API Top 10

**A06:2025 Insecure Design**

**API6:2023 – Unrestricted Access to Sensitive Business Flows**

**CVSS v3.1:** 7.5 (High)

---

## Description

Mass Assignment occurs when an API automatically binds user-controlled input to internal object properties without proper validation. An attacker can modify sensitive fields that should only be controlled by the application, bypassing intended business logic.

---

## Business Impact

- Circumvention of business rules.
- Unauthorized modification of sensitive object properties.
- Financial loss through manipulation of order workflows.
- Loss of application integrity and trust.

---

## Evidence

### Challenge 8 – Return an Item Without Following the Intended Workflow

The attacker first retrieved the order details to identify the current order status. The API returned the order in the **`return_pending`** state.

![Order Before](../screenshots/Business%20logic%20flaw%20using%20mass%20assignment/order-before.png)

The request was then modified by directly updating the order status to **`returned`** using a `PUT` request. The API accepted the user-supplied value and responded with **HTTP 200 OK**, indicating that the business workflow could be bypassed.

![Order After](../screenshots/Business%20logic%20flaw%20using%20mass%20assignment/order-after.png)

---

### Challenge 10 – Modify Internal Video Properties

The attacker updated the internal **`conversion_params`** field by sending a crafted `PUT` request. Although this property is intended for server-side video processing, the API accepted the modification and stored the attacker-controlled value, demonstrating a Mass Assignment vulnerability.

![Video Properties](../screenshots/Business%20logic%20flaw%20using%20mass%20assignment/video-properties.png)

---

## Remediation

- Explicitly whitelist fields that clients are allowed to modify.
- Reject updates to internal or server-managed properties.
- Enforce business workflow validation on the server.
- Separate user-facing DTOs from internal data models.

---

## Tools Used

- Burp Suite Community Edition
- Docker
- OWASP crAPI