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

---

### 🧪 Test Case: TC006
* **Feature:** Input Validation
* **Type:** Boundary Value Analysis (BVA) | **Priority:** Medium
* **Scenario:** Password length boundary limits (Min: 8, Max: 16 characters)
* **Steps to Reproduce:**
  1. Navigate to `/register` or `/reset-password`
  2. Test Password with **7 chars** (Min - 1): Expect Error `"Password must be at least 8 characters"`
  3. Test Password with **8 chars** (Exact Min): Expect Success
  4. Test Password with **16 chars** (Exact Max): Expect Success
  5. Test Password with **17 chars** (Max + 1): Expect Error `"Password cannot exceed 16 characters"`
* **Expected Result:** System enforces exact length constraints at min/max limits without system errors.
