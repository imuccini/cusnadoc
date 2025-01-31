# Cambium cnMaestro

## cnMaestro setup

First step, you need to create a WLAN configured to support  ePSKs.&#x20;

Form the **Configuration** menu, select **WiFi Profiles**. Open the **WLANs** tab.

Add a new WLAN. Set the **Name** and the **SSID** (e.g. "Residents WiFi"). Set the Security to WPA2 Pre-Shared Key and change the default Passphrase with a complex value (no one will use this passphrase).

Set **Client** **Isolation** to **Disable** (each resident will have its own VLAN and all the devices will be able to communicate regardless of the AP they are connected to)

![](<../../.gitbook/assets/image (216).png>)

{% hint style="warning" %}
Cusna implements an automatic VLAN management to segregate each resident traffic. Cusna uses by default the slot of VLANs 2000-4000 so you should avoid using these VLANs for any other purposes.
{% endhint %}

Once you have a **WLAN** you can assign it to one or multiple **AP Groups**.&#x20;

ePSK are managed at the WLAN level by cnMaestro, so if you assign the same WLAN to multiple AP groups (for example on different Network), a user will be able to connect to WiFi with the same ePSK on all the APs where such WLAN is deployed.



**Distributed communities scenario**

If you want users to be able to connect with the same ePSK in multiple Networks (or AP groups), you should create one WLAN and assigned to multiple AP groups.&#x20;

In Cusna you can still create a dedicated Network for each physical site, even if multiple Networks are assigned to the same WLAN profile. In the alternative, you can create a single "virtual" Network matching all the AP groups where the WLAN is deployed.

In Cusna, an Account is always associated with one Network. If the Account visits a different Network where the same WLAN is deployed, he would be able to connect with the same ePSK.&#x20;

If you are assigning VLANs to the Account, the same VLAN should be enable on all the sites.

In Cusna, an email address can be associated to ONLY one Account in the same Organization.



**Isolated communities scenario**

If you want to create isolated communities, where a user is able to connect only in one specific Network, you need to create a dedicated WLAN for each AP Group (assuming you are using a dedicated AP Group per each Network).

Note that a user, with the same email, cannot exists with different Accounts on different Networks.



## Cusna setup

To connect Cusna to your Cambium account you need to get the **hostname** of your cnMaestro account. You can easily identify the hostname form the URL base of your browser once you are logged in in your cnMaestro account.

![](<../../.gitbook/assets/image (139).png>)

Then you need to generate an API Client and retrieve a client ID and Client Secret. Go to **Network Services** and open **API Client**

![](<../../.gitbook/assets/image (146).png>)



Click Add API Client and fill the Basic Information form as follow:

* **Name**: any name, such as _Cusna_
* **Description**: any text such as _Cusna_
* **Expiration Time**: Cusna will refresh the API access automatically, but we recommend enter a greater value than the default one, such as 10000
* **Token Renewal** Time: enter the same value as entered above

Click **Save**.

Copy the Client ID and Client Secret that appear on the screen after saving

![](<../../.gitbook/assets/image (234).png>)



Go to Settings in your Cusna account and select Cambium (cnMaestro).

Enter the requested value;

* hostname
* Client ID
* Client Secret

Click **Setup**.

<figure><img src="../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

After clicking **Setup**, you'll see the Cambium integration in the list.

<figure><img src="../../.gitbook/assets/image (215).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
You can change the Client ID and Client Secret in future, but you can't change the account hostname
{% endhint %}

## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **WLAN** that you have enabled on the Access Point of the related to property.



![](<../../.gitbook/assets/image (175).png>)

###

### Creating Accounts

When you create a new Account, a new PSK user will be created in your cnMaestro account with a predefined WiFi Passphrase. The Account of type Tenant and Visitors, receive an activation email with the default passphrase and QR code, and a link to the **WiFi Portal** where can change the passphrase.

{% hint style="danger" %}
To avoid synchronization problems, do not manage manually the ePSKs in the cnMaestro interface
{% endhint %}

