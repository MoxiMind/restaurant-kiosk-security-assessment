# Restaurant Kiosk Security Assessment
**Professional Security Research & Vulnerability Demonstration**

This project demonstrates a comprehensive security assessment of **tablet-based self-service kiosks (TBSSKs)** in the casual dining industry. It focuses on three high-impact vulnerabilities:

1. **Tablet UI Escape** – Users bypass the kiosk interface to access system settings.  
2. **Broken Object Level Authorization (BOLA / IDOR)** – Users can modify other users’ data due to missing server-side ownership checks.  
3. **Mass Assignment / Authorization Bypass** – Users can escalate roles (e.g., Customer → Admin/Chef) via unvalidated API fields.

---

## Key Features

- **Real-World Observations** – Non-invasive field testing of kiosk interfaces.  
- **Ethical API Exploitation** – Controlled testing in **Damn Vulnerable RESTaurant (DVREST)**.  
- **Validated Remediation** – Demonstrated fixes for BOLA and Mass Assignment vulnerabilities with strict field-level validation.  
- **Low-Cost, High-ROI Security** – Targeted mitigations prevent multi-million-dollar breach exposure.  
- **Compliance Alignment** – Remediations align with **PCI DSS**, **NIST SP 800-53**, and **OWASP Top 10** standards.

---

## Tools & Environment

- **DVREST (Damn Vulnerable RESTaurant)** – Fully intentionally vulnerable sandbox designed for safe testing of REST APIs.  
  - Supports **endpoint manipulation** and live response monitoring.  
  - Demonstrates common high-risk vulnerabilities, including **BOLA/IDOR and Mass Assignment**, in a controlled environment.  

> All testing, exploitation, and remediation validation was performed directly within DVREST—no external tools were required.

---

## Why This Project Matters

Tablet-based self-service kiosks are widely adopted but often poorly secured, exposing restaurants to:

- Theft of sensitive customer data (PII & payment info)  
- Unauthorized administrative control  
- Regulatory fines and reputational damage  

This research shows that **small, targeted code changes and policy enforcement** can eliminate major vulnerabilities, making it relevant for cybersecurity professionals, software engineers, and risk managers.  

---

## Ethical Statement

- Field testing was **non-invasive**; no production systems were modified.  
- All API testing was performed in a **sandboxed DVREST environment**, eliminating risk to real-world systems.  
- Vulnerabilities were responsibly documented and remediated to demonstrate **secure best practices**.
