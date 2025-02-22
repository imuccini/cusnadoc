# Passpoint

Passpoint option allows resident to download a Passpoint profile directly form the WiFi portal, on their supported devices. Passpoint will work on all the access points part of the customer network.

## Network Setup

To enable Passpoint you need to create and or configure a dedicated Passpoint-enabled SSID on your network.

To find step by step user guides on how to configure your WiFi network, please refer to our Core Paltform user guides:

* [Aruba Central](https://cloud4wi.zendesk.com/hc/en-us/articles/21805428506893-Aruba-Central-Passpoint-configuration)
* [Cisco Catalyst 9800](https://cloud4wi.zendesk.com/hc/en-us/articles/10531050431885-Cisco-Catalyst-9800-Passpoint-configuration)
* [Cisco Meraki](https://cloud4wi.zendesk.com/hc/en-us/articles/4413079885069-Meraki-Passpoint-configuration)
* [Extreme CloudIQ](https://cloud4wi.zendesk.com/knowledge/articles/5945572850189/en-us?brand_id=2977846\&return_to=%2Fhc%2Fen-us%2Farticles%2F5945572850189)
* [Forinet Fortigate](https://cloud4wi.zendesk.com/hc/en-us/signin?return_to=https%3A%2F%2Fcloud4wi.zendesk.com%2Fhc%2Fen-us%2Farticles%2F6031652408077-Fortinet-FortiGate-Passpoint-Configuration)
* [more...](https://cloud4wi.zendesk.com/hc/en-us/articles/18939388439309-Passpoint-Network-Configuration)

To configure the network you need some parameters, including:

* RADIUS IP/Secret/Ports
* Passpoint Realm

You can find these parameters in the **Setup**, **Integration** page of your Cusna dashboard. On the WiFi Network card find **Show RADIUS data**.

<figure><img src="../.gitbook/assets/image (365).png" alt=""><figcaption></figcaption></figure>

The dialog RADIUS Information provides all the data you need to configure your network.

<figure><img src="../.gitbook/assets/image (366).png" alt=""><figcaption></figcaption></figure>



## Enabling Passpoint onboarding

Go to **Setup**, **Onboarding** and find the **Passpoint** card. Click the toggle to enable Passpoint onboarding.

<figure><img src="../.gitbook/assets/image (364).png" alt=""><figcaption></figcaption></figure>

## User experience

In the WiFi Portal, the Resident will see a Passpoint panel.

<figure><img src="../.gitbook/assets/image (367).png" alt=""><figcaption></figcaption></figure>

By Clicking Enroll, the user is redirected to the Passpoint Enrollment page, that guides the in the process of downloading and installing the Profile certificate ([learn more](https://cloud4wi.zendesk.com/hc/en-us/articles/4413031728781-WiFi-Profile-Download-Page))

