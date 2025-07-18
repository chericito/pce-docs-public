---
title: SEC Codes
excerpt: >-
  Understand PCE’s supported ACH SEC codes—PPD, CCD, WEB, and TEL—and learn why
  CTX entries aren’t available on our platform, so you can classify your debits
  correctly and stay fully Nacha-compliant.
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

Every ACH entry must be classified with a three-letter Standard Entry Class (SEC) code. These codes define the transaction type, authorization method, and applicable Nacha rules (including return deadlines). Using the correct SEC code is critical for ACH compliance.

**In this guide you’ll learn**

* The purpose and requirements of each supported SEC code
* Best practices for selecting PPD, CCD, WEB, or TEL entries
* Why CTX entries are not supported on PCE

### Prerequisites & Limitations

* Active merchant account with ACH Debit origination enabled
* Compliance with Nacha Operating Rules and Regulation E for consumer protection
* PCE supports only PPD, CCD, WEB, and TEL—CTX is not available

# Compliance / Regulation Mandates

* **Nacha Operating Rules**\
  Every ACH entry must use the correct SEC code and follow its specific authorization, data, and return requirements.
* **Regulation E**\
  Provides consumer rights and error-resolution procedures for electronic fund transfers.
* **Authorization & Record-Keeping**

  * **PPD:** Written mandates retained for at least 2 years.
  * **TEL:** Oral authorizations with scripted disclosures, retained for at least 1 year.
* **SEC-Specific Controls**

  * **WEB:** Requires secure identity verification and account validation before origination.
  * **TEL:** Must adhere to Nacha’s call-record scripting and authentication standards.

# Feature Table

| Feature | Description                                                                                             |
| ------- | ------------------------------------------------------------------------------------------------------- |
| **PPD** | Prearranged Payment & Deposit – consumer-signed written authorizations for one-time or recurring debits |
| **CCD** | Corporate Credit or Debit – single-line remittance for business-to-business ACH transfers               |
| **WEB** | Internet-Initiated/Mobile Entry – online-collected approvals with enhanced security checks              |
| **TEL** | Telephone-Initiated Entry – oral authorizations over the phone following Nacha scripting rules          |

# Key Details

## What Are SEC Codes?

A Standard Entry Class (SEC) code is a three-letter designation on each ACH file that governs authorization methods, data requirements, return timeframes, and risk controls.

## Supported SEC Codes

### PPD (Prearranged Payment & Deposit)

* **Use case:** Consumer billing (utilities, subscriptions)
* **Authorization:** Written mandate (paper or electronic signature)
* **Returns:** 60 days for unauthorized, dispute window up to 2 years

### CCD (Corporate Credit or Debit)

* **Use case:** B2B payments with minimal remittance data
* **Authorization:** Business agreement, usually written or contractual
* **Returns:** 2 business days for unauthorized; standard corporate return windows

### WEB (Internet-Initiated/Mobile Entry)

* **Use case:** Consumer debits via website or mobile app
* **Authorization:** Online agreement; PCE requires identity & account validation
* **Security:** Must comply with Nacha’s WEB security guidelines (e.g., tokenization, risk scoring)

### TEL (Telephone-Initiated Entry)

* **Use case:** One-time or recurring debits authorized orally over telephone
* **Authorization:** Recorded call or written summary; follow Nacha’s scripting requirements
* **Retention:** Store call records or signed confirmation for at least 1 year

## Unsupported SEC Code

### CTX (Corporate Trade Exchange)

* **Not supported on PCE**
* Designed for high-volume B2B use with up to 9,999 addenda records for detailed remittance—beyond PCE’s SME-focused ACH capabilities.
