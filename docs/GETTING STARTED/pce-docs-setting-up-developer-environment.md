---
title: Setting up the Developer Environment
excerpt: >-
  Configure your developer environment to authenticate and call PCE’s Sandbox
  APIs securely.
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

This page walks you through setting up your local or CI environment to start coding against the PCE Sandbox APIs.

**In this guide you’ll learn**

* How to obtain your Sandbox Bearer (API) token
* Which base URL to use for all requests
* Best practices for storing and using your token

### Prerequisites & Limitations

* A provisioned PCE Sandbox account with API-User access
* A secure place to store your credentials (environment variables, vault, etc.)

# Key Details

## Share Your Sandbox Token

To authenticate your API calls, you need a Bearer token:

* Contact PCE Support to request your Sandbox API token.
* You will receive a token tied to your API-User credentials.

## Sandbox Base URL

Always point your requests at the Sandbox endpoint:

```
https://<your-sandbox-base-url>/v1
```

## Authorization Header

Include your token in every request:

```
Authorization: Bearer <YOUR_TOKEN>
```

## Secure Token Management

* **Environment Variables:** Don’t hardcode your token in source code.
* **Secrets Management:** Use a vault or secrets manager to rotate and inject your token at runtime.