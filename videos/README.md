# Demo Videos – Restaurant Kiosk Security Assessment

This folder contains demonstration videos showcasing key findings and controlled exploits from the **Restaurant Kiosk Security Assessment** project. Each video highlights a specific vulnerability or mitigation technique observed during field research and DVREST testing.

---

## 1. Field Observation – Tablet UI Escape
**Description:**  
Demonstrates the non-invasive UI escape observed on a restaurant tablet-based kiosk. Rapid inputs allowed access to backend settings, including table assignments, cloud update status, and editable fields. No data was modified during this observation, following strict ethical guidelines.  

**Watch Video:** [Field Observation – UI Escape](https://drive.google.com/file/d/1Qbg-NvQKbxuWqFKQUwF0kJ8g4d5qxNnK/view?usp=sharing)

---

## 2. BOLA / IDOR Exploit & Remediation
**Description:**  
Shows a controlled exploitation of **Broken Object Level Authorization (BOLA/IDOR)** using the Damn Vulnerable RESTaurant environment. A low-privilege user was able to modify another user’s profile data. The video also demonstrates the simple code remediation that enforces server-side ownership checks to prevent unauthorized access.  

**Watch Video:** [BOLA / IDOR Exploit & Remediation](https://drive.google.com/file/d/1KEzV4DpCJUj78HWZL5kMSBIYGq9vyiST/view?usp=sharing)

---

## 3. Mass Assignment / Authorization Bypass Exploit & Remediation
**Description:**  
Illustrates how a user with basic credentials could escalate privileges by sending unauthorized parameters (Mass Assignment) to their profile endpoint, effectively becoming an admin (“Chef”). The remediation shows whitelisting fields, enforcing `extra=forbid`, and returning a 422 error for unauthorized input.  

**Watch Video:** [Mass Assignment Exploit & Remediation](https://drive.google.com/file/d/1mqjwW0kM-LAlXG1alalJXz83cb8g9NFP/view?usp=sharing)

---

### Notes
- All demos were conducted in a **controlled, local DVREST environment**.  
- No live production systems were accessed or impacted.  
- Videos are linked externally to maintain repo performance and accessibility.  
- This folder serves as a supplement to the full research documentation and showcases practical application of API security and ethical vulnerability testing.
