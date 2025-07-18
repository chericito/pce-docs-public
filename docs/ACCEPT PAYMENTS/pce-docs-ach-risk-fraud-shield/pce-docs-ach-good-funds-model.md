---
title: Good Funds Model
excerpt: >-
  Understand how PCE holds funds through a “good funds” model to mitigate ACH
  return risk and manage cash flow timing.
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

The “Good Funds” model defines when settled ACH debits become available for use. Because ACH is not real-time and returns can arrive days or even weeks later, PCE imposes a clearing period (realization interval) to protect against administrative and unauthorized returns.

**In this guide you’ll learn**  
* Why a holding period is necessary in ACH debit processing  
* How long PCE waits before releasing funds  
* How to programmatically retrieve and configure your realization interval  

### Prerequisites & Limitations

* Active PCE merchant account with ACH debit origination enabled  
* Understanding of ACH return windows (administrative: 2 business days; unauthorized: up to 60 days)  
* Funds are unavailable until the end of the configured realization interval  

# Compliance / Regulation Mandates

- **Nacha Return Rules**: RDFIs may return debits for R01–R04 reasons within two business days, and R10–R29 reasons up to 60 days.  
- **Risk Management**: Holding funds aligns with Nacha guidelines to prevent claw-backs and negative balances.  

# Feature Table

| Feature                  | Description                                                                               |
| ------------------------ | ----------------------------------------------------------------------------------------- |
| Clearing Period          | Delay before funds availability to cover the most common return windows (R01–R04)         |
| Realization Interval API | Endpoint to retrieve the configured holding period for your merchant account             |
| Configurable Interval    | PCE default is 3 days; can be adjusted per account via API or PCE Portal (Internal Admin) |

# Key Details

## Purpose of the Clearing Period

ACH debits are “pull” instructions without real-time confirmation of funds. The holding period buffers you against returns:
- **Administrative returns (R01–R04)** often occur within 2 business days.  
- **Unauthorized returns (R10)** may arrive up to 60 days later.  
Holding funds reduces the chance of claw-backs after you’ve already used the money.

## PCE Default and Configuration

By default, PCE enforces a 3-day realization interval on all originated ACH debits, matching the two-day window for administrative returns plus a safety margin. You can:
- **Retrieve** the interval via `GET /v1/account/{accountId}` (look for `realizationInterval`).  
- **Adjust** the interval in the PCE Portal (Internal Admin) to suit your risk tolerance and cash-flow needs.

## Programmatic Access

To check your current good funds period:

```http
GET /v1/account/{accountId}
```