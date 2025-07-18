---
title: 'ACH: Risk and Fraud Shield'
excerpt: Initiate and manage ACH bank debits with PCE’s secure, compliant API suite.
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

This page provides a centralized view of PCE’s ACH risk and fraud controls, from real-time fraud prevention to automated blocks, velocity limits, and compliance safeguards. With these features you can minimize returns, prevent unauthorized activity, and manage your cash flow confidently.

**In this guide you’ll learn**

* How PCE automatically blocks high-risk accounts when return thresholds are exceeded  
* Best practices and system settings for fraud detection and statement clarity  
* The role of velocity limits and the “good funds” model in mitigating ACH risk  

### Prerequisites & limitations

* ACH origination, validation, and monitoring must be enabled on your PCE merchant account  
* External Accounts must be created and verified before debiting  
* Blocking and velocity controls apply per External Account, not per customer profile  

# Feature Table

| Feature                       | Description                                                                        |
| ----------------------------- | ---------------------------------------------------------------------------------- |
| Automated Debit Blocks        | Instantly block accounts breaching Nacha return-rate thresholds                     |
| Fraud Prevention              | Dynamic rules and best practices to detect and deter unauthorized ACH activity     |
| Good Funds Model              | Configurable clearing period to wait out the highest-probability return window     |
| Statement Descriptors         | Clear “Company Name” and “Description” fields to reduce friendly-fraud disputes    |
| Velocity Limits               | Per-account rules capping transaction count and volume over custom time intervals  |

# Key details

## [Automated Debit Blocks on High Return Rates](doc:pce-docs-ach-debit-blocks-on-high-return-rates)  
Learn how PCE tracks 60-day rolling return rates and blocks accounts for administrative or unauthorized return codes to prevent repeated failures.

## [Fraud Prevention](doc:pce-dos-ach-fraud-prevention)  
Implement clear naming conventions, dynamic descriptors, and entry controls to reduce ACH disputes and unauthorized returns.

## [Good Funds Model](doc:pce-docs-good-funds-model)  
Understand PCE’s default and configurable “good funds” clearing period, which holds funds until the most common return windows have passed.

## [Statement Descriptors](doc:pce-docs-ach-statement-descriptors)  
Configure concise “Company Name” and “Company Description” fields—within NACHA limits—to maximize customer recognition and minimize disputes.

## [Velocity Limits](doc:pce-docs-ach-velocity-limits)  
Set proactive per-account caps on transaction count and total dollar volume to mitigate large-scale fraud risks before they occur.