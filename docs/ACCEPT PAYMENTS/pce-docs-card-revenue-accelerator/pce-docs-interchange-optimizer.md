---
title: Interchange Optimizer
excerpt: "Optimize your interchange costs by supplying Level\_1–3 data in CARD transactions for reduced processing fees."
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

The Interchange Optimizer feature lets merchants submit enhanced transaction details—Level 1, Level 2, and Level 3—to qualify for lower interchange rates. By providing more granular invoice, shipping, and tax information, you can reduce fees on corporate and purchase cards.

**In this guide you’ll learn**

* The differences between Level 1, Level 2, and Level 3 processing
* Required data fields to qualify for each level
* Best practices for implementing enhanced data in CARD transactions

### Prerequisites & limitations

* Merchant account approved for corporate or purchase-card acceptance
* PCE with Level 2/Level 3 data enabled in your configuration
* Qualification ultimately determined by the card network and issuing bank

# Compliance / Regulation Mandates

* **PCI DSS Level 1**: All card data storage, processing, and transmission must meet PCI DSS requirements to protect cardholder data.
* **PSD2 Strong Customer Authentication**: EU transactions require SCA under PSD2 for customer-initiated e‑commerce payments, ensuring two-factor authentication.
* **AML & KYC**: Implement risk-based Anti-Money Laundering (AML) controls, including Customer Identification Programs (CIP), Customer Due Diligence (CDD), and Enhanced Due Diligence (EDD) to comply with global AML regulations.
* **GDPR Data Protection**: Personal and payment data storage must adhere to GDPR principles—data minimization, explicit consent, and security-by-design—when handling EU citizen data.

# Feature table

| Feature            | Description                                                            |
| ------------------ | ---------------------------------------------------------------------- |
| Level 1 Processing | Basic card transactions with standard interchange fees                 |
| Level 2 Processing | Submit billing and purchase-order fields to lower corporate rates      |
| Level 3 Processing | Include full line-item, tax, shipping, and duty details for best rates |

# Key details

Merchants can improve interchange pricing by supplying additional fields in CARD transactions:

## Level 1 Processing

Basic transaction data: card number, expiration, amount, and merchant descriptor. This is the default and requires the least information.

## Level 2 Processing

Adds mid-level details to qualify for corporate rates:

* Card number, expiration, billing and shipping addresses
* Invoice number or unique purchase-order (PO) reference
* Tax amount separate from total transaction value

> *Level 2 submissions typically reduce fees on corporate and purchase cards when accepted by networks.*

## Level 3 Processing

Requires comprehensive, line-item data for the lowest interchange rates:

* All Level 2 fields
* Unit price or unit amount and unit-of-measure
* Freight, shipping, and duty amounts
* Discount amount and discount code
* Commodity or product codes
* Item description and quantity
* Unit tax and unit discount
* Ship‑from ZIP code

> **Note:** Not all transactions qualify; final eligibility is determined by the card network and issuing bank.

The customer portal and API both support adding Level 2 and Level 3 fields. Ensure your payload includes the required properties to unlock lower interchange tiers.