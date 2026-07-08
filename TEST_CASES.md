# Manual Test Suite: User Authentication System

## System Under Test (SUT)
Web Application Login & Session Management

---

### 🧪 Test Case: TC001
* **Feature:** Login
* **Type:** Positive | **Priority:** High
* **Scenario:** Successful authentication with valid credentials
* **Steps to Reproduce:**
  1. Navigate to `/login`
  2. Enter valid email and password
  3. Click "Submit"
* **Expected Result:** User redirected to `/dashboard` with valid session token.

---

### 🧪 Test Case: TC002
* **Feature:** Login
* **Type:** Negative | **Priority:** High
* **Scenario:** Unregistered email validation
* **Steps to Reproduce:**
  1. Navigate to `/login`
  2. Enter unregistered email
  3. Enter valid password syntax
  4. Click "Submit"
* **Expected Result:** Error message displays `"Invalid credentials"`. No disclosure of email existence.

---

### 🧪 Test Case: TC003
* **Feature:** Security
* **Type:** Security | **Priority:** Critical
* **Scenario:** SQL Injection attempt in login fields
* **Steps to Reproduce:**
  1. Navigate to `/login`
  2. Enter `' OR '1'='1` in email field
  3. Enter arbitrary password
  4. Click "Submit"
* **Expected Result:** Input sanitized; authentication rejected with standard error.

---

### 🧪 Test Case: TC004
* **Feature:** Session
* **Type:** Edge Case | **Priority:** Medium
* **Scenario:** Account lockout policy after repeated failures
* **Steps to Reproduce:**
  1. Enter valid email with incorrect password 5 consecutive times
* **Expected Result:** Account temporarily locked for 15 minutes; notification sent.

---

### 🧪 Test Case: TC005
* **Feature:** Input
* **Type:** UI/Frontend | **Priority:** Low
* **Scenario:** Password field masking & toggle
* **Steps to Reproduce:**
  1. Enter password string
  2. Toggle visibility icon
* **Expected Result:** Password masked by default (`•••••`); plain text toggles correctly.
