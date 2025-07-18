---
title: Velocity Limits
excerpt: >-
  Learn how to configure and monitor transaction velocity limits in PCE to
  proactively curb fraud and control risk exposure.
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

Velocity limits are proactive rules that cap the count and total dollar value of ACH debit transactions over rolling time windows—before they ever reach the network.

**In this guide you’ll learn**  
* What velocity controls are and why they matter  
* How PCE lets you tailor limits per customer or program  
* How to retrieve and display remaining limits via API  

### Prerequisites & Limitations

* Active PCE merchant account with ACH debit origination enabled  
* Sufficient permissions to view or configure velocity settings  
* Limits apply only to ACH debit origination; they do not affect credits or other payment methods  

# Compliance / Regulation Mandates

- **NACHA Risk Management**: Velocity limits support Nacha’s requirement for originators to maintain risk-based controls.  
- **Fraud Prevention Best Practices**: Industry standards recommend transaction throttling to limit exposure.  

# Feature Table

| Feature              | Description                                                       |
|----------------------|-------------------------------------------------------------------|
| Daily/Weekly/Monthly Limits | Cap the number and/or aggregate amount of debits per time window |
| Per-Customer & Program-Level | Configure separate velocity profiles for individual customers or entire programs |
| API-Driven Visibility | Retrieve remaining allowances to power real-time UI notifications |

# Key Details

## Proactive Controls: Velocity Limits

Before any ACH debit is sent to the network, PCE evaluates it against configured velocity rules. If the transaction would exceed a limit, it is blocked immediately.

### How Velocity Controls Work

- **Count Limits**: Maximum number of debits allowed (e.g., 10 transactions per day).  
- **Amount Limits**: Maximum aggregate dollar volume (e.g., $50,000 per month).  
- **Rolling Windows**: Windows reset on a rolling basis (e.g., last 24 hours, last 30 days), not calendar boundaries.  

### Purpose

Velocity rules mitigate large-scale fraud by limiting how much an attacker can pull from a compromised account in a short period.

### Configuration

- **Scope**: Define rules at the individual customer level or inherit defaults from the program-wide profile.  
- **Customization**: Tailor limits based on customer risk factors—industry, transaction history, account age, etc.  

### API Access

You can programmatically retrieve both the configured limits and the customer’s current usage:

GET /v1/customers/{customerId}/velocity_limits