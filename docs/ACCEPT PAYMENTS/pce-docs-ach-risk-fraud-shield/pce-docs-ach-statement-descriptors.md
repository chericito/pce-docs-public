---
title: Statement Descriptors
excerpt: >-
  Learn how to craft and configure ACH statement descriptors in PCE to minimize
  friendly-fraud disputes and returns.
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

Clear, concise statement descriptors are your first line of defense against “friendly fraud” returns. This guide explains how PCE surfaces “Company Name” and “Company Description” on customer bank statements, navigating the legacy NACHA fixed-width limits to maximize recognition and reduce disputes.

**In this guide you’ll learn**  
* The difference between “Company Name” and “Company Description” fields  
* Best practices and examples for high-recognition descriptors  
* How to set defaults and override per transaction in PCE  

### Prerequisites & Limitations

* Active PCE merchant account with ACH debit origination enabled  
* “Company Name” and DBA registered with your ACH processor if using a trade name  
* NACHA-mandated fixed-width limits (94 characters total per entry)  

# Compliance / Regulation Mandates

- **NACHA Fixed-Width Format**: Descriptors must fit within the 94-character ACH file specification; PCE enforces the maximum length but does not alter network rules.  
- **Unauthorized Return (R10)**: Unrecognized descriptors often trigger R10 returns; clear naming helps satisfy “commercially reasonable” best practices.  

# Feature Table

| Feature                       | Description                                                         |
|-------------------------------|---------------------------------------------------------------------|
| Company Name                  | Originator identifier shown on statement (legal or DBA)             |
| Company Description           | Contextual memo explaining the debit (e.g., invoice or service)     |
| Transaction-Level Override    | Override the default description via `processingDetail.companyDescription` |

# Key Details

When an ACH debit posts, the customer sees two fields:

1. **Company Name**  
   - Identifies the entity initiating the debit.  
   - Should be instantly recognizable (use your DBA if that’s more familiar than your legal name).  
   - PCE truncates any excess to fit the NACHA limit—design your naming to avoid mid-word cuts.

2. **Company Description**  
   - Provides context for why the debit occurred.  
   - Keep it concise and jargon-free:  
     - Recurring service: “Monthly Software Subscr”  
     - One-time purchase: “Invoice #12345”  
     - Utility bill: “Electric Bill June”  
     - Loan payment: “Loan Pmt 06/25”  
   - Defaults are set at the customer account level; override per transaction via:

     ```json
     "processingDetail": {
       "companyDescription": "Your custom memo here"
     }
     ```

**Why it matters**  
Vague or cut-off descriptors (e.g., “ACMEINC PAYMENT”) lead to confusion and higher R10 returns. Investing effort in clear, customer-friendly messaging directly reduces disputes and associated fees.

**Configuring in PCE**  
- **Account-Level Default**: Set your standard company name and description in the merchant dashboard or via API to apply to all ACH debits.  
- **Per-Transaction Override**: Include `processingDetail.companyDescription` in your debit request to tailor the memo for individual transactions.

> **Tip:** Test your descriptors by mapping them in a sandbox and reviewing sample NACHA files to ensure readability after truncation.