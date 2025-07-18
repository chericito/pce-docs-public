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

<Table>
  <thead>
    <tr>
      <th>
        Feature
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        One-Time Payments
      </td>

      <td>
        Process single-use transactions without storing payment details.  

        * \*Use cases: \*\*Retail checkout, Event registrations, Invoice or service-fee payments
      </td>
    </tr>

    <tr>
      <td>
        Saved Payment Details
      </td>

      <td>
        Store customer payment methods securely for repeat purchases.   

        * \*Use cases: \*\*Returning e-commerce customers, Subscription sign-ups, Vendor payments
      </td>
    </tr>

    <tr>
      <td>
        Recurring Payments
      </td>

      <td>
        Automate charges on a schedule—ideal for subscriptions & installment plans.   

        * \*Use cases:\*\* SaaS subscriptions, Membership dues, Installment billing.
      </td>
    </tr>
  </tbody>
</Table>

## Payment Methods

PCE supports a variety of payment methods to suit your business needs. Choose from any of the options below:

<HTMLBlock>{`
<table>
  <thead>
    <tr>
      <th align="left">Product</th>
      <th align="left">Capabilities</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Card</strong></td>
      <td>
        <ul>
          <li><strong>Payments Core</strong>
            <ul>
              <li>✓ Direct Sale (Immediate Capture)</li>
              <li>✓ Separate auth and captures</li>
              <li>✓ Authorization Controls
                <ul>
                  <li>✓ Incremental Auth</li>
                  <li>✓ Void authorization</li>
                </ul>
              </li>
              <li>✓ Capture Controls
                <ul>
                  <li>✓ Full captures</li>
                  <li>✓ Partial captures (single/multi)</li>
                  <li>✓ Over capture</li>
                </ul>
              </li>
              <li>✓ Refunds
                <ul>
                  <li>✓ Full Refunds</li>
                  <li>✓ Partial (single/multiple)</li>
                </ul>
              </li>
              <li>✓ Tip Adjustments</li>
              <li>✓ Store Card Detail (Tokenization)</li>
              <li>✓ Supported Card Brand Support
                <ul>
                  <li>✓ Visa, Mastercard, AMEX OptBlue, Discover</li>
                  <li>✗ AMEX Direct, Discover Direct</li>
                </ul>
              </li>
              <li>✓ Recurring Payments</li>
            </ul>
          </li>
          <li><strong>Risk / Fraud Shield</strong>
            <ul>
              <li>✓ PCI Compliance Support</li>
              <li>✓ Good funds model</li>
              <li>✓ Reduce Decline Rates
                <ul>
                  <li>✓ AVS, CVV checks</li>
                  <li>✓ Name Match Check</li>
                  <li>✓ Decline Reasons</li>
                </ul>
              </li>
              <li>✓ Dynamic Statement Descriptors</li>
              <li>✓ Velocity checks</li>
            </ul>
          </li>
          <li><strong>Revenue Accelerator</strong>
            <ul>
              <li>✓ Interchange Optimization via Payment L2/L3 Line Items</li>
              <li>✓ Cost Recovery via Surcharge</li>
            </ul>
          </li>
          <li><strong>Power your Platforms (Marketplace)</strong>
            <ul>
              <li>✓ Split Payments</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><strong>ACH Bank Debit</strong></td>
      <td>
        <ul>
          <li><strong>Payments Core</strong>
            <ul>
              <li>✓ ACH Debit Initiation</li>
              <li>✓ Same day ACH Payment</li>
              <li>✓ Track Payments</li>
              <li>✓ SEC Codes – CCD, PPD, WEB, TEL</li>
              <li>✓ Modify Payments – Cancel, Update</li>
              <li>✓ Refunds
                <ul>
                  <li>✓ Full Refunds</li>
                  <li>✓ Partial / Multiple Partial</li>
                </ul>
              </li>
              <li>✓ Addenda Records – Single line</li>
              <li>✓ Recurring Payments</li>
            </ul>
          </li>
          <li><strong>Account Validation & Verification</strong>
            <ul>
              <li>✓ Instant Verification via EWS</li>
              <li>✓ Prenotification (Prenote)</li>
              <li>✓ Micro-deposit Verification</li>
            </ul>
          </li>
          <li><strong>Processing / Settlement</strong>
            <ul>
              <li>✓ Standard ACH Processing</li>
              <li>✓ Same Day ACH Processing</li>
              <li>✓ ACH Reversals</li>
              <li>✓ Automated Return handling</li>
              <li>✓ Notification of Change handling</li>
            </ul>
          </li>
          <li><strong>Risk / Fraud Shield</strong>
            <ul>
              <li>✓ Good funds model</li>
              <li>✓ Velocity Controls</li>
              <li>✓ Statement Descriptors</li>
              <li>✓ Fraud prevention
                <ul>
                  <li>✓ Debit Blocks on high return rates</li>
                </ul>
              </li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td><strong>Check Deposit</strong></td>
      <td>
        <ul>
          <li><strong>Payments Core</strong>
            <ul>
              <li>✓ Mobile Check Deposit</li>
              <li>✓ Lockbox Check Deposit</li>
            </ul>
          </li>
          <li><strong>Processing / Settlement</strong>
            <ul>
              <li>✓ Check Rejections and Returns handling</li>
            </ul>
          </li>
          <li><strong>Risk / Fraud Shield</strong>
            <ul>
              <li>✓ Good funds model</li>
              <li>✓ Velocity Controls</li>
              <li>✓ Manual review</li>
            </ul>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
`}</HTMLBlock>
