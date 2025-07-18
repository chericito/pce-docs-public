---
title: Account Validation and Verification
excerpt: >-
  Ensure bank account accuracy and reduce return risk with PCE’s robust
  validation methods: instant EWS, prenotes, and micro-deposits.
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

Before initiating any ACH debit, it’s critical to confirm that the customer’s bank account is valid, open, and can receive transactions. PCE offers three complementary verification methods—Instant EWS, Prenotification, and Micro-deposits—so you can choose the right balance of speed, coverage, and user experience for your application.

**In this guide you’ll learn**

* How each verification method works and when to use it  
* The trade-offs between speed, coverage, and cost  
* Best practices for handling failures and timeouts  

### Prerequisites & limitations

* An active PCE merchant account with ACH debit permissions  
* Accurate routing and account numbers provided by the customer  
* Instant EWS requires Early Warning Services connectivity (limited to participating banks)  
* Prenotes introduce a 2-day delay; micro-deposits introduce a 1–2 day delay  

# Feature Table

| Feature                    | Description                                                                    |
| -------------------------- | ------------------------------------------------------------------------------ |
| Instant EWS Verification   | Real-time account status, ownership, and negative-history check via EWS        |
| Prenotification (Prenote)  | Zero-dollar test ACH entry to validate routing and account numbers over 2 days |
| Micro-deposit Verification | Two small random credits (\<$1) sent to the account; customer confirms amounts |

# Key details

## [Instant EWS Verification](doc:pce-docs-ach-instant-ews-verification)

Perform a real-time lookup against Early Warning Services to confirm that the account is active, owned by the customer, and free of negative history. Ideal for high-volume consumer apps that require instant onboarding with minimal friction.  

## [Prenotification (Prenote)](doc:pce-docs-ach-prenotification)

Send a zero-dollar ACH entry to test the routing and account numbers. The receiving bank must return invalid prenotes within two business days; if no return is received, the account is marked valid. Use when you need 100% bank coverage and can tolerate a short delay.  

## [Micro-deposit Verification](doc:pce-docs-ach-micro-deposit-verification)

Issue two small, random credit amounts to the customer’s account. After 1–2 business days, the customer enters these amounts in your app to prove access. Once confirmed, PCE debits the same amounts back. Provides universal bank support at the cost of extra latency and user effort.