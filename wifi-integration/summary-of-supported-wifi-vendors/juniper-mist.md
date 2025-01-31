# Juniper (Mist)

## Account preparation

For each property you need to create a new **Site**.

Go to **Organization**, **Site Configuration** and click **Create Site**. Give the site a name, for example one that recalls the name of the property, and click **Save**.

![](<../../.gitbook/assets/image (206).png>)

Go to **Sites** and select **WLANs**. Click **Add WLAN**.

Give the **SSID** a name, such as "Residents WiFi".

On the Security card, select **WPA-2/PSK with multiple passphrases**.&#x20;

Select **Local** or **Cloud** as a source.

Enable the checkbox next to **Configure as a personal WLAN**.



![](<../../.gitbook/assets/image (115).png>)

## Account integration

To connect Cusna to your Mist account, you need to generate an API Access Token and to retrieve your Organization ID.

Go to **Organization** and select **Settings**.

In the top left card, you can find the Organization ID. Copy it because you'll need to enter it later in the Cusna dashboard.

![](<../../.gitbook/assets/image (214).png>)



Scroll down to the end of the page until you find the card **API Token**. Click **Create Token**.

Give the token a name, such as "Cusna" and select **Network Admin** as **Access Level**.&#x20;

In the **Site Access** setting, select **All Sites**. Click **Generate**.

![](<../../.gitbook/assets/image (190).png>)

Copy the value that appears in the Key input and save it. You'll need to enter it in the Cusna dashboard.





Open your Cusna dashboard and go to Setting, expand the WiFi setup card, select **Juniper (Mist)** and enter your **API Token** and your **Organization ID**

<figure><img src="../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

On PSK Mode, you can select among the following options:

1. **Org Level**: with this option, PSKs will be created at the Organization level, meaning that users could use them to connect to any Site.
2. **Site Level**: with this option, each PSK will be valid only on the Site for which it is initialized.

{% hint style="warning" %}
When you select Org Level PSKs, Cusna Accounts are still associated with an initial Network. However, their WiFi passphrase will be working across all Networks/Sites.
{% endhint %}



## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **Site** and SSID related to the property.



![](<../../.gitbook/assets/image (123).png>)



### Creating Accounts

When you create a new Account, a new PSK user will be created in your Mist account with a predefined WiFi Passphrase. The Account of type Tenant and Visitor receive an activation email with the default passphrase and QR code, and a link to the Tenant Portal where can change the passphrase.

{% hint style="danger" %}
To avoid synchronization problems, do not manage manually the multi PSKs in the Mist interface
{% endhint %}

