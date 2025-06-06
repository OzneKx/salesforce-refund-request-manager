# ⚙️ Trigger & Apex Logic – Refund Request Manager

## 📌 Trigger: `RefundRequestTrigger`

### When:

* After Insert on `Refund_Request__c`

### What it does:

* Calls helper class to log refunds above \$5000 into a separate audit object.

### Code Snippet

```apex
trigger RefundRequestTrigger on Refund_Request__c (after insert) {
    if (Trigger.isAfter && Trigger.isInsert) {
        RefundRequestHelper.logHighValueRefunds(Trigger.new);
    }
}
```

---

## 👨‍💻 Helper Class: `RefundRequestHelper`

### Purpose

Separate the logic from the trigger for testability and maintainability.

### Key Method

```apex
public class RefundRequestHelper {
    public static void logHighValueRefunds(List<Refund_Request__c> refunds) {
        List<High_Value_Refund__c> logs = new List<High_Value_Refund__c>();
        for (Refund_Request__c r : refunds) {
            if (r.Amount__c > 5000) {
                logs.add(new High_Value_Refund__c(
                    Refund_Reference__c = r.Id,
                    Amount__c = r.Amount__c,
                    Reason__c = r.Reason__c,
                    Logged_Date__c = Date.today()
                ));
            }
        }
        if (!logs.isEmpty()) {
            insert logs;
        }
    }
}
```

### Design Benefits

* Separation of concerns
* Easier to reuse and extend logic
* Easier to write focused unit tests
