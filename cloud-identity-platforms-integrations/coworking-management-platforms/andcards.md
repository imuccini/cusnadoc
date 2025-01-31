# Andcards

Andcards integration allow co-working customers to self-provision their secure WiFi access.

Customers can visit the WiFi Portal - which URL is different per each Location - and enter the email address associated with their account in Andcards.

If the email matches with the email associated to a CoWorker in Andcards, Cusna sends a magic link to the provided email to login into the WiFi portal. At this point the user will be able to see and change its own private WiFi passphrase.

At this time, Cusna can automatically provisions access for:

* **members** with an active plan\
  WiFi access for individual members is scheduled for automatic termination on the end-date associated to the user account&#x20;
* user with a **desk booking** in the same day; WiFi access is granted only for the day of the booking until the midnight
* users with a **room booking** in the same day; WiFi access is granted only for the day of the booking until the midnight

{% hint style="info" %}
WiFi access for users with **bookings** is granted via the WiFi portal only for the day of the booking and it is valid until the midnight of the same day. Accounts are not deleted in Cusna, but simply disabled; if the same user attempts to retrieve access on another day for a new booking, it will be reactivated.
{% endhint %}



#### Supported features:

* **Traffic separation**: when enabling VLAN management for Andcards, Cusna automatically creates Groups for each Company. Members of the same company are assigned to the same VLAN so their traffic is secured and their devices can reach each others.
* **Roaming**: when enabling Roaming, users can connect to all Locations using the same passphrase



## Andcards setup

Login in your Andcards account as an admin, go to **Product** **Settings**, and select **API Credentials**\


<figure><img src="../../.gitbook/assets/image (223).png" alt=""><figcaption></figcaption></figure>

Copy the **Client ID** and the **Client Secret**.&#x20;

## Setting up the integration in Cusna

Go to **Setting** and scroll to the **Integrations** section. Click **New Integration**. Select Andcards.

Enter the following values:

* Client ID
* Client Secret

<figure><img src="../../.gitbook/assets/image (209).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.&#x20;

Once your integration is active, only for some WiFi vendors, you have the option to enable or disable the automatic management of VLANs for users provisioned via this integration.

<figure><img src="../../.gitbook/assets/image (238).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can easily share the link to the Location WiFi Portal is to create a dedicate information box in the Information section of each location:\
\
![](<../../.gitbook/assets/image (165).png>)


{% endhint %}
