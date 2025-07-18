---
title: Create PCE Account
excerpt: >-
  Learn how to request and configure your PCE sandbox environment, invite team
  members, and prepare for seamless integration.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
This page walks you through the steps a Program Manager needs to take to get started with PCE: from requesting a sandbox account to managing access and sharing resources.

### Prerequisites & Limitations

* You must have a Program Manager or Partner-level role authorized to request sandbox access.
* A secure email channel for sharing temporary credentials and API keys.
* Adherence to your organization’s security policies for credential storage and rotation.

# Request a New PCE Sandbox Account

1. Email the PCE Support/Implementation team at **[support@passportpayments.com](mailto:support@passportpayments.com)**
2. Use the subject line:

   ```
   Request: New PCE Sandbox Account for [Partner/Program Name]
   ```
3. In the email body, include:

   * First Name, Last Name
   * Business Email, Business Phone
   * Job Title, Company, Company Website

The Account Management team will then provision your sandbox and reach out with next steps.

# Receive and Secure Your Credentials

Once your request is approved, you’ll receive:

* **Sandbox Portal URL**
* **Username & Temporary Password**
* **API Credentials** (API Key + Secret)
* **Documentation Links**

> **Tip:** Store these securely (e.g., in a secrets manager) and rotate passwords/API keys if they’re shared across multiple users.

# Share Access with Your Team

1. Log in to the PCE Sandbox Portal.
2. Go to **Settings → User Management → Add**.
3. Enter the new user’s details:

   * First Name, Last Name, Email, Phone
   * Date of Birth, Address, Tax Identifier
4. Select **User Type**: Portal User or API User.
5. Assign appropriate access controls based on their role.
6. Click **Add User**—they’ll get an onboarding email automatically.

> **Optional:** For each API User, you can generate unique API keys by contacting your Admin team.

# Supporting Materials

* **PCE API Documentation**: Comprehensive reference for all endpoints
* **Sample Postman Collection**: Ready-to-use requests for rapid testing
* **Test Data Sets**: Preconfigured accounts, transactions, and use-case scenarios