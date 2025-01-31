# Zyxel Nebula (Pro)

{% hint style="info" %}
To enable Zyxel Nebula on your account [contact support](mailto:support@cloud4wi.com).
{% endhint %}

## Nebula setup&#x20;

Login to your [Nebula portal](https://nebula.zyxel.com/)

First step, you need to create a Site and add your Device. In general, you would have a Site for each property.

Then, create an SSID (WiFi network) with DPPSK as an authentication method and fill in a very long complex backup key. \
Go to **Access point** –> **Configure** –> **SSID Overview** and set **WLAN security** = **DPPSK**\
\


![](<../../.gitbook/assets/image (177).png>)

\


## Cusna setup

To connect Cusna to your Zyxel Nebula account you need to get the Nebula API Key.

Go to **Site-Wide**, **General Setting** and scroll down to the end of the page until you find the **API Access** section.

Click Generate and then copy the **API token**.

![](<../../.gitbook/assets/image (107).png>)

Login in your [Cusna](https://cusna.io) account ad go to **Settings**. Select _Zyxel_ and enter the **API token** in the input field.

Click **Setup**.



## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **Site** and the **SSID** that you have enabled on the Access Point of the related to property.



### Creating Accounts

When you create a new Account, a new PPSK user will be created in your Nebula account with the personal WiFi Passphrase.

{% hint style="info" %}
The default, initial WiFi Passphrase is the resident phone number!
{% endhint %}



