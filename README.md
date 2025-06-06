# 🧾 Salesforce Project – Refund Request Manager

This project simulates a real-world refund request system using Salesforce automation, logic, and reporting. It is part of my Salesforce Developer portfolio.

---

## 🔧 Features

- Custom object: `Refund_Request__c`
- Record-Triggered Flow: email sent to manager if refund > $1000
- Apex Trigger + Helper Class: logs high-value refunds (> $5000)
- Validation Rules for clean input data
- Report showing audit logs
- Apex Test Class with 100% coverage

---

## 📁 Project Structure

```
salesforce-refund-project/
├── README.md
├── docs/
│   ├── overview.md         ← Business context, user stories
│   ├── data-model.md       ← All custom objects & field details
│   ├── flows.md            ← Flow setup, structure and logic
│   ├── trigger.md          ← Trigger logic & helper breakdown
│   ├── tests.md            ← Test class details and assertions
│   └── screenshots/        ← Screens from the app
```

---

## 📄 Documentation Overview

### 🧠 Purpose

To automate and enforce a refund request process. It ensures:
- Refunds are validated and contain all required information
- High-value refunds are monitored for auditing
- Managers are alerted automatically

### 🧪 Business Use Case

"As a company, we want to allow clients to submit refund requests and have those:
- Automatically validated
- Escalated when needed
- Logged when significant for compliance"

### 👤 Actors

- **Customer (User)** – submits refund request
- **Manager** – receives email for high-value refunds
- **Admin/Backoffice** – reviews audit reports of flagged refunds

### 📸 Screenshots

Stored under `docs/screenshots/`:
- Flow structure
- Trigger execution
- Object and field settings
- Test class execution result
- Sample report

### 📊 Manual Test Scenarios

| Scenario                      | Input                             | Expected Outcome                                             |
|------------------------------|-----------------------------------|--------------------------------------------------------------|
| Valid Refund < $1000         | Amount: 900                       | Record created. No email. No audit log.                     |
| Refund > $1000, < $5000      | Amount: 3000                      | Email sent to manager. No audit log.                        |
| Refund > $5000               | Amount: 6000                      | Email sent + log created in `High_Value_Refund__c`         |
| Invalid refund (zero amount) | Amount: 0                         | Blocked. Error from Validation Rule.                        |
| Missing Reason               | Empty Reason field                | Blocked. Error from Validation Rule.                        |
| Apex Test Class              | Run `RefundRequestTriggerHandlerTest` | Asserts all logic. Coverage: 100%.                        |

---

## ✅ Why This Project Is Valuable

- Demonstrates ability to combine declarative (Flow, Validation Rules) and programmatic (Trigger, Apex) tools.
- Follows good practices (separation of logic, helper classes, test coverage).
- Has a real-world scenario aligned with enterprise needs (auditing, approval, automation).
