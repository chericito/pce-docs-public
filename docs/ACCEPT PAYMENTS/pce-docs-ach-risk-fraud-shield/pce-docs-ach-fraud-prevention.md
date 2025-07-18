---
title: Fraud Prevention
excerpt: >-
  Reduce ACH return rates and “friendly fraud” disputes with clear, recognizable
  company names and dynamic entry descriptions that customers instantly
  understand.
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

This page covers best practices for preventing ACH returns by using effective statement descriptors and platform configuration in PCE.  

**In this guide you’ll learn**  

* How to choose and configure your company name for ACH entries  
* Techniques for crafting dynamic, clear entry descriptions  
* Where and how to override descriptors per transaction in PCE  

### Prerequisites & Limitations

* ACH origination must be enabled on your merchant account  
* Must comply with Nacha SEC code requirements  
* Descriptor fields are limited by the fixed-width Nacha file format (94 characters total)  

# Compliance / Regulation Mandates

* **Nacha File Format**: Statement descriptor fields adhere to the 94-character fixed-width Nacha specification.  
* **SEC Code Rules**: Must use the correct SEC code (PPD, CCD, WEB, TEL) for each debit; descriptor requirements vary by code.  
* **GDPR & Data Privacy**: Ensure any personal data in descriptions complies with data protection regulations.  

# Feature Table

| Feature                       | Description                                                        |
| ----------------------------- | ------------------------------------------------------------------ |
| Statement Descriptor Defaults | Configure a default “Company Name” at the customer account level   |
| Dynamic Entry Descriptions    | Override the “Company Description” on a per-transaction basis      |
| Descriptor Length Enforcement | Automatic validation/truncation to meet Nacha’s fixed-width limits |

# Key Details

## Best Practices and Configuration

To minimize customer confusion and reduce unauthorized returns:

* **Use a Recognizable Company Name**

  The Company Name should be the name your customers know you by, such as your “Doing Business As” (DBA) name, even if it differs from your legal entity name.

* **Provide a Dynamic and Clear Description**

  The Company Entry Description is your best tool for providing context. Instead of a generic value like “PAYMENT,” use dynamic information that helps the customer identify the specific transaction. Examples include:  

  * “INVOICE #12345”  
  * “JUNE RENT”  
  * “YOGA CLASS”

* **Platform Configuration**

  A default Company Name can be configured at the customer’s PCE account level to apply to all transactions. For more granular context, pass a custom description in the payment creation API payload via:  

  ```json
  "processingDetail": {
    "companyDescription": "YOUR_CUSTOM_DESCRIPTION"
  }
  ```
