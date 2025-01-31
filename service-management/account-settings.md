# Account settings

In the bottom left corner, on the left side bar, click on the name of the account and then click on **Account Settings.**

In this page you can:

* Visualize License details (only available to direct Cusna customers)
* Visualize the details of the Managed Service Provider (if the account is managed by an MSP)
* Reset the account data



### Service Provider

If the Oganization acoutn is actively managed by an MSP, the Service Provider card shows the details of the MSP.

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

### License

On the **License** card, you can see your current Subscription and check the status of your allowances in terms of **max Properties** and **max Residents**

<figure><img src="../.gitbook/assets/image (167).png" alt=""><figcaption></figcaption></figure>

Moreover you can see the activation status of the add-ons, including:

* [**Units**](units.md): the Units add-on allows you to manage the [Units](units.md) of your Network and assign an Access Point to each unit. This option is disabled by default because not all hardwares support this capability.
* [**Billing**](../add-ons/billing.md): the billing module allows to create subscription plans that you can assign to tenants. Tenants will have to setup their payment method on their first login to the Tenant Portal before seeing their WiFi passphrase



### Account Management

The **Reset Your Workspace** option allows to delete all data in the account.

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

When clicking the button **Reset account**, the user has to confirm the action by typing "_reset_" in an input box.

<figure><img src="../.gitbook/assets/image (19).png" alt="" width="375"><figcaption></figcaption></figure>



The **Delete your account** option allows to permanently delete the Organization account and all its related configuration and PII.

<figure><img src="../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

When clicking the button **Delete account**, the user has to confirm the action by typing "_delete_" in an input box.

<figure><img src="../.gitbook/assets/image (18).png" alt="" width="375"><figcaption></figcaption></figure>

{% hint style="info" %}
The only metadata retained after Organization delete, is the reference name of the account, used in the MSP dashboard to consult the history subscriptions and MAA consumption.
{% endhint %}



The **Data Retention option**, allows to automatically delete accounts (a related PII) after a certain number of days since the service was suspended.

<figure><img src="../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
A daily routine checks for all Accounts that match the data retention settings and deletes them. If you set the number of days to 0, only Accounts that have been terminated before the daily data retention routine runs are deleted, otherwise they are deleted the following day.
{% endhint %}
