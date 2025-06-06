# 🔄 Flows – Refund Request Manager

## 📥 Flow: Notify Manager if Refund > \$1000

### Type

* **Record-Triggered Flow**
* Triggered **after insert** on `Refund_Request__c`

### Entry Criteria

* `Amount__c > 1000`

### Elements

1. **Get Records (User)** – Find Manager's User record.
2. **Send Email** – Uses Email Alert to notify Manager.

### Outcome

If the refund exceeds \$1000, an automated email is sent to a designated Manager.

## 💬 Why Flow?

Declarative automation is preferred for simple business logic. Here, sending an email based on a field value is clear, visual, and maintainable.

> Included in screenshots folder: `docs/screenshots/flow-email-manager.png`
