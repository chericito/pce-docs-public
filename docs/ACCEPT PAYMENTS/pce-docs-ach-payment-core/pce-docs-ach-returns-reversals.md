---
title: Returns and Reversals
excerpt: >-
  Manage exception flows for ACH debits in PCE—understand RDFI‐initiated returns
  and Originator‐initiated reversals, their timing, reasons, and the new portal
  tools for processing them.
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

When ACH transactions fail or need correcting, PCE supports two mechanisms:

* **Returns:** RDFI‐initiated pulls when a debit can’t settle
* **Reversals:** Originator‐initiated undo entries for errors
* How to track, process, and reconcile both in the PCE portal

### Prerequisites & Limitations

* **ACH Originations Enabled:** ACH debit initiation must be active on your merchant profile.
* **Transaction History:** You must be able to view the original transaction in **PROCESSING** or **COMPLETED** status.
* **Return Timeframes:** RDFIs have strict deadlines (24 hrs for businesses, 60 days for consumers).
* **Reversal Window:** Originators can only reverse within 5 banking days of the original transaction.

# Compliance / Regulation Mandates

* **Nacha Operating Rules:** Govern both returns and reversals, including time limits and data formats.
* **Written Statements:** Required for certain return reasons (e.g., unauthorized or revoked authorizations).
* **Audit Trail:** All return and reversal requests must be logged and retained for at least 2 years.

# Feature Table

| Feature                       | Description                                                                           |
| ----------------------------- | ------------------------------------------------------------------------------------- |
| **ACH Returns**               | Automatic processing of RDFI‐initiated return files with standard return codes        |
| **ACH Reversals**             | Originator‐initiated undo entries created via the PayOps Portal or REST API           |
| **Portal Reversal Workflow**  | In-portal “Reversal” section to schedule and track reversal transactions              |
| **Return Matching & Ledgers** | Automatic matching of return files to original entries and creation of return ledgers |

# Key Details

Despite best efforts, not all ACH transactions complete successfully. PCE supports two primary exception mechanisms: **ACH Returns** (RDFI-initiated) and **ACH Reversals** (Originator-initiated).

---

### ACH Returns

An ACH return occurs when the Receiving Depository Financial Institution (RDFI) cannot post a debit and sends it back to the Originating Depository Financial Institution (ODFI). Returns must comply with Nacha rules and be initiated within the specified timeframes (typically within two banking days of settlement).

#### Return Reasons

| Code    | Reason                   | Description                                                                    |
| ------- | ------------------------ | ------------------------------------------------------------------------------ |
| **R01** | Insufficient Funds       | Available balance is insufficient to cover the debit entry.                    |
| **R07** | Authorization Revoked    | Receiver revoked previously granted authorization; written statement required. |
| **R10** | Unauthorized Transaction | Debit not authorized by Receiver; written statement required.                  |
| **R02** | Account Closed           | The previously active account has been closed.                                 |
| **R03** | No Account / Not Found   | Account format valid but not on file or not open.                              |
| **R04** | Invalid Account Number   | Account number structure is invalid.                                           |
| **R08** | Payment Stopped          | Receiver requested stop-payment on this entry.                                 |
| **R16** | Account Frozen           | Funds unavailable due to freeze or legal action.                               |

#### Consumer vs. Business Returns

* **Consumer Purpose Accounts:** RDFIs have up to **60 days** from settlement to return a consumer debit (most returns occur within 2 days).
* **Business Purpose Accounts:** RDFIs have **24 hours** from posting to return a business-to-business debit.

---

### ACH Reversals

An ACH reversal is initiated by the Originator to correct errors (e.g., wrong amount or duplicate entry). Reversals must adhere to Nacha guidelines:

* **Initiation Window:** Within **5 banking days** of the original transaction date.
* **Amount:** Must equal the full original debit amount.
* **Data:** Mirrors the original transaction fields and references it via the **Parent Transaction** field.

#### Legacy Reversal Process

Previously, PCE users contacted the PCE Payment Operations team to manually create and process reversals via ACH.com. These reversals did not generate ledgers in PCE, causing reconciliation gaps.

#### Enhanced Reversal Workflow

PCE now enables PayOps users (with the appropriate role) to initiate reversals directly from the portal:

* **Reversal Panel:** A new **Reversal** section on the transaction detail screen.
* **Collect Transactions:**

  * Can reverse entries in **PROCESSING** (once EED ACK2 received) and **COMPLETED** status.
  * Reversal is created in **SCHEDULED**; if reversing a PROCESSING entry, both complete in tandem.
  * The original collect remains in **COMPLETED**.
* **Send Transactions:**

  * Can reverse only **COMPLETED** entries.
  * A new reversal collect is created in **SCHEDULED**; the original send remains **COMPLETED**.

> When a reversal is initiated, PCE creates a transaction of type **REVERSAL**, matching the original amount and populating its **Parent Transaction** field. The reversal appears on both PayOps and PM portals.

#### REST API Enhancements

* Support for `type=REVERSAL` on the Transaction entity.
* Retrieve Transaction API exposes full reversal details.
* List Transactions API includes reversal entries.

#### Ledger Handling & Return Matching

* Reversals generate proper ledger entries in PCE.
* PCE consumes return files for reversal entries, matches them by Individual ID and trace number, and creates offsetting ledgers—leaving the reversal in **COMPLETED**.

#### Realization Interval

Reverse ACH debits (send → collect) are held for **4 business days** by default to mitigate return risk (configurable via PCE Internal Admin).