---
title: Addenda Records
excerpt: >-
  Learn how PCE handles ACH addenda records—adding up to 80 characters of
  supplemental info for PPD, CCD, WEB, or TEL entries—to improve reconciliation
  and reference clarity.
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

Addenda records let you append extra information—like invoice numbers or customer IDs—to ACH entries.

**In this guide you’ll learn**

* What addenda records are and when to use them
* Character limits and formatting rules
* How PCE’s single-line support compares to CTX multi-addenda

### Prerequisites & Limitations

* ACH origination enabled on your PCE merchant account
* Supported only for PPD, CCD, WEB, and TEL entries
* Single addenda record per transaction, max 80 alphanumeric characters

# Compliance / Regulation Mandates

* **Nacha Requirements:** Every addenda record must follow Nacha’s formatting rules (80-character maximum, ASCII text).
* **Data Retention:** Retain addenda content in your records for at least 2 years to support audits and dispute resolution.
* **Privacy & Security:** Ensure any sensitive info in addenda (e.g., customer IDs) complies with GDPR/CCPA and is masked as needed.

# Feature Table

| Feature                 | Description                                                          |
| ----------------------- | -------------------------------------------------------------------- |
| **Single-Line Addenda** | One addenda record per PPD/CCD/WEB/TEL entry, up to 80 characters    |
| **Reconciliation Aid**  | Include invoice, PO, or customer reference numbers for easy matching |
| **CTX Limitation**      | CTX multi-addenda (up to 9,999 records) is not supported on PCE      |

# Key Details

An **addenda record** is a supplemental data record attached to an ACH entry, providing additional context for the payment.

* **Single‐Line Support:** PCE allows exactly one addenda record per PPD, CCD, WEB, or TEL transaction.
* **Character Limit:** Each addenda record may contain up to **80 alphanumeric characters** (ASCII).
* **Use Cases:**

  * Embedding an **invoice number** or **purchase order** for downstream reconciliation
  * Passing a **customer account ID** to help the Receiver match the debit to internal systems
  * Including a brief **note** or **reference** that clarifies payment purpose
* **CTX Limitation:** Because CTX (Corporate Trade Exchange) isn’t supported on PCE, multi-line or multiple addenda records per entry aren’t possible. Clients requiring extensive remittance data should use a CTX-capable solution or split payments into multiple entries.
