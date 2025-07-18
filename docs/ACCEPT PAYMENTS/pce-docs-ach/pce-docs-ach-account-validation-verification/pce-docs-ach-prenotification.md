---
title: Prenotification
excerpt: >-
  Quickly verify ACH account and routing numbers with a zero-dollar “prenote”
  entry to ensure live transactions will succeed.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Overview

Prenotification (prenote) sends a \$0 ACH entry to validate account details before live debits. The customer’s bank must return any failures within two business days; absent a return, the account is deemed valid.

**In this guide you’ll learn**

* How prenotes work and why they’re required
* Timeline and behavior of prenote returns
* When to use prenotes vs. instant or micro-deposit methods

### Prerequisites & Limitations

* Merchant profile must have prenote capability enabled
* Requires accurate account and routing numbers at submission
* Introduces a minimum two-business-day delay before live debits

# Compliance / Regulation Mandates

* **Nacha Rules:** RDFIs must return invalid prenotes within two business days.
* **Mandate Validation:** Prenote serves as a supplemental authorization check under Nacha Operating Rules.
* **Good-Funds Model:** Prenotes carry no dollar value but confirm routing path and account status.

# Feature Table

| Feature               | Description                                                                |
| --------------------- | -------------------------------------------------------------------------- |
| Zero-Dollar Entry     | Send a \$0 ACH debit to test account/routing validity                      |
| Automated Return      | Platform auto-processes any prenote return codes within two business days  |
| Validity Confirmation | If no return is received by day three, the account is cleared for live use |

# Key Details

A **prenote** is a special ACH entry with an amount of \$0, sent solely to verify that the account and routing numbers are correct. It does **not** move funds.

* **Submission:** Initiate a prenote just like a normal debit, specifying `"amount": 0`.
* **Return Window:** The Receiving Depository Financial Institution (RDFI) must return invalid prenotes (e.g., closed account, invalid routing) within **two business days**.
* **Success Criteria:** If no return message is received by the end of the second business day, treat the account as valid and proceed with live debits.
* **Failure Handling:** Any prenote return (e.g., R03 – No Account, R04 – Invalid Account Number, R02 – Account Closed) should trigger automated alerts or require manual intervention to correct customer details.

**When to Use Prenotes**\
Use prenotes when you need broad bank coverage and cannot rely on instant EWS verification. Ideal for B2B scenarios where a two-day setup window is acceptable and cost per check is minimal.

> **Integration Tip**

> Schedule prenotes early in your onboarding flow and implement fallbacks (micro-deposits) if no response is received within three business days, ensuring you don’t block customers indefinitely.
