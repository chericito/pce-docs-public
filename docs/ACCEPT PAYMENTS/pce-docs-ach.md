---
title: ACH Bank Debits
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

PCE’s ACH capabilities let you initiate one-time and recurring bank debits, track payment status, handle returns, and validate accounts—all via a unified, PCI-light API. Whether you need standard or same-day processing, addenda records, or advanced fraud controls, PCE delivers a robust, compliant solution.

**In this guide you’ll learn**

* How to initiate, modify, and track ACH debits  
* Best practices for returns, reversals, and refunds  
* Techniques for account validation, risk controls, and split payouts  

### Prerequisites & Limitations

* Active merchant bank account enabled for ACH origination  
* Agreement to NACHA Operating Rules and ODFI sponsorship  
* HTTPS endpoint for notifications (webhooks)  
* Sandbox data is isolated—don’t import live bank details  

# Compliance / Regulation Mandates

- **NACHA Operating Rules:** All ACH transactions must comply with NACHA rules for SEC codes, settlement windows, and return timelines.  
- **Reg E (EFTA):** Provide required disclosures and error-resolution procedures for consumer debits.  
- **OFAC & KYC/AML:** Screen all transactions against OFAC lists and perform risk-based customer due diligence.  
- **Reg CC Funds Availability:** Adhere to cutoff and settlement timing requirements for same-day and next-day ACH.  
- **GDPR & Data Privacy:** Protect personal and bank account data in accordance with GDPR and applicable privacy laws.  

# Feature Table

| Feature                           | Description                                                            |
| --------------------------------- | ---------------------------------------------------------------------- |
| ACH Debit Initiation              | Create one-time or recurring ACH debits with selectable SEC codes       |
| Same-Day ACH                      | Submit and settle transactions within same-day processing windows       |
| SEC Code Support                  | CCD, PPD, WEB, TEL (CTX not supported) with addenda line records       |
| Payment Tracking                  | Query transaction status and receive webhook notifications             |
| Modify Payments                   | Cancel or update scheduled debits before cutoff                        |
| ACH Returns & Reversals           | Handle automated returns, reversals, and NOC workflows                 |
| Refunds                           | Issue full and partial (multiple) refunds on settled debits            |
| Account Validation & Verification | Instant EWS, prenotes, and micro-deposit verification                  |
| Processing & Settlement           | Standard vs same-day ACH, cutoff times, settlement timings             |
| Risk & Fraud Shield               | Good-funds model, approvals, velocity controls, statement descriptors, debit blocks |
| Revenue Accelerator               | Split payouts to multiple Passport or external accounts; clearing accounts |
| Integration Methods               | REST APIs, bulk file uploads, webhooks (incl. returns), sandbox simulator |

# Key Details

## ACH Debit Initiation

Initiate ACH debits by specifying amount, SEC code (CCD, PPD, WEB, TEL), and schedule. Use addenda records for extra info.

## Same-Day ACH

Submit debits for same-day settlement within designated cutoff windows; subject to network limits and fees.

## SEC Code Support

Support for CCD (corporate credit), PPD (consumer debit), WEB (e-commerce), and TEL (telephone-initiated). CTX (corporate trade) is not supported.

## Addenda Records

Include a single addenda line to convey invoice or remittance details alongside the debit.

## Modify Payments

Cancel or update scheduled debits (amount, date, or addenda) before the cutoff time to prevent origination.

## ACH Returns & Reversals

Automatically process NACHA return codes (R-codes) and reversals. Receive webhook notifications for returned or reversed transactions.

## Refunds

Issue full refunds or one-or-more partial refunds against settled debits, up to the original amount.

## Account Validation & Verification

### Instant EWS Verification  
Perform upfront ACH account checks via Early Warning System for immediate validation.

### Prenotification (Prenote)  
Send zero-dollar prenote transactions to verify account and routing data before live debits.

### Micro-deposit Verification  
Use two-small deposits and customer confirmation to verify account ownership.

## Processing & Settlement

- **Standard ACH:** Next-day settlement following NACHA batch windows.  
- **Same-Day ACH:** Multiple intraday windows for faster settlement.  
- **Cutoff Times:** Observe ACH network cutoff deadlines to ensure timely processing.  
- **Automated Return Handling:** System-driven retries and notifications for common return reasons.  
- **Notification of Change (NOC):** Accept routing/account updates via NOC events.

## Risk & Fraud Shield

- **Good-Funds Model:** Reserve funds upon initiation to reduce NSF risk.  
- **Payment Approvals:** Optional pre-approval flows before debit submission.  
- **Velocity Controls:** Limit transaction counts and volumes per account or customer.  
- **Statement Descriptors:** Customize ACH debit descriptions for clarity.  
- **Fraud Prevention:** Leverage machine learning and rules engines.  
- **Debit Blocks:** Automatically block debits on accounts with high return rates.

## Revenue Accelerator

- **Split Payouts:** Distribute debit proceeds across multiple Passport or external accounts based on funding rules.  
- **Clearing Accounts:** Use dedicated clearing accounts for consolidated settlement and reconciliation.

## Integration Methods

- **APIs:** Full CRUD support for debits, returns, validations, and payouts.  
- **Bulk File Uploads:** Submit NACHA-formatted files for high-volume batches.  
- **Webhooks:** Receive real-time event notifications for creations, updates, returns, and reversals.  
- **Sandbox Simulator:** Emulate full ACH lifecycles and failure scenarios in a safe test environment.