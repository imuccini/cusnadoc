# Extreme Networks

## Account preparation

To get started, you need to create a **Network Policy**.

{% hint style="info" %}
To lear more about restrictions and guidelines on how to use PCGs, please refer to the [ExtremeCloudIQ documentation](https://extremeportal.force.com/ExtrArticleDetail?an=000099731) and watch this [short video about PCGs](https://www.youtube.com/watch?v=1JiacjAIyt8).
{% endhint %}

Go to **Configure**, **Network Policies** and click **Add Network Policy**. Give the Policy a name, for example one that recalls the name of the Network.

![](<../../.gitbook/assets/image (126).png>)

Then, go to the Wireless Networks tab and create a new **Wireless Network** clicking on the icon "**+**". Give the network an **SSID** name, such as _Residents_.

As **SSID Authentication**, select **Private Pre-Shared Key**. Leave all the other fields as per the default settings.

You can optionally set a maximum number of devices per resident by enabling **Set the maximum number of clients per private PSK**.

Select the option **Private Client Group Option** and select **Key-based** as a sub-type.



![](<../../.gitbook/assets/image (174).png>)



## Account integration

To connect Cusna to your Extreme Cloud IQ account, you need to generate an API Access Token.

**Option 1.** Connect it directly from Cusna.

Go to **Setting**, **Integration** and select **Extreme form the vendor selection menu**. Click the **Generate an access token now** button.&#x20;

<figure><img src="../../.gitbook/assets/image (263).png" alt=""><figcaption></figcaption></figure>

A dialog opens and asks for your ExtremeCloudIQ username and password. Make sure to use an account with admin permissions.

<figure><img src="../../.gitbook/assets/image (264).png" alt="" width="375"><figcaption></figcaption></figure>

Click **Login**. If the credentials are correct, an Access Token will be generated. If your accoutn has access to multple Organizations, a dropdown will appear to let you select the the Organization.

Click **Save** to finalize the setup.



**Option 2**: manually generate a Token in ExtremeCloudIQ (requires an Extreme Networks Developer Portal account)&#x20;

In your ExtremeIQ dashboard, click on your avatar on the top bar and select **Global Settings**. Go to **API Token Management** and click the icon "**+**" to create a new token.

The **Client ID** is the Credentials value from **My Profile** > **Your API Developer Application** in the Extreme Networks Developer Portal.

<figure><img src="../../.gitbook/assets/image (266).png" alt="" width="375"><figcaption></figcaption></figure>

Open your Cusna dashboard and go to **Setting**, expand the WiFi setup card, select Extreme, enter your API **Access Token** and click **Save**.

![](<../../.gitbook/assets/image (119).png>)

## Operating Cusna

Once you have configured your Network Policy and Wireless Network, you can start operating your Cusna account.



### Creating Networkd

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **Network Policy** and **SSID** related to the Network.



![](<../../.gitbook/assets/image (193).png>)

{% hint style="warning" %}
This operation will create a dedicate Use Group in Extreme CloudIQ and enable it to the selected Network Policy.
{% endhint %}

#### Roaming configuration

If you want users to be able to connect with the same PPSK across multiple Network you simply need to assign the same Network policy to the Network you want to federate.





### Creating Accounts

When you create a new Account, a new PSK user will be created in your ExtremeCloud IQ Pilot account with a predefined WiFi Passphrase. The Account of type Tenant and Visitors receives an activation email with the default passphrase and QR code, and a link to the WiFi Portal where can change the passphrase.

{% hint style="danger" %}
To avoid synchronization problems, do not manage manually the PPSKs in the ExtremeCloud IQ Pilot interface
{% endhint %}





***

<details>

<summary>Under the hood</summary>

Cusna automates many configuration and processes on the Extreme dashboard.

1. When setting up the integration, Cusna initializes a **User Gro**up with a default name (Cusna-Default-PCG). All users will be created in the same user group
2. When initializing a Location in Cusna, the default **User Group** is automatically enabled on the **Network Policy** associated to the Location
3. When enabling an Account in Cusna, it creates a **User** in the default User Group&#x20;

</details>

