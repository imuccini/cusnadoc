# Passpoint

Cloud4Wi integration allows to bring to Cusna end users access to a secure network via WPA2 Enterprise and/or Passpoint, and optionally to enable access to the access networks in the OpenRoaming federation.



## Setup

In the Integration page, find the Secure WiFi by Cloud4Wi section and click WPN Name.

Enter the API credentials generated in your Cloud4Wi account.

* API Key
* API Secret
* Organization ID

<figure><img src="../.gitbook/assets/image (97).png" alt=""><figcaption></figcaption></figure>

Read this article to learn how to [create API credentials in Cloud4Wi](https://create.cloud4wi.com/dev-hub/api-reference/getting-started).





## Configuration

In the General options page, once you have your Cloud4Wi account connected, you'll see a panel SecureWiFi by Cloud4Wi.

Here you can opt to enable:

* WPA2 Enterprise
* Passpoint

<figure><img src="../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

When enabling 802.1X or Passpoint, for each Account of type Tenant that you create in Cusna, a matching WiFi account is created and kept in sync in your Cloud4Wi account.



## User experience

In the WiFi Portal, the Tenant will see two new panels:

* **802.1X**: name of the secure network and credentials
* **Passpoint**: link to download a Passpoint profile - only visible on Android and apple devices

<figure><img src="../.gitbook/assets/image (96).png" alt="" width="375"><figcaption></figcaption></figure>
