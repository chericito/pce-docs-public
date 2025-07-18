---
title: PCE Entities and Operations
excerpt: >-
  A concise catalog of all PCE entities and the operations you can perform on
  them via the API.
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

This page provides a complete reference for every PCE entity—such as Customer, Account, Transaction, and more—and details the Create, Retrieve, Update, Delete, and specialty actions supported on each. Use this guide to plan your integration flows, automate workflows, and understand the full surface area of the PCE API.

**In this guide you’ll learn**

* The core PCE entities and their business roles
* Which CRUD and advanced operations each entity supports
* How to leverage these operations in your integration and automation

### Prerequisites & Limitations

* A PCE sandbox account with valid API credentials
* Appropriate API role permissions for entity operations
* Adherence to the rate limit (1,000 requests per 10 seconds) to avoid throttling

# Key Details

| Entity                             | Description                                                                                    | Operations Available                                                                                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| **Customer**                       | An individual, business, or joint tenancy onboarded onto PCE.                                  | Create, Retrieve, Update, Delete, List, Add Customer Preferences, Retrieve Customer Preferences, Retrieve Beneficial Owners |
| **Account**                        | FDIC-insured account opened for a customer to collect, manage, store, and move funds.          | Create, Retrieve, Update, Delete, List, Retrieve by Customer, Close, Account Statement, List Interest History               |
| **External Account**               | A bank account outside PCE linked to a customer for pulls or pushes.                           | Create, Retrieve, Update, Delete, List, Retrieve by Customer, Validate, Verify, Block, Unblock                              |
| **International External Account** | A non-U.S. bank account supporting cross-border transfers.                                     | Create, Retrieve, Update, List, Retrieve by Customer, List Meta Data                                                        |
| **Merchant**                       | A business customer that accepts and processes card transactions.                              | Create, Retrieve, Update, Delete, List, Retrieve by Customer, Merchant Statement, Preview API                               |
| **Terminal**                       | A semi-integrated POS endpoint for card-present payments.                                      | Retrieve                                                                                                                    |
| **Card**                           | A payment card outside PCE linked to a customer for payments.                                  | Create, Retrieve, Update, Delete, List, Retrieve by Customer                                                                |
| **Mailing Address**                | A postal address associated with a customer or entity.                                         | Create, Retrieve, Update, Delete, List, Retrieve by Customer                                                                |
| **Collect**                        | Instruction to pull funds (ACH, Card, Check) from an external account or card.                 | Create, Retrieve, Update, Delete, List, Cancel, Void                                                                        |
| **Send**                           | Instruction to push funds (ACH, Check, Wire, Book, Virtual Card) from PCE to external account. | Create, Retrieve, Update, Delete, List, Cancel, Stop, Retrieve Virtual Card Image                                           |
| **Transaction**                    | Any fund-movement instruction (ACH, Card, Check, Wire, Book).                                  | Create, Retrieve, Update, Delete, List, Cancel, Stop, Void, Refund, Capture Transactions, Retrieve Virtual Card, FX Quotes  |
| **Recurring Transaction**          | A scheduled, repeating fund-movement instruction.                                              | Create, Retrieve, Update, Delete, List, List History, Cancel, Pause, Resume                                                 |
| **Ledger**                         | A record of every transaction performed on an account.                                         | List                                                                                                                        |
| **Chargeback**                     | Issuer-initiated reversal of a card transaction due to dispute or fraud.                       | List                                                                                                                        |
| **Authorized User**                | A legal user entity linked to a business customer.                                             | Create, Retrieve, Update, List, Retrieve by Customer                                                                        |
| **Debit Card**                     | A physical debit card issued against a PCE account.                                            | Create, Retrieve, List, Freeze, Unfreeze, Replace, Reissue, Retrieve Card Image                                             |
| **Location**                       | A saved business or customer address record.                                                   | Create, Retrieve, Update, List, Retrieve by Merchant, Retrieve by Customer                                                  |
| **Signup Invite**                  | Self-signup invitation for new users via email or SMS.                                         | Create, List                                                                                                                |
| **Contact**                        | A frequent payee or counterparty for collect/send transactions.                                | Create, Retrieve, Update, Delete, List, Retrieve by Customer, Verify PPI                                                    |
| **Batch**                          | A group of card captures and refunds bundled for settlement.                                   | List, Retrieve, Retrieve by Customer                                                                                        |
| **Funding Rule**                   | Rules to split incoming funds among multiple recipients or accounts.                           | Create, Retrieve, Deactivate, List                                                                                          |
| **Secured Credit Card**            | A collateral-backed credit card issued to a customer.                                          | Create, Retrieve, Activate                                                                                                  |
| **Webhook**                        | A configured HTTP callback that notifies your endpoint of PCE events.                          | Create, Retrieve, Update, Delete, List                                                                                      |