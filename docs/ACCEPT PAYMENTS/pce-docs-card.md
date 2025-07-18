---
title: Card
excerpt: >-
  Accept and manage credit and debit card payments with PCE’s robust, compliant
  platform.
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

Priority’s Commerce Engine (PCE) empowers businesses to accept and manage card payments with flexibility, control, and compliance. Built to support diverse industries—from e-commerce and hospitality to government services and subscription billing—PCE handles everything from simple one-time transactions to advanced routing and reconciliation. All card features adhere to PCI DSS Level 1 standards and operate within U.S. regulatory and card network rules.

**In this guide you’ll learn**

* Core capabilities of card payments in PCE
* How PCE ensures PCI DSS Level 1 compliance
* Advanced routing and reconciliation features

### Prerequisites & Limitations

* Valid merchant account and card network agreements
* PCI DSS Level 1 compliance for your organization
* U.S. regulatory requirements and card acceptance rules apply

# Compliance / Regulation Mandates

* **PCI DSS Level 1**: All card data handling—authorization, capture, routing, and tokenization—must comply with PCI DSS Level 1 standards to secure cardholder information.  
* **PSD2 Strong Customer Authentication**: Two-factor authentication under PSD2 is required for EU card payments initiated by customers.  
* **AML & KYC**: Implement risk-based anti-money laundering controls and customer due diligence for card transactions, especially high-value or cross-border.  
* **GDPR Data Protection**: Ensure personal and payment data processed in card workflows adheres to GDPR principles, including minimization, consent, and secure handling.

# Feature Table

| Feature                    | Description                                                        |
| -------------------------- | ------------------------------------------------------------------ |
| One-Time Card Transactions | Process single-charge payments with immediate authorization        |
| Card Tokenization          | Securely store card details as tokens for future transactions      |
| Advanced Routing           | Route transactions to optimal gateways or processors automatically |
| Reconciliation & Reporting | Automate settlement, track disputes, and generate payment reports  |

# Key Details

## One-Time Card Transactions

Process a single authorization and capture cycle for ad-hoc sales. Ideal for retail and one-off service charges.

## Card Tokenization

Replace sensitive card data with secure tokens. Reduce PCI scope and simplify repeat billing by referencing tokens instead of raw card details.

## Advanced Routing

Leverage configurable rules to route transactions based on geography, currency, volume, or cost. Optimize approval rates and transaction costs.

## Reconciliation & Reporting

Consolidate settlement data, monitor chargebacks, and generate detailed reports. Stay informed with automated notifications and clear audit trails.
