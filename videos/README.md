# Demo Videos – Restaurant Kiosk Security Assessment

This folder contains demonstration videos highlighting key findings and controlled exploits from the **Restaurant Kiosk Security Assessment** project. Each video showcases a specific vulnerability or mitigation technique observed during field research and DVREST testing.

---

## Vulnerability Overview

| Vulnerability | Impact | Demonstration |
|---|---|---|
| Tablet UI Escape | Access to backend kiosk configuration menus | Video Demo |
| BOLA / IDOR | Unauthorized modification of another user's profile | Video Demo |
| Mass Assignment | Privilege escalation via injected request fields | Video Demo |

---

## 1. Field Observation – Tablet UI Escape

**Description:**  
Demonstrates a non-invasive UI escape observed on a restaurant tablet-based kiosk. Rapid inputs allowed navigation outside the intended ordering interface and into backend configuration menus.

During the observation, the interface exposed internal configuration areas including:

- Table assignment settings  
- Cloud synchronization status  
- Editable system fields

No data was modified during testing. The observation was conducted strictly as a **passive security assessment** following ethical research practices.

**Watch Video:**  
[Field Observation – UI Escape](https://drive.google.com/file/d/1Qbg-NvQKbxuWqFKQUwF0kJ8g4d5qxNnK/view?usp=sharing)

---

## 2. BOLA / IDOR Exploit & Remediation

**Description:**  
Shows a low-privileged user (`test1`) exploiting the API to update another user's profile information. The API endpoint accepted a username parameter but did not verify that the authenticated user owned the target account.

This allowed **horizontal privilege abuse**, where one user could modify another user's data.

**Key Takeaways**

- **Exploit:** A crafted PUT request successfully updated another user's profile.
- **Security Issue:** **Broken Object Level Authorization (BOLA)**, a form of **Broken Access Control** in the OWASP Top 10.
- **Impact:** Unauthorized modification of user data.

### Remediation

The endpoint was patched to enforce ownership validation before allowing updates.

```python
if db_user.id != current_user.id:
    raise HTTPException(
        status_code=status.HTTP_403_FORBIDDEN,
        detail="You are not authorized to update this profile."
    )
```

This ensures that users may only update their own profile records.

**Validation:**  
After implementing the fix, unauthorized modification attempts return **HTTP 403 Forbidden**, preventing horizontal privilege escalation.

**Watch Video:**  
[BOLA / IDOR Exploit & Remediation](https://drive.google.com/file/d/1KEzV4DpCJUj78HWZL5kMSBIYGq9vyiST/view?usp=sharing)

---

## 3. Mass Assignment / Authorization Bypass Exploit & Remediation

**Description:**  
Demonstrates a **Mass Assignment vulnerability** where the API accepted unexpected fields in the request body. Because the model allowed extra attributes, a regular user could inject `"role": "Chef"` and grant themselves administrative privileges.

**Key Takeaways**

- **Exploit:** Injecting `"role": "Chef"` into a PATCH request granted unauthorized admin privileges.
- **Security Issue:** **Mass Assignment**, where APIs automatically bind request fields to internal model attributes.
- **Impact:** Privilege escalation from regular user to administrator.

### Remediation

The endpoint was secured using three defensive controls.

#### 1. Field Whitelisting

Only approved profile fields are allowed to be updated.

```python
class UserUpdate(BaseModel):
    first_name: str
    last_name: str
    phone_number: str
```

#### 2. Ignore Unset Fields

```python
update_data = user_update.dict(exclude_unset=True)
```

This ensures only fields explicitly provided in the request are processed.

#### 3. Reject Unexpected Fields

```python
class Config:
    extra = Extra.forbid
```

This blocks unexpected attributes (such as `role`) before they reach application logic.

**Validation:**  
After these protections were implemented, requests containing unauthorized attributes return **HTTP 422 – Unprocessable Entity**, preventing privilege escalation.

**Watch Video:**  
[Mass Assignment Exploit & Remediation](https://drive.google.com/file/d/1mqjwW0kM-LAlXG1alalJXz83cb8g9NFP/view?usp=sharing)

---

## Notes

- All demonstrations were conducted in a **controlled local DVREST environment**.
- No live production systems were accessed or impacted.
- Videos are hosted externally to maintain repository performance and accessibility.
- This folder supplements the full research documentation and demonstrates practical application of **API security testing**, **secure coding remediation**, and **ethical vulnerability research**.
