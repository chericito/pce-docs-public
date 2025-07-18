---
title: Refunds
excerpt: >-
  Manage full and partial ACH refunds with PCE’s refund capabilities—covering
  workflows, timelines, and settlement dependencies.
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

This page explains how to issue refunds for ACH debits using PCE, from customer request through funds re-credit. You’ll learn about the end-to-end refund flow, timing expectations, and how to handle both full and partial refunds.

**In this guide you’ll learn**

* How to initiate an ACH credit refund via PCE
* Typical timelines and settlement prerequisites
* The differences between full and partial refunds

### Prerequisites & Limitations

* The original ACH debit **must have settled** (1–2 business days) before a refund can be initiated.
* Merchant must be enabled for ACH “push” credits.
* Refunds process in batch and cannot be expedited in real time.

# Compliance / Regulation Mandates

* **Nacha Operating Rules** govern all ACH credit (refund) entries.
* Refund initiation is only permitted after the original debit has posted and settled.
* Maintain sufficient “good funds” in your ODFI account to cover refunds.

# Feature Table

| Feature         | Description                                                           |
| --------------- | --------------------------------------------------------------------- |
| Full Refunds    | Return the entire original debit amount in one ACH credit entry       |
| Partial Refunds | Return a portion of the original amount (item-level or custom amount) |
| Timeline        | Refunds typically settle in **3–5 business days**                     |
| Settlement      | Can only be initiated **after** original debit settlement (1–2 days)  |

# Key Details

### Refund Workflow

1. **Customer Request**

   * Customer contacts merchant to request a refund for a settled ACH debit.
2. **Merchant Initiation**

   * Merchant calls the PCE ACH-credit (refund) API or submits a bulk file to create a “push” transaction.
   * The ODFI packages the refund as an ACH credit destined for the customer’s RDFI.
3. **Batch Processing**

   * Refund entries are sent in the next ACH batch to an ACH Operator (The Clearing House or Federal Reserve).
   * Operator sorts and routes the credit to the RDFI.
4. **Funds Deposited**

   * RDFI debits its reserve account and credits the customer’s account.

### Timelines and Dependencies

* **Refund Settlement:** 3–5 business days from initiation.
* **Cut-off Times:** Subject to each bank’s ACH transmission windows.
* **Original Settlement:** The initial debit must post and clear (1–2 business days) before refund initiation.

### Full vs. Partial Refunds

* **Full Refund**

  * The refund amount equals the original debit.
  * Use when canceling or reversing an entire transaction.
* **Partial Refund**

  * Refund only a portion of the original debit.
  * Ideal for item-level returns or prorated credits.
  * Supported via the same ACH-credit API—simply specify a lesser amount.

### Implementation Notes

* **API vs. Bulk Upload:**

  * Single refunds can be initiated via the PCE REST API.
  * High-volume refunds can be uploaded as NACHA-formatted files.
* **Reconciliation:**

  * Include the original transaction’s trace number or external reference in your addenda to link refunds to debits.
* **Error Handling:**

  * If RDFI rejects a refund (e.g., invalid account), PCE will surface a return file which you must handle per Nacha return rules.
