---
title: 'Overview: Online Payments'
excerpt: >-
  Accept and manage online payments effortlessly with PCE’s flexible payment
  types and methods.
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
Priority’s Commerce Engine (PCE) empowers businesses to accept secure, seamless, and flexible payments directly on their websites and mobile applications. Built on a modern, cloud-native platform, PCE brings together operational expertise and a comprehensive suite of tools to support complex commerce and finance needs. Whether you’re processing one-time transactions, saving customer payment methods, or handling subscription billing, PCE delivers a unified, scalable solution.

Offering support for multiple payment methods—credit and debit cards, ACH Debits, and checks — PCE ensures your customers can pay however they prefer. By integrating through Passport PCE APIs, you gain a single platform for all your payment channels, unified transaction data, and powerful reporting, enabling you to launch products faster and optimize your payment flows. 

# Use case

[block:parameters]
{
  "data": {
    "h-0": "Feature",
    "h-1": "Description",
    "0-0": "One-Time Payments",
    "0-1": "Process single-use transactions without storing payment details.  \n  \n**Use cases: **Retail checkout, Event registrations, Invoice or service-fee payments",
    "1-0": "Saved Payment Details",
    "1-1": "Store customer payment methods securely for repeat purchases.   \n  \n**Use cases: **Returning e-commerce customers, Subscription sign-ups, Vendor payments",
    "2-0": "Recurring Payments",
    "2-1": "Automate charges on a schedule—ideal for subscriptions & installment plans.   \n  \n**Use cases:** SaaS subscriptions, Membership dues, Installment billing."
  },
  "cols": 2,
  "rows": 3,
  "align": [
    null,
    null
  ]
}
[/block]


## Payment Methods

PCE supports a variety of payment methods to suit your business needs. Choose from any of the options below:

[block:html]
{
  "html": "<table>\n  <thead>\n    <tr>\n      <th align=\"left\">Product</th>\n      <th align=\"left\">Capabilities</th>\n    </tr>\n  </thead>\n  <tbody>\n    <tr>\n      <td><strong>Card</strong></td>\n      <td>\n        <ul>\n          <li><strong>Payments Core</strong>\n            <ul>\n              <li>✓ Direct Sale (Immediate Capture)</li>\n              <li>✓ Separate auth and captures</li>\n              <li>✓ Authorization Controls\n                <ul>\n                  <li>✓ Incremental Auth</li>\n                  <li>✓ Void authorization</li>\n                </ul>\n              </li>\n              <li>✓ Capture Controls\n                <ul>\n                  <li>✓ Full captures</li>\n                  <li>✓ Partial captures (single/multi)</li>\n                  <li>✓ Over capture</li>\n                </ul>\n              </li>\n              <li>✓ Refunds\n                <ul>\n                  <li>✓ Full Refunds</li>\n                  <li>✓ Partial (single/multiple)</li>\n                </ul>\n              </li>\n              <li>✓ Tip Adjustments</li>\n              <li>✓ Store Card Detail (Tokenization)</li>\n              <li>✓ Supported Card Brand Support\n                <ul>\n                  <li>✓ Visa, Mastercard, AMEX OptBlue, Discover</li>\n                  <li>✗ AMEX Direct, Discover Direct</li>\n                </ul>\n              </li>\n              <li>✓ Recurring Payments</li>\n            </ul>\n          </li>\n          <li><strong>Risk / Fraud Shield</strong>\n            <ul>\n              <li>✓ PCI Compliance Support</li>\n              <li>✓ Good funds model</li>\n              <li>✓ Reduce Decline Rates\n                <ul>\n                  <li>✓ AVS, CVV checks</li>\n                  <li>✓ Name Match Check</li>\n                  <li>✓ Decline Reasons</li>\n                </ul>\n              </li>\n              <li>✓ Dynamic Statement Descriptors</li>\n              <li>✓ Velocity checks</li>\n            </ul>\n          </li>\n          <li><strong>Revenue Accelerator</strong>\n            <ul>\n              <li>✓ Interchange Optimization via Payment L2/L3 Line Items</li>\n              <li>✓ Cost Recovery via Surcharge</li>\n            </ul>\n          </li>\n          <li><strong>Power your Platforms (Marketplace)</strong>\n            <ul>\n              <li>✓ Split Payments</li>\n            </ul>\n          </li>\n        </ul>\n      </td>\n    </tr>\n    <tr>\n      <td><strong>ACH Bank Debit</strong></td>\n      <td>\n        <ul>\n          <li><strong>Payments Core</strong>\n            <ul>\n              <li>✓ ACH Debit Initiation</li>\n              <li>✓ Same day ACH Payment</li>\n              <li>✓ Track Payments</li>\n              <li>✓ SEC Codes – CCD, PPD, WEB, TEL</li>\n              <li>✓ Modify Payments – Cancel, Update</li>\n              <li>✓ Refunds\n                <ul>\n                  <li>✓ Full Refunds</li>\n                  <li>✓ Partial / Multiple Partial</li>\n                </ul>\n              </li>\n              <li>✓ Addenda Records – Single line</li>\n              <li>✓ Recurring Payments</li>\n            </ul>\n          </li>\n          <li><strong>Account Validation & Verification</strong>\n            <ul>\n              <li>✓ Instant Verification via EWS</li>\n              <li>✓ Prenotification (Prenote)</li>\n              <li>✓ Micro-deposit Verification</li>\n            </ul>\n          </li>\n          <li><strong>Processing / Settlement</strong>\n            <ul>\n              <li>✓ Standard ACH Processing</li>\n              <li>✓ Same Day ACH Processing</li>\n              <li>✓ ACH Reversals</li>\n              <li>✓ Automated Return handling</li>\n              <li>✓ Notification of Change handling</li>\n            </ul>\n          </li>\n          <li><strong>Risk / Fraud Shield</strong>\n            <ul>\n              <li>✓ Good funds model</li>\n              <li>✓ Velocity Controls</li>\n              <li>✓ Statement Descriptors</li>\n              <li>✓ Fraud prevention\n                <ul>\n                  <li>✓ Debit Blocks on high return rates</li>\n                </ul>\n              </li>\n            </ul>\n          </li>\n        </ul>\n      </td>\n    </tr>\n    <tr>\n      <td><strong>Check Deposit</strong></td>\n      <td>\n        <ul>\n          <li><strong>Payments Core</strong>\n            <ul>\n              <li>✓ Mobile Check Deposit</li>\n              <li>✓ Lockbox Check Deposit</li>\n            </ul>\n          </li>\n          <li><strong>Processing / Settlement</strong>\n            <ul>\n              <li>✓ Check Rejections and Returns handling</li>\n            </ul>\n          </li>\n          <li><strong>Risk / Fraud Shield</strong>\n            <ul>\n              <li>✓ Good funds model</li>\n              <li>✓ Velocity Controls</li>\n              <li>✓ Manual review</li>\n            </ul>\n          </li>\n        </ul>\n      </td>\n    </tr>\n  </tbody>\n</table>"
}
[/block]