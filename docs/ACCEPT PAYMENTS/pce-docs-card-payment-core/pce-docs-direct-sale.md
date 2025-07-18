---
title: Direct Sale (Immediate Capture)
excerpt: >-
  Process and settle payments instantly with a single API call—ideal for
  immediate-order fulfillment.
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

The Direct Sale (Immediate Capture) method authorizes and captures funds in one step, delivering fast, straightforward payment processing for merchants fulfilling orders right away—such as digital goods, event tickets, or in-stock products.

**In this guide you’ll learn**

* When to use Direct Sale vs separate auth and capture
* How to structure your single-sale API request
* How to handle PCE’s synchronous response

### Prerequisites & Limitations

* Active merchant account with card processing enabled
* PCI DSS Level 1 compliance
* Network permissions for enhanced data (L1, L2 & L3) when collecting detailed line-item information

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: All card data captured and processed must comply with PCI DSS Level 1 to ensure cardholder data security.  
- **PSD2 Strong Customer Authentication**: EU direct-sale transactions require two-factor authentication under PSD2 for customer-initiated e-commerce payments.  
- **AML & KYC**: Apply risk-based anti-money laundering controls and KYC checks, especially for high-value or unusual transactions.  
- **GDPR Data Protection**: Adhere to GDPR principles—data minimization, explicit consent, and secure storage—when handling EU citizens’ payment information.  

# Feature Table

| Feature                 | Description                                                             |
| ----------------------- | ----------------------------------------------------------------------- |
| Combined Auth & Capture | Authorization and capture in one API call                               |
| Synchronous Response    | Immediate success or failure confirmation                               |
| Level 2/3 Data Support  | Attach enhanced transaction details (L1, L2 & L3) for optimized routing |

# Key Details

## Direct Sale (Immediate Capture)

A “Direct Sale” or “Sale” transaction combines authorization and capture into a single step. This method is best when you need to charge the customer’s card and begin transferring funds as soon as the transaction is approved.

Use this method when you want a fast, one-step payment flow that immediately settles funds into your account.

1. Customer submits payment details.
2. Merchant server sends one `CREATE_TRANSACTION` API request to PCE, including amount, payment data, and optional L2/L3 fields.
3. PCE contacts card networks to authorize and immediately capture funds.
4. PCE returns a synchronous response indicating success or failure.

**Reference documentation**

* [Create Transaction API Reference](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-create-transaction)
* [API Guide: Transaction entity (CARD method)](https://documentation.prioritypassport.com/passport-docs/v2.0.0/docs/pm-entities)