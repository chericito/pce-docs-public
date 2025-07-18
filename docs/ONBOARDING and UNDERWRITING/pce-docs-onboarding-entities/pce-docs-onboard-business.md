---
title: Onboarding & Underwriting a Business
excerpt: A .
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
# Onboarding a Business 

A business entity can sign up for <a href="doc:pce-docs-onboard-merchants"> Merchant Services </a> to be able to collect payments online (via paylink) and for Card-present and card-not-present scenario (in-store and online ecommerce). 

The business may decide at the same time or at a later to activate disbursements and pay-outs to vendors.

When Applied:
Onboarding corporations, LLCs, partnerships, or other legal entities
Required before enabling accounts or financial services
Also triggers KYC for linked individuals (Authorised Users, Beneficial Owners)

To comply with regulatory standards (such as AML, BSA, and card network rules) and to assess business legitimacy, Passport enforces identity verification protocols during onboarding and service enablement. These include:
KYC (Know Your Customer) - for individuals and sole proprietors
KYB (Know Your Business) - for companies and business entities
Underwriting - for enabling high-risk or card-based merchant services


### Single Business boarding

PCE Onboarding would create an entity in SES of type business and facilitate the collection of boarding and underwriting data and orchestrate the boarding process in Passport and MXM. 

SES will track business data along with compliance checks and UW status in order to inform the boarding API of what additional data collection and checks are needed to activate a new service.

When the business requires to add terminals, PCE boarding will require additional data collection complete KYC/KYB compliance.

Progressive onboarding allows businesses to be instantly provisioned a bank account, but requires added personal details to disburse funds.

A business  may elect to utilize Plastiq to optimize their working capital and extend cashflow. This would require the onboarding process to create a payer account in Plastiq and request any added  information at the time of activation.

Additionally, we have a requirement from Teamworks to onboard Universities. "U Arkansas" requested the ability to open an account without sharing PII information, referencing an "authorization letter." Business and Compliance have approved permitting these universities, unwilling to provide CP identification, to use a letter option. This represents another use case for business onboarding on PCE v2.

### Bulk Business boarding

Onboarding their customers as businesses in PCE by loading your existing users (businesses) to be provisionally setup in PCE. Services will be activated when the business completes their boarding/KYC/KYB.

# Underwriting