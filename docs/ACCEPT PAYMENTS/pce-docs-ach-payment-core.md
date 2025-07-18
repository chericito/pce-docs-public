---
title: 'ACH: Payment Core'
excerpt: >-
  Manage ACH debit initiation, validation, returns, and refunds with PCE’s
  robust ACH Payment Core features.
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

This page outlines PCE’s ACH Payment Core suite, empowering you to originate, modify, and reconcile ACH debits, handle exceptions, and process refunds. Whether you need single-entry debits or high-volume NACHA file uploads, PCE delivers the controls and compliance you require.

**In this guide you’ll learn**

* How to originate and modify ACH debit transactions  
* The role of SEC codes and addenda records in compliance and reconciliation  
* Best practices for handling ACH returns, reversals, and refunds  

### Prerequisites & limitations

* Active merchant account with ACH debit capabilities  
* Nacha Operating Rules compliance for all entries  
* Bank and network agreements for ACH origination, returns, and refunds  

# Feature table

| Feature              | Description                                                       |
| -------------------- | ----------------------------------------------------------------- |
| ACH Debit Initiation | Originate one-off or recurring debits via REST API or NACHA files |
| SEC Codes            | Classify entries with PPD, CCD, WEB or TEL codes for compliance   |
| Addenda Records      | Attach single-line remittance details to simplify reconciliation  |
| Modify Payments      | Update or cancel scheduled debits before the ACH cutoff           |
| Returns & Reversals  | Handle bank-initiated returns and originator-initiated reversals  |
| Refunds              | Issue full or partial ACH credits to customers                    |

# Key details

## [ACH Debit Initiation](doc:pce-docs-ach-debit-initiation)

Create and schedule ACH debit entries—one-off or recurring—by referencing a verified external account. Supports next-day and same-day processing, with clear cutoff rules.

## [SEC Codes](doc:pce-docs-ach-sec-codes)

Select the correct Standard Entry Class (PPD, CCD, WEB, TEL) to define transaction type, authorization method, and return rules under Nacha.

## [Addenda Records](doc:pce-docs-ach-addenda-records)

Include a single 80-character addenda record per entry to carry invoice numbers, customer IDs, or other remittance details.

## [Modify Payments](doc:pce-docs-ach-modify-payments)

Before the ACH cutoff, update amount or purpose of a Scheduled debit or cancel it entirely; once processing begins, origination reversals must be used.

## [Returns & Reversals](doc:pce-docs-ach-returns-reversal)

Automatically consume RDFI return notifications (R-codes) and initiate originator reversals within Nacha timelines to correct errors or duplicates.

## [Refunds](doc:pce-docs-ach-refunds)

Push ACH credits for full or partial refunds after settlement, with settlement times of 3–5 business days and proper trace referencing to aid reconciliation.
