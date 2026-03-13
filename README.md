## Restaurant Kiosk Security Assessment

A security assessment of a restaurant tablet kiosk system, combining real-world interface observation with controlled API vulnerability testing and remediation.

This project demonstrates common application security issues observed in modern kiosk-style systems and REST APIs. The research combines **field observation**, **controlled vulnerability testing**, and **secure coding remediation** to illustrate how these weaknesses can be identified and mitigated.

---

## Security Findings

This assessment documents several security observations and vulnerability demonstrations discovered during testing. Findings were validated in a controlled **DVREST API environment** to safely demonstrate exploitation scenarios and remediation techniques.

### Summary of Findings

| Category | Vulnerability | Impact | Demonstration |
|---|---|---|---|
| Kiosk Interface | Tablet UI Escape | Access to internal kiosk configuration menus | [View Demo](videos/README.md#1-field-observation--tablet-ui-escape) |
| API Security | Broken Object Level Authorization (BOLA / IDOR) | Unauthorized modification of another user's profile | [View Demo](videos/README.md#2-bola--idor-exploit--remediation) |
| API Security | Mass Assignment | Privilege escalation via injected request fields | [View Demo](videos/README.md#3-mass-assignment--authorization-bypass-exploit--remediation) |

Detailed demonstrations of each finding are available in the project’s video documentation.

➡ **[View All Demonstration Videos](videos/README.md)**

---

## Research Methodology

The assessment followed a structured security testing approach similar to common **application security review workflows**.

### 1. Field Observation

Initial testing involved passive interaction with a tablet-based restaurant kiosk interface. Rapid user input sequences allowed navigation outside the intended ordering interface and exposed backend configuration menus.

### 2. Controlled Vulnerability Testing

To safely reproduce and analyze vulnerabilities, a **local DVREST API environment** was used. This allowed testing of authentication and authorization weaknesses without interacting with live production systems.

### 3. Vulnerability Analysis

Two primary API security issues were identified and reproduced:

- **Broken Object Level Authorization (BOLA / IDOR)**  
  A user could modify another user's profile due to missing ownership validation.

- **Mass Assignment**  
  The API accepted unexpected request fields, allowing a regular user to escalate privileges by injecting role attributes.

### 4. Remediation Implementation

Secure coding fixes were implemented to mitigate the vulnerabilities:

- Server-side object ownership validation
- Field whitelisting for update operations
- Rejection of unexpected input fields
- Defensive API model configuration

### 5. Validation Testing

After applying remediation, exploitation attempts were repeated to verify that the vulnerabilities were successfully mitigated.

---

## Ethical Considerations

- All demonstrations were conducted in a **controlled local environment**.
- No production systems were accessed or modified.
- Field observations were **non-invasive** and did not alter system data.

This project is intended solely for **educational and security research purposes**.

---

## Project Documentation

| Section | Description |
|---|---|
| `videos/` | Demonstration videos of vulnerabilities and remediation |
| `README.md` | Project overview and research summary |

➡ **[View Video Demonstrations](videos/README.md)**

---

## Skills Demonstrated

- Application Security Testing  
- API Security Analysis  
- Vulnerability Reproduction  
- Secure Coding Remediation  
- Authorization Control Design  
- Security Documentation
