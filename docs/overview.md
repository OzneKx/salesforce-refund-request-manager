# 📘 Overview – Refund Request Manager

## 🎯 Objective

Create an automated refund management system that allows clients to request a refund, validates their input, and alerts managers or logs critical data based on refund amount.

## 👥 Actors

* **Client**: Submits a refund request.
* **Manager**: Receives email notification for high-value refunds.
* **Admin**: Monitors refund trends and audits logs.

## 📚 User Story

"As a client, I want to submit a refund request with a reason and amount so that my refund can be processed efficiently and reviewed if necessary."

## 🧠 Business Rules

* The refund amount must be greater than 0.
* A reason must always be provided.
* Refunds over \$1000 trigger a notification to a manager.
* Refunds over \$5000 are flagged and stored in an audit log.

## 🔍 Goals

* Automate communication and logging.
* Ensure clean and complete data entry.
* Keep the system scalable and testable.

## 🧩 Value

This project simulates a real enterprise process and demonstrates how to use Salesforce tools for automation, validation, and custom logic with separation of concerns.
