---
title: Onboarding Entities
excerpt: Easy onboarding and meet compliance with minimal friction.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
<p style="color:rgb(4, 4, 4);font-size: 15px; padding-bottom: 5px;padding-top: 15px;line-height: 23px;">PCE offers a flexible and secure onboarding framework for both individual and business customers, integrating directly into your product workflows.

The onboarding flow is designed to minimize friction and enable incremental data collection through a **wizard-like experience**. It is intelligent and adaptive — dynamically rendering forms based on user input such as:

Users can save their progress and resume later without losing any data. The flow also supports **progressive onboarding**, allowing customers to access additional financial services by submitting only the new, required information, without re-entering previously submitted data.

# Compare Onboarding Methods

Choose the method that fits your customer experience model best.

<HTMLBlock>{`
<style> table.onboarding-compare { width: 100%; border-collapse: separate; border-spacing: 0; border: 1px solid #f0f0f0; border-radius: 8px; overflow: hidden; font-size: 14px; } table.onboarding-compare th, table.onboarding-compare td { padding: 12px 16px; text-align: left; border-bottom: 1px solid #f6f6f6; vertical-align: top; } table.onboarding-compare th { background-color: #fafafa; font-weight: 600; color: #333; } table.onboarding-compare tr:last-child td { border-bottom: none; } </style> <table class="onboarding-compare"> <thead> <tr> <th>Onboarding Method</th> <th>Authentication Required</th> <th>User Experience</th> <th>Integration Effort</th> <th>Use Case Suitability</th> <th>Compliance Support</th> </tr> </thead> <tbody> <tr> <td>MFA (Multi-Factor Auth)</td> <td>Yes</td> <td>Secure, user-verified entry</td> <td>Moderate</td> <td>High-risk or sensitive data onboarding</td> <td>Enhanced security compliance</td> </tr> <tr> <td>Wet Signature</td> <td>Manual identity verification</td> <td>Offline, physical form signing</td> <td>High</td> <td>Legal or high-compliance scenarios requiring physical signature</td> <td>Jurisdiction-specific</td> </tr> <tr> <td>App Engine</td> <td>Depends on configuration</td> <td>Customizable, embedded forms</td> <td>High</td> <td>Tailored onboarding journeys with advanced logic</td> <td>Fully configurable</td> </tr> <tr> <td>🖊️ eSign</td> <td>Yes (email/mobile)</td> <td>Digitally signed document flow</td> <td>Moderate</td> <td>Mid to high-value accounts, regulated industries</td> <td>Compliant with eSignature laws</td> </tr> <tr> <td>Invite for Self Signup</td> <td>Optional (via invite link)</td> <td>Self-service, user-initiated</td> <td>Low</td> <td>Referral flows, marketplaces, partners</td> <td>Optional KYC/AML configurable</td> </tr> <tr> <td>Click Wrap</td> <td>Yes (IP Address and acceptance details)</td> <td>Fast, lightweight flow</td> <td>Low</td> <td>Simple agreements, low-risk onboarding</td> <td>Basic consent capture</td> </tr> </tbody> </table>
`}</HTMLBlock>

# Who Can You Onboard?

<div class="3b" style="display: flex;align-content: space-between;flex-direction: row;width: 865px; position: relative;gap: 15px;margin-bottom: 15px;">

<a href="doc:pce-docs-onboard-business" style="text-decoration:none">
<div class="b1" style=" box-sizing: border-box; border: solid 1px rgba(0, 0, 0, 0.1);background-color: #fff;border-radius: 7px;text-align: center;text-decoration: none!important;box-shadow: 0 4px 10px rgba(62, 62, 62, 0.03);transition: all .2s ease 10ms!important;padding: 25px 25px 20px 25px;color: #000!important;width: 265px; height: 295px; transition: all .2s ease 10ms">
<img src="https://files.readme.io/f810a73c0a8b5771ee4a1ccf7b8e1fb33b58430e0535adc1a3b28ab793bad23b-images_5.png" style="width: 50px;">
<h2 style="font-size: 18px;line-height: 27px;">Business </h2>
<p style="font-size: 15px;line-height: 20px;margin: 8px 0 10px 0;color: rgba(0,0,0,.5);">A registered entity with legal documents, tax ID, beneficial owners, and authorized signers</p>
</div>
</a>

<a href="doc:pce-docs-onboard-joint-tenancy" style="text-decoration:none">
<div class="b2" style=" box-sizing: border-box;border: solid 1px rgba(0,0,0,.1);background-color: #fff;
border-radius: 7px;text-align: center;text-decoration: none!important;box-shadow: 0 4px 10px rgba(62,62,62,.03);transition: all .2s ease 10ms!important;padding: 25px 25px 20px 25px;color: #000!important;width: 265px;height: 295px; transition: all .2s ease 10ms">
<img src="https://files.readme.io/b7a607987ad2d4bbc7da8f9898e801cb0c3b968643476e18fc5d1179f24c3005-family-house-icon-vector-isolated-260nw-722004034_copy.png" style="width: 50px;">
<h2 style="font-size: 18px;line-height: 27px;">Joint Tenancy</h2>
<p style=" font-size: 15px;line-height: 20px;margin: 8px 0 10px 0;color: rgba(0,0,0,.5);"> A shared account type where two or more individuals hold equal rights to the entire account </p>
</div>
</a>

<a href="doc:pce-docs-onboard-individual" style="text-decoration:none" >
<div class="b3" style="box-sizing: border-box;border: solid 1px rgba(0,0,0,.1);background-color: #fff;border-radius: 7px;text-align: center;text-decoration: none!important;box-shadow: 0 4px 10px rgba(62,62,62,.03);transition: all .2s ease 10ms!important;padding: 25px 25px 20px 25px;color: #000!important;width: 265px;height: 295px; transition: all .2s ease 10ms">
<img src="https://files.readme.io/d8d2b875814f09f0e77e2ecb9946e1e34424d0baafbadb7329ecbba132f4f5cd-personal-id-icon-logo-vector-design_810420-797.avif" style="width: 50px;">
<h2 style="font-size: 18px;line-height: 27px;">Individual</h2>
<p style="font-size: 15px;line-height: 20px;margin: 8px 0 10px 0;color: rgba(0,0,0,.5);"> A sole user or consumer onboarded with personal identity verification</p>
</div>
</a>
