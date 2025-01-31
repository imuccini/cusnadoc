# IoT Devices Authentication

{% hint style="danger" %}
This functionality is in beta access only. Contact our team to learn more.
{% endhint %}

In some cases, legacy headless devices cannot be easily connected to the WiFi by mean of a PSK, either because it is not supported by the device or because it might be too difficult to configure.

In such cases, devices can be manually provisioned for MAC Authentication.



### Device Onboarding

Users can find a dedicated card in their WiFi Portal called **Your Devices** where they can add and manage their personal IoT devices

<figure><img src="../../.gitbook/assets/image (307).png" alt=""><figcaption></figcaption></figure>

Clicking on the link "**How to find your device MAC address**" opens a screen with step by step instructions for the major streaming, gaming and assistant devices.

<figure><img src="../../.gitbook/assets/image (74).png" alt="" width="375"><figcaption></figcaption></figure>



Adding a devices only requires to specify

* a reference **Name**
* the **MAC address**

<figure><img src="../../.gitbook/assets/image (271).png" alt="" width="375"><figcaption></figcaption></figure>



### Setup

You can enable manual IoT device provisioning form the [WiFi Portal options](access-control-options.md#allow-users-to-register-legacy-devices) , enabling the toggle for the option "**Allow users register headless devices**"

In order to allow devices to authenticate via MAC authentication, you need to create a dedicated SSID (for example named "_IoT devices_") and configure it to support MAC authentication. RADIUS server parameters and vendor-specifc instruction are provided on demand by our support team.

When this option is enabled, the admin is prompted to specify which is the SSID dedicated for this service when setting up Networks, in the **IoT Network SSID** field (this field can be a dropdown or a simple input depending the WiFi vendor connected in the account)

<figure><img src="../../.gitbook/assets/image (306).png" alt=""><figcaption></figcaption></figure>

