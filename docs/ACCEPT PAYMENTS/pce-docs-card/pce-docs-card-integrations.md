---
title: Integrations
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
This page guides you through connecting your platform to PCE’s APIs, handling real-time event notifications via webhooks, and validating your integration in our sandbox environment. Whether you’re encrypting cards in-browser, subscribing to live transaction updates, or stress-testing workflows in a safe simulator, PCE delivers the tools and compliance you need.

### Prerequisites

* Valid PCE API credentials (sandbox and production)
* HTTPS endpoint for webhooks (with optional basic auth)

### Limitations

* Sandbox data is isolated—do not import live customer or transaction data

<br />

<Cards columns={3}>
  <Card title="Integration Methods" href="doc:integration-methods" icon="fa-code">
    Learn how to embed PCE’s JavaScript SDK for card encryption, collect sensitive data securely in the browser, and exchange it for payment tokens—minimizing your PCI scope.
  </Card>

  <Card title="Webhooks" href="doc:webhooks" icon="fa-bell">
    Set up and secure webhook subscriptions in the PCE portal, confirm your endpoint, and handle incoming notifications for resource creations and updates to keep your systems in sync.
  </Card>

  <Card title="Sandbox Simulator" href="doc:sandbox-simulator" icon="fa-flask">
    Use the PCE Sandbox Simulator to recreate the full transaction lifecycle—including success and failure paths—so you can validate end-to-end flows without impacting production systems.
  </Card>
</Cards>