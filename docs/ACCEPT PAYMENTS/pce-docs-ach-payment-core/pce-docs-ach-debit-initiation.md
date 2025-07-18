---
title: ACH Debit Initiation
excerpt: >-
  Manage and refine payment authorizations with granular controls for dynamic
  transaction scenarios.
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

ACH Direct Debit lets you “pull” funds from a customer’s bank account—ideal for recurring billing, invoice collections, and platform funding—using the Automated Clearing House network. Unlike real-time methods, ACH debits settle in batch windows and carry return and dispute risks.

**In this guide you’ll learn**

* How ACH debits differ from card and wire payments  
* The end-to-end flow and key participants in an ACH debit  
* Cutoff rules, transaction types, status lifecycle, and best practices  

### Prerequisites & Limitations

* Your business must be a U.S.‐registered entity with an enabled ACH origination relationship.  
* ACH debits carry return risk (NSF) and consumer disputes up to 2 years post-settlement.  
* Not recommended for one-off high-value transactions; best for established, trust-based recurring payments.  
* No real-time authorization—final success/failure can take 4–5 business days to confirm.  

# Compliance / Regulation Mandates

* **NACHA Operating Rules**: Must follow SEC code requirements, batching formats, settlement windows, and return handling timelines.  
* **Reg E (EFTA)**: Provide required disclosures and consumer error-resolution procedures for consumer debits.  
* **OFAC & KYC/AML**: Screen transactions against sanctions lists and perform risk-based customer due diligence.  
* **Reg CC Funds Availability**: Adhere to cutoff and settlement timing for same-day vs. next-day ACH.  
* **GDPR & Data Privacy**: Securely handle personal and bank account data in compliance with GDPR and local privacy laws.  

# Feature Table

| Feature                 | Description                                                               |
| ----------------------- | ------------------------------------------------------------------------- |
| Pull-Based Collection   | “Pull” funds from payer accounts via one-time or recurring ACH debits     |
| Next-Day & Same-Day ACH | Choice of standard next-day or accelerated same-day settlement            |
| SEC Code Support        | CCD, PPD, WEB, TEL with single-line addenda (CTX not supported)           |
| Cutoff & Scheduling     | Multiple daily batch windows; missed cutoff schedules for next day        |
| Account Validation      | Instant EWS checks, zero-dollar prenotes, and micro-deposit verifications |
| Track & Modify Payments | Query status; cancel or update debits before cutoff                       |
| Returns & Reversals     | Automated NACHA return code handling and reversal workflows               |
| Refunds                 | Full or partial (multiple) refunds on settled debits                      |

# Key Details

## Core Characteristics

* **Pull-Based Mechanism**

  Originators “pull” funds from a customer’s account via debit instructions—opposite of ACH Credits. Requires a signed mandate specifying account/routing, amount (fixed or variable), frequency, and revocation instructions.

* **Asynchronous, Batch Processing**

  ACH operates in fixed batch windows (not real-time). You’ll receive final success or failure acknowledgments up to 4–5 business days after initiation, impacting funds availability and refund timing.

* **Risk & Dispute Window**

  — Returns (e.g., NSF) can occur days after settlement.\
  — Consumer disputes under Reg E allowed up to 2 years post-settlement; business-originated debits up to 1 year.

* **Best for Recurring, Trust-Based Use Cases**

  Ideal for subscriptions, B2B invoice collections, wallet funding, and automated bill payments. Not recommended for one-off, high-value goods where instant settlement is critical.

## Common Use Cases

* **Recurring Subscription Billing**:  Automate monthly SaaS or membership fees.  
* **B2B Payments & Invoice Collection**: Pull scheduled or on-demand payments from corporate clients.  
* **Account Funding & Wallet Top-Ups**: Allow users to fund internal accounts/wallets from their bank.  
* **Automated Bill Payments**: Utilities, insurance, rent, loan repayments.

## Key Participants & Flow

| Entity           | Role                                                                                                     |
| ---------------- | -------------------------------------------------------------------------------------------------------- |
| **Originator**   | Your business initiating the debit instruction.                                                          |
| **Receiver**     | Customer whose bank account is debited.                                                                  |
| **ODFI**         | Originating Depository Financial Institution (Passport’s partner bank); submits NACHA-formatted batches. |
| **ACH Operator** | Central clearing (Fed or EPN) that sorts and routes entries.                                             |
| **RDFI**         | Receiver’s bank; posts the debit and handles returns.                                                    |

**Flow Steps**  

1. **Authorization & Initiation**: Customer signs mandate; you call Passport API to create an ACH debit.  
2. **Batching**: ODFI aggregates entries into a NACHA file.  
3. **Transmission**: File sent to ACH Operator before cutoff.  
4. **Sorting & Routing**: Operator routes each entry to the correct RDFI.  
5. **Processing & Settlement**: RDFI debits the account; funds ultimately settle to your Passport account after the good-funds period.

## Origination & Cutoff Rules

* **Cutoff Time**: 3:30 pm PT / 6:30 pm ET for same-day and forward-day batches.  
* Transactions created **before** cutoff enter the current window; those **after** schedule for the next.  
* Missed a cutoff? Your debit simply moves to the next available batch (e.g., next-day settlement).
* You may originate ACH debits by using saved contacts.

![Originated ACH Debit Flowchart](https://files.readme.io/7690d36dfa2198c40cfcfd0cdaaf685f7befc7d417d2e29d9f2b96e9dcf2ab9e-image.png)

## ACH Debit Types

* **Next-Day ACH (Default)**: Standard settlement in next batch.  
* **Same-Day ACH**: Accelerated settlement across intraday windows (subject to network fees and limits).

## Transaction Status Lifecycle

| Status           | Description                                                                                                                                                   |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SCHEDULED**    | Default upon creation.                                                                                                                                        |
| **PENDING**      | Waiting processing checks:<br>• Source account must be ACTIVE with sufficient funds<br>• Destination must be ACTIVE<br>• Entities must be OFAC & CIP verified |
| **APPROVED**     | *(Card only)* Authorized by issuing bank.                                                                                                                     |
| **PROCESSING**   | Picked up for batch processing.                                                                                                                               |
| **CANCELLED**    | Cancelled by user before settlement.                                                                                                                          |
| **COMPLETED**    | • After good-funds period<br>• Upon successful refund completion                                                                                              |
| **FAILED**       | • Unable to process within batch interval<br>• Returned for reasons like account closure or debit block                                                       |
| **IN\_DELIVERY** | *(Check only)* Check is in shipment.                                                                                                                          |
| **DELIVERED**    | *(Check only)* Check delivered successfully.                                                                                                                  |
| **STOPPED**      | *(Check only)* Stop-payment request after printing.                                                                                                           |

## Track & Modify Payments

* **Track Payments**: Poll the Transactions API or subscribe to webhooks for status updates.  
* **Modify Before Cutoff**: Cancel or update amount/date/addenda on a scheduled debit to prevent origination.  
* **Handle Returns & Reversals**:  System automatically processes NACHA return codes and reversal flows per NACHA rules.
