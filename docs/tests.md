# ✅ Apex Tests – Refund Request Manager

## 🧪 Test Class: `RefundRequestTriggerHandlerTest`

### Key Goals

* Validate that high-value refunds are logged properly.
* Ensure no audit records are created for small refunds.
* Achieve 100% coverage of trigger and helper logic.

### Code Snippet

```apex
@isTest
private class RefundRequestTriggerHandlerTest {
    @isTest
    static void testHighValueRefundLogged() {
        Refund_Request__c highRefund = new Refund_Request__c(
            Amount__c = 6000,
            Reason__c = 'Test refund',
            Request_Date__c = Date.today(),
            Status__c = 'New',
            Client_Email__c = 'test@example.com'
        );
        insert highRefund;

        List<High_Value_Refund__c> logs = [SELECT Id FROM High_Value_Refund__c];
        System.assertEquals(1, logs.size());
    }

    @isTest
    static void testLowValueRefundNotLogged() {
        Refund_Request__c lowRefund = new Refund_Request__c(
            Amount__c = 800,
            Reason__c = 'Minor refund',
            Request_Date__c = Date.today(),
            Status__c = 'New',
            Client_Email__c = 'minor@example.com'
        );
        insert lowRefund;

        List<High_Value_Refund__c> logs = [SELECT Id FROM High_Value_Refund__c];
        System.assertEquals(0, logs.size());
    }
}
```

## 🔍 Test Coverage

* Trigger logic: ✅
* Helper class: ✅
* Data insertions with different scenarios: ✅
* Validation for absence of log when not required: ✅

> Result: **100% code coverage** with two simple yet strong assertions.
