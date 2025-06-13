# Oracle Opera Cloud

{% hint style="info" %}
This is a Beta feature only for partners and customer with access to the Beta Program
{% endhint %}

**Oracle Opera Cloud** integration enables guests to self-onboard by identifying themselves via **Last Name** and **Room Number** from the WiFi portal. If they have a valid reservation, they receive a personal WiFi Passphrase, which is automatically deactivated at the end of their room stay.



### Cusna setup

Go to Integrations and click **New** in the Integration card, then select **Opera Cloud**.

Enter the following data:

* **Hostname**: full hostname of your instance, including https://
* **Client ID**
* **Secret**
* **Enterprise ID**

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Settign up networks for each Hotel

When you create a Network, you need to enter your **Hotel ID** in the Hotel ID field.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Enabling SSO via Oracle Opera Cloud

Go to **Setup**, **Onboarding** and enable the toggle next to Oracle Opera Cloud

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

## User experience

The WiFI portal can be distributed via in-room QR codes or published on a dedicated SSID as a captive portal.

Guests can sign in using their Last Name and Room number and get immediate access to the portal where they’ll can find their personal WiFi passphrase. If PAN is enabled, all devices connected with the same PSK will be in the same network segment (e.g. mobile phones, laptops and personal headless device such as gaming consoles, medical devices, etc..)



<figure><img src="../../.gitbook/assets/operaUX.gif" alt=""><figcaption></figcaption></figure>

