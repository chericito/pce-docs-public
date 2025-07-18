---
title: v2.58 Fiorentina 06/23
excerpt: Sandbox Release Date - June 23, 2025
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
![](https://files.readme.io/73a0f01bd2cfdf2137cc21a6b22965f1e256605a29bcabccc7f98566825a84b1-Fior_Release_notes_internal.png)

# About CPX
Commercial Payment Exchange is a seamless, end-to-end solution which can be used by institutions offering automated account payables solutions to their customers. It provides these institutions the capability to process payments to different suppliers using different instruments through a standard file format. It offers discounts, rebates, and incentives to the customers through supplier activation. It also supports an interactive portal that provides complete control and full visibility of payment status through easy, yet robust, reports.


# Enhancement

## 1. CPX to allow users to add Buyer details in CPX to onboard buyer on Visa (CPXBIZ-810)

CPX has now been enhanced to allow users to be able to add buyer details in CPX which would automatically onboard the buyer in Visa (VPA). 
Earlier users had to manually onboard a buyer in TSYS followed by onboarding in Visa (VPA) and then configuring the buyer details in CPX. 


__Implementation__

<ul>

<li>CPX has been enhanced to add buyer details in CPX which would onboard a buyer in Visa (VPA) directly. </li>
<li>At the institution level, a new configuration has been added for Visa (VPA) as Implementation Type. The user can setup the value as Pseudo accounts or TSYS Virtual accounts. This should be set as Pseudo account for the current buyers.</li>
</ul>

> ![](https://files.readme.io/4c041f85ee7426d8195330d8fd49fa99091bed33fbef59b533aef61a8b1cfd74-Fior_image1.png)
> <div align="center"> <i> Image 1: : Implementation Type added as a new field under Card tab under Institution Settings for Visa (VPA).  </i> </div>

<ul><li>At the buyer level, for Pseudo account configuration, the user can add the Buyer template ID and the Buyer ID. The buyer Id should be existing on TSYS and the Buyer template ID should be existing on Visa (VPA). </li>
</ul>

> ![](https://files.readme.io/e4f6ecc0429b25da53ea35231b4da8f3b382576973fb3ebb71fed175475a21d3-Fior_image2.png)
> <div align="center"> <i> Image 2: Buyer Template Id added as a new field under Card tab under Buyer Settings for Visa (VPA).</i> </div>

<ul><li>Once the user has added the details, the user can add the Funding account details. The funding account number, Credit limit and Expiration Date should be added and should already be configured on TSYS. </li>
</ul>

> ![](https://files.readme.io/db60b8e423501c0b690e1bdaf69c4cafd88927490d27972fe8883e1c90c2d2fb-Fior_image3.png)
> <div align="center"> <i> Image 3: Funding account Information needs to be added to setup Visa (VPA) at the buyer level.   </i> </div>

<ul>
<li>Once added, Funding account number cannot be edited, but Credit limit and expiration date can be changed and would be updated on Visa accordingly. </li>
<li>Once buyer and Funding account configurations are setup. The user can add card management rules on CPX. </li>
<li>The user can add single or multi use card rules and add user defined Proxy Pool Id. To setup the card management rules, users would also have to add Initial Order Count, Minimum Available Accounts, and Reorder Count. </li>
<li>The Initial Order count refers to the Initial count of available accounts/cards in the proxy pool at the time of pool creation. The minimum available accounts refers to the minimum count of accounts/cards that should be available in the proxy pool at all times. The Reorder count refers to the count of accounts/cards that should be ordered once the pool reaches the minimum count level. </li>
</ul>


> ![](https://files.readme.io/8629fff8475d51504bf1fbaa4a09cfaf3a50028d82acf358cdf93d3ebda5ee61-Fior_image4.png)
> <div align="center"> <i> Image 4: New fields added for Card Management Rules for Visa (VPA) for card under buyer settings  </i> </div>


<ul><li>The initial order count should always be greater than the Minimum available count.</li>
<li>CPX would call the requisite APIs to create buyer, funding account and proxy pool on Visa (VPA).  </li>
<li>If there are any errors in creating buyer, Funding account or Proxy Pool on Visa, the relevant error messages would be shown in corresponding sections. The user can only process payments using Visa (VPA) if buyer, funding account and Proxy pool have been configured correctly. </li>
<li>Internal admins can delete the Funding account details as well which would clear the funding account details but it would be mandatory to add funding account details to save the buyer. Deleting the funding account does not delete it on Visa, it only allows to delete the information from CPX. </li>
<li>If the funding account is changed, the card management rules would become irrelevant since they are associated to the previously set up funding account and would have to be deleted manually and new card management rules would have to be added to be able to process payments. </li>
<li>The user can delete card management rules/ proxy pools as well. This is only allowed if there are no existing active cards associated to that pool else deletion would not be allowed. </li>
</ul>


__Impact__

This would allow users to be able to setup Visa (VPA) on CPX and reduce manual overhead to setup the same on Visa.



__Table 1: Impacted Screens__


| Category           | Description                                                                                                                                                                                                                                                                                        |
|--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Institutions Tab | Impacted Screens<ul><li> Institutions</li><ul><li>Settings</li><ul><li>Card</li><ul><li>    Visa (VPA)</li><ul><li>Implementation Type</li><ul><li>Pseudo Accounts</li><li>TSYS Virtual Accounts</li></ul></ul></ul></ul></ul></ul>                                                                                                                                                    |
|   Buyers Tab       | Impacted Screens <ul><li>Buyers</li><ul><li>Settings</li><ul><li>Card</li><ul><li>Visa (VPA)</li><ul><li>Processor Information</li><ul><li>Buyer Template Id</li></ul><li>Funding Information</li><ul><li>Funding Account</li><li>Credit Limit</li><li>Expiration Date</li></ul><li>Card Management Rules</li><ul><li>Initial Order Count</li><li>Minimum Available Accounts</li><li>Reorder Count</li></ul></ul></ul></ul></ul> |


## 2. CPX to allow processing of ACH returns for UMB (CPXBIZ-901)(Hotfixed with Exeter City)

CPX has been enhanced to process ACH returns for UMB.

Earlier CPX was receiving returns for transactions but it has been tested for different NACHA ids as well. 


__Implementation –__

<ul><li>CPX has been enhanced to process returns from ach.com for UMB and update the ACH transactions as returned. </li>
<li>CPX would be receiving ACH returns as usual via ach.com and CPX would be consuming this information per NACHA ID and update the transaction on CPX as returned.  </li>
</ul>

__Impact__

This would allow UMB to be able to get updated on returns on the ACH transactions. 



## 3. CPX to support other as a billing method for ACH (CPXBIZ-900)(Hotfixed with Exeter city)

CPX has now been enhanced to support other as a billing method for ACH as a payment method.

Earlier CPX supported Good Funds and Pre-Fund as a billing method for ACH. 


__Implementation –__


<ul><li>CPX has been enhanced to support other as a billing method for ACH payment method.</li>
<li>If other has been set as the billing method for ACH, CPX will not be creating any debits for the ACH transactions, only credits will be processed for these transactions and the billing will have to be done manually.</li>
</ul>

> ![](https://files.readme.io/b75b00e96060ca3955e0aa0d478fac283bf13ce366d64eb0318432cc9eb01b6d-Fior_image5.png)
> <div align="center"> <i> Image 5: Other introduced as a billing method for ACH under buyer underwriting.  </i> </div>

<ul><li>Additionally any NACHA files being generated will only have credits and will be unbalanced NACHA files for such ACH transactions. </li></ul>

__Impact:__

This would allow CPX users(mainly UMB) to be able to user other as a billing method for ACH and get billing for the transactions separately as well as receive unbalanced NACHA files as requested.



__Table 2: Impacted Screens__

| Category     | Description                                                                                        |
|--------------|----------------------------------------------------------------------------------------------------|
|   Buyers Tab | Impacted Screens <ul><li>Buyers</li><ul><li>Underwriting</li><ul><li>Products</li><ul><li>ACH</li><ul><li>Billing Method</li><ul><li>Other</li></ul></ul></ul></ul></ul></ul> |


## 4. CPX to introduce custom roles for AMC (CPXBIZ-922) (Released with Exeter City)

CPX has now been enhanced to allow custom roles for AMC Institution

Earlier CPX allowed standard roles for all users and no custom roles were available. 

__Implementation –__

<ul><li>CPX has been enhanced to allow AMC to be able to add users with custom roles. </li>
<li>Three custom roles have been setup as AMC System Admin, AMC Property Accountant and AMC Accounting supervisor. </li>
<li>The roles are similar to Institution admin with certain additional restrictions. The Property Accountant and Accounting supervisor have the same set of privileges. </li>
<li>Only AMC institution can have access to these roles. Users can only be assigned AMC specific roles by Internal admin users or users associated to AMC institution already. </li></ul>


> ![](https://files.readme.io/d5d019e71478caf5bfecaefe0f7e9843e9ed663f3f60da2e5bc1933802bf00d4-Fior_image6.png)
> <div align="center"> <i> Image 6: New Custom Roles introduced for AMC under Users tab. </i> </div>

<ul>
<li>Any privileges not mentioned will automatically be provided to the custom role by default if a similar role in CPX has those privileges.</li>
</ul>


__Impact__

This would allow AMC to get onboarded while allowing their users to have custom roles thereby helping CPX generate revenue. 

## 5. CPX to consume Auth and Settlement information for Visa VPA (CPXBIZ-810) (Hotfixed)

CPX has now been enhanced to consume auth and settlement information for Visa VPA.
Earlier CPX was  able to create transactions on Visa VPA but CPX was not able to receive any auth or settlement updates leading to transactions not getting updated as per auth and settlements activity. 

__Implementation –__

<ul><li>CPX has been enhanced to receive auth and settlement data as Push notifications from Visa VPA. </li>
<li>This will allow CPX to consume any auth or settlement activities from Visa and update the transactions as per the activity allowing users to get updated on auth and settlements against the payments. </li>
<li>On receiving an auth or settlement notification CPX would update the auth or settlement history against the payment and would update the status of the transaction as well. </li>
</ul>


__Impact__

This would allow users to get updated on auth and settlements against the payments. 

## 6. CPX to generate custom Billing report for UMB (CPXBIZ-852) (Hotfixed)

CPX has now been enhanced to create a custom billing report for UMB buyers.
Earlier CPX was creating a custom billing report for Heartland only. 

__Implementation –__

<ul><li>CPX has been enhanced to create a custom billing report for UMB as well. </li>
<li>CPX will be creating the report with different billing elements including Check fees as received from Smart Payables and count of various transactions. </li>
<li>Additionally any elements that have a 0 count will not be included in the report and the report would only include accounts which have ACH or check set as default. Additionally CPX would also fee associated with check payments in the report once the check has moved to Sent status. </li>
</ul>

__Impact__

This would allow UMB to receive Billing report as per different elements for its buyers. 

# Bug Fixes

## 1. Fixed issue with CPX not being able to receive authorization information from Visa (CPXBIZ-810) (Hotfix)

It was noted that CPX was not being able to sync authorization data from Visa (VPA) due to incorrect date format. Additionally CPX was not being able to parse authorizations in the correct order for Visa (VPA) payments. The transaction has an auth decline followed by authorization but CPX parsed the authorization followed by auth decline leading to the payment being updated to Auth declined.
This issue has now been resolved and CPX is able to consume auth and settlement data from Visa to update status of transaction and CPX will parse the authorizations in the correct status.


## 2. Fixed issue with users not being able to view card details in disposition files (CPXBIZ-925) (Hotfixed with Exeter City)

It was noted that users were not being able to view card number and CVV in disposition files. This was due to recent changes in file importer where CPX started passing only last 4 digits of the card number which were being sent in the disposition file instead of the full card details. 
This issue has now been resolved and users will not be able to view the card details in the disposition files.


## 3. Fixed issue with exposure limits not getting updated for users as per the setting (CPXBIZ-921) (Hotfixed with Exeter City)

It was noted that when exposure limit was set for payment methods for users, the limit was not getting refreshed as per the time duration set leading to files getting stuck for approval due to the exposure limit getting breached falsely.  
This issue has now been resolved and the exposure limit for different payment methods would get refreshed as per the time duration.


## 4. Fixed issue with file staying in Pending External approval even if all payments are failed (CPX-5819) 

It was noted that when External Dual Approval was set up for a buyer but the external status of the supplier was inactive, all payments under the file would be failed but the file still remained in Pending External Approval status. 
This issue has now been resolved and if all payments under a file fail before the file is held for approvals, the file would be marked as failed as well.


## 5. Fixed issue with Merchant details not getting populated for Lodged transactions for Payments/PIF report (CPXBIZ-572) 

It was noted that merchant details were not getting populated for Lodged transactions for Payments/PIF report . 
This issue has now been resolved and merchant details will be populated for lodged transactions for DXC and Galileo as well as VCN transactions for Visa (VPA) as well in the Payments/PIF report.



![](https://files.readme.io/f41c27e9cd911f3d614bd78fdf57a5c0fd70df776fdd3593e3a733739ddfb2bf-Fior_Disclaimer.png)