# Engenius Cloud

{% hint style="warning" %}
You need an AP Pro license to use Cunsa with Engenius Cloud
{% endhint %}

{% hint style="info" %}
To enable Engenius Cloud on your account [contact support](mailto:support@cloud4wi.com).
{% endhint %}

## Engenius setup&#x20;

Login to your [Engenius Cloud](https://cloud.engenius.ai).

You need to create an SSID properly configured to support multiple PSK.

Go to **Configure** and select **SSID** and set a **Name** (eg. Residents WiFi).

On **Security Type**, select **WPA2-PSK** and then check the box **WPA2-MyPSK**.  Enter a long complex default passphrase (it wont be used).

Select **Cloud MyPSK Users** in the select menu.

![](<../../.gitbook/assets/image (133).png>)

Once you have the SSID properly configured, you can deploy it on your access points.\


{% hint style="warning" %}
Cusna implements an automatic VLAN management to segregate each resident traffic. Cusna uses the slot of VLANs 2000-4000 so you should avoid using these VLANs for any other purposes.
{% endhint %}

## Cusna setup

To connect Cusna to your Enginus Cloud account you need to get the Enginus API Key.

Click on your avatar icon and select **API Key**. Enter a name (e.g. Cusna) and click "**Generate new API key**.

![](<../../.gitbook/assets/image (160).png>)

Copy your API Key.

Login in your [Cusna](https://cusna.io) account ad go to **Settings**. Select Enginus and enter the **API Key** in the input field. Click **Setup**.



## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **Network** and the **SSID** that you have enabled on the Access Point of the related to property.



### Creating Accounts

When you create a new  Account, a new PPSK user will be created in your Engenius account with the personal WiFi Passphrase.

{% hint style="info" %}
The default, initial WiFi Passphrase is the resident phone number!
{% endhint %}







