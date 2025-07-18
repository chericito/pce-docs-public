---
title: 'Card: Integrations'
excerpt: >-
  Integrate with PCE’s powerful APIs—from secure card tokenization and real-time
  webhooks to sandbox simulation—for seamless payment workflows.
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

This page guides you through connecting your platform to PCE’s APIs, handling real-time event notifications via webhooks, and validating your integration in our sandbox environment. Whether you’re encrypting cards in-browser, subscribing to live transaction updates, or stress-testing workflows in a safe simulator, PCE delivers the tools and compliance you need.

**In this guide you’ll learn**

* How to securely collect and tokenize card data on the frontend  
* Steps to subscribe, confirm, and process PCE webhook events  
* How to emulate full payment lifecycles and edge cases in the sandbox  

### Prerequisites & limitations

* Valid PCE API credentials (sandbox and production)  
* HTTPS endpoint for webhooks (with optional basic auth)  
* Sandbox data is isolated—do not import live customer or transaction data  

# Feature table

| Feature                        | Description                                                           |
| ------------------------------ | --------------------------------------------------------------------- |
| Card Encryption & Tokenization | Securely collect card data in-browser and exchange it for PCE tokens  |
| Webhook Subscription           | Register and confirm endpoints, then receive real-time event payloads |
| Sandbox Simulator              | Emulate authorizations, captures, refunds, and error scenarios        |

# Key details

## [Integration Methods](doc:integration-methods)

Learn how to embed PCE’s JavaScript SDK for card encryption, collect sensitive data securely in the browser, and exchange it for payment tokens—minimizing your PCI scope.

## [Webhooks](doc:webhooks)

Set up and secure webhook subscriptions in the PCE portal, confirm your endpoint, and handle incoming notifications for resource creations and updates to keep your systems in sync.

## [Sandbox Simulator](doc:sandbox-simulator)

Use the PCE Sandbox Simulator to recreate the full transaction lifecycle—including success and failure paths—so you can validate end-to-end flows without impacting production systems.
