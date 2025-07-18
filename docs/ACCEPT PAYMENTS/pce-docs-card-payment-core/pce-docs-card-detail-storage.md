---
title: Card Detail Storage
excerpt: >-
  Securely vault and tokenize card details to accelerate checkouts and minimize
  PCI scope.
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

Card Detail Storage lets you securely save customer payment information in a PCI-compliant vault, enabling faster checkouts, subscription billing, and automatic top-ups—without handling raw card data.

**In this guide you’ll learn**

* How tokenization replaces sensitive card data with secure tokens
* Best practices for managing token lifecycle and shopper consent
* Use cases: subscriptions, top-ups, and one-click checkouts

### Prerequisites & Limitations

* Active merchant account with card-vaulting enabled
* PCI DSS Level 1 compliance
* Shopper consent for storing payment details
* Token operations subject to network and regional data rules

# Compliance / Regulation Mandates

- **PCI DSS Level 1**: Ensure all tokenization and storage processes obey PCI DSS Level 1 requirements to protect cardholder data.  
- **PSD2 Strong Customer Authentication**: Apply two-factor authentication for saving and using payment details in EU e-commerce scenarios.  
- **AML & KYC**: Follow risk-based Anti-Money Laundering and Know Your Customer guidelines when onboarding tokenized payment methods.  
- **GDPR Data Protection**: Comply with GDPR mandates on data minimization, explicit consent, and secure storage for EU citizens’ payment information.  

# Feature Table

| Feature                       | Description                                                     |
| ----------------------------- | --------------------------------------------------------------- |
| Secure PCI-Compliant Vaulting | Store card data in a fully compliant, tokenized vault           |
| Token Lifecycle Management    | Create, retrieve, update, and delete tokens securely            |
| Subscription & Top-ups        | Charge stored tokens for recurring billing or automatic reloads |

# Key Details

Securely store customer payment details to streamline future purchases. We provide a fully PCI DSS Level 1–compliant vault using tokenization to protect card data, reduce your PCI scope, and simplify compliance. With shopper consent, you can store one or more payment methods per customer.

We refer to saved payment details as **tokens**, and the process as **tokenization**.

**Benefits of tokenization**

* Let shoppers store payment details for one-click or recurring payments.
* Support subscriptions, installment plans, and automatic account top-ups.
* Remove sensitive data handling from your systems—shrink your PCI footprint.

**Use cases**

* E-commerce platforms offering saved cards for returning customers.
* SaaS and membership billing with recurring charges.
* Prepaid account reloads or wallet top-ups without re-entering card data.

**API Reference:** Refer to the tokenization section in the Appendix of the API guide:
[Card Tokenization API](https://documentation.prioritypassport.com/passport-docs/v3.0.0/docs/doc-card-tokenization)