---
title: Modify Payments
excerpt: >-
  Manage and adjust scheduled ACH debit transactions in PCE—update amounts,
  change details, or cancel before processing to avoid errors and optimize cash
  flow.
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

You can update or cancel ACH debits that are still pending submission to the bank. Make changes to amount, purpose, or revoke the transaction entirely—so you can correct mistakes or adapt to customer requests.

**In this guide you’ll learn**

* How to originate an ACH collect and link it to a verified external account
* When and how you can update or cancel a scheduled transaction
* Why reversals are required once a payment enters the ACH network

### Prerequisites & Limitations

* **ACH Originations Enabled:** Your PCE merchant profile must have ACH debit initiation turned on.
* **Verified External Account:** The customer’s bank account must be in `VERIFIED` status before you can originate or modify transactions.
* **Modification Window:** Updates and cancellations are only permitted while the transaction remains in `SCHEDULED` or `PENDING` status and before the cutoff time.
* **Irrevocable After Processing:** Once a payment moves to `PROCESSING` (i.e., submitted to the ACH Operator), you cannot modify or cancel it via the API—only an ACH Reversal can address errors post-processing.

# Compliance / Regulation Mandates

* **Nacha Rules:** All updates and cancellations must comply with Nacha’s timing and formatting requirements for ACH entries.
* **Audit Trail:** Maintain logs of every modification or cancellation request for at least 2 years to support Nacha audits.
* **Customer Authorization:** Ensure any change to amount or schedule is covered by the original mandate or an amended authorization on file.

# Feature Table

| Feature             | Description                                                             |
| ------------------- | ----------------------------------------------------------------------- |
| **Update Payment**  | Modify amount, purpose, or effective date of a scheduled ACH debit      |
| **Cancel Payment**  | Revoke a scheduled debit before it’s transmitted to the ACH network     |
| **Bulk Operations** | Support for updating or canceling multiple transactions via file upload |

# Key Details

## Origination Process

1. **Create a Contact**

   * Use the PCE API to create a `Contact` object representing your customer.
2. **Add & Verify External Account**

   * Link an `ExternalAccount` with bank and routing numbers to the Contact.
   * Verify via instant EWS, prenote, or micro-deposits until status is `VERIFIED`.
3. **Originate ACH Collect**

   * Call the `Create Transaction` endpoint (method `ACH`) referencing the verified account.
   * Transaction enters `SCHEDULED` status awaiting batch submission.

## Modifying a Scheduled Transaction

While a transaction remains in **SCHEDULED** or **PENDING** status and before the daily cutoff, you may:

* **Update a Collect**

  * Change fields such as `amount`, `purpose`, or `scheduleDate`.
  * Send a `PATCH /v1/transactions/{id}` request with only the fields to update.
* **Cancel a Collect**

  * Send a `DELETE /v1/transactions/{id}` request to revoke the debit entirely.
  * The transaction moves to `CANCELLED` and will not be included in the next ACH file.

## Cutoff Times & Irreversibility

* **Standard Cutoff:** Typically 3:30 PM PT / 6:30 PM ET for forward-day ACH batches.
* **After Cutoff:** Any `SCHEDULED` items not yet transmitted will roll to the next processing window.
* **Processing Status:** Once a debit transitions to **PROCESSING**, it has entered the ACH network and cannot be modified or canceled via the API.
* **Reversals:** To correct errors after processing, initiate an ACH Reversal (`POST /v1/transactions/reversal`), subject to its own Nacha rules and timeframes.
