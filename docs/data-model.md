# 🧩 Data Model – Refund Request Manager

## 📦 Custom Object: `Refund_Request__c`

| Field Label   | Field Name         | Data Type   | Required | Description                                   |
| ------------- | ------------------ | ----------- | -------- | --------------------------------------------- |
| Refund Number | Name (Auto Number) | Auto Number | Yes      | Unique record ID. Format: RR-{0000}           |
| Amount        | Amount\_\_c        | Currency    | Yes      | Refund amount requested                       |
| Reason        | Reason\_\_c        | Text Area   | Yes      | Explanation provided by the client            |
| Request Date  | Request\_Date\_\_c | Date        | Yes      | Date the refund was requested                 |
| Status        | Status\_\_c        | Picklist    | Yes      | Values: New, Under Review, Approved, Rejected |
| Client Email  | Client\_Email\_\_c | Email       | Yes      | For communication or audit trail              |

## 🔁 Relationships

* This object is standalone.
* In a real-world extension, it could be related to `Case`, `Order`, or `Account` objects via Lookup fields.

## 🛡️ Validation Rules

* **Amount must be greater than 0**
* **Reason cannot be blank**
* **Request Date must be today or earlier**
