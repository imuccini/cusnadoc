# MSP Dashboard

MSP accounts allows partners and service providers to manage multiple organizations from the same dashboard.

<figure><img src="../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

The main dashboard shows summary KPIs related ot the MSP, including:

* total number of managed Organizations / max number of Organizations allowed on the MSP
* total number of Accounts / max number of Accounts allowed on the MSP
* total number of Networks

## Managing Organizations

The Organization table shows the list of the Organizations managed by the MSP. By clicking on the Login button, the MSPo can login into the dashboard of a specific Organization.



## Creating new Organizations

If the Max Organization allowance of the MSP is greater than the current number of managed organizations, the MSP is allows to create a new Org. Creating a new Organization only required to set the **Name** of the Organizations as input and the **MAX MAU** threshold.

If you wish to not block end-users from onboarding into the service, simply enter a big number (e.g. 1 million)

<figure><img src="../.gitbook/assets/image (285).png" alt=""><figcaption></figcaption></figure>

## Managing MSP administrators

Form the Admin menu, the Admin assigned as "Owner" of the MSP, can create additional Admin accounts that will have all permissions except creating other MSP Admins

<figure><img src="../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

When creating a new Admin is possible to:

* elect the new Admin as the Owner of the MSP account
* create a standard MSP Admin and optionally add additional permissions, including
  * create Organizations
  * purchase Licenses
* opt to notify new Admin via email. The welcome email include a link to let the new admin set up their credentials

<figure><img src="../.gitbook/assets/image (340).png" alt=""><figcaption></figcaption></figure>



## License management

On the License page, the MSP Admins can visualize the status of current subscriptions metrics and extend current allowances.



{% hint style="info" %}
**What are MAA (Monthly Active Account)**\
Monthly Active Accounts (MAA) quantifies the number of unique Accounts that have held '_Active_' status at any point during a given month. An '_Active_' account is authorized for network access, while an '_Inactive_' account is not. Accounts can transition between these statuses through automated rules or manual changes via the admin console.

The MAA metric captures all accounts that were active during the month, including those active at the month's start and any that became active during the month. If an account switches between active and inactive multiple times within the same month, it is counted only once in the MAA tally.
{% endhint %}



### Summary

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

The first sections shows the main current relevant metrics:

* **Current Month MAAs:**  number of Active Accounts accounted for the current Month.&#x20;
* Current level of **MAA allowance**: MAA Allowance represent a thresholds of MAAs under which the Organization does not incur in any Overage fees.
* **Overage MAAs**: number of MAAs accounted for the current  month that exceed the current MAA Allowance

### **MAU Allowance History**

The **MAU Allowance History** section, shows the level of MAU Allowance on the past 12 months. It also reports all past orders to extend the MAU allowance

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

By click the "**Extend**" button, the MSP Admin can order a MAA Subscription among those available. Fro example, by ordering quantity 2 of the SKU "_1K MAA Allowance_", the organization MAU Allowance increases of 2,000 MAA for the next 12 months

<figure><img src="../.gitbook/assets/image (85).png" alt="" width="375"><figcaption></figcaption></figure>

### **Monthly Active Account History**

**The Monthly Active Account History** section shows the level of MAA for the past 12 months for the MSP overall, or for one specific Organization as selected form the dedicated dropdown.

The table provides the detail of the MAAs for each Organization for every month of the past 12 months, or for a specific month as selected form the dedicated dropdown

<figure><img src="../.gitbook/assets/image (351).png" alt=""><figcaption></figcaption></figure>



## Anomalies

The **Anomalies** page provide the MSP visibility of all critical service notifications of managed Organizations to help identify issues affecting the service availability.

<figure><img src="../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>
