# TP-Link Omada

## Omada setup

For each Network you need to setup a Site in your Omada account.

Once you have the Site, create a WLAN network and an SSID.

Go to **Settings** > **Wireless Networks** and click **+ Create New Wireless Network**. And the **Network Name (SSID)**, for example "Residents WiFi".

Select **PPSK without RADIUS** in the **Security** dropdown.

On the PPSK Profile, you need to add create and assign at least one PPSK user in order to create the SSID. Click on the menu and select the last item, **Create new PPSK Profile**.

The **Create New PPSK Profile** dialog opens. Enter a **Name**, such as "_Default_". in the **PPSK1** section, enter as **Name** something like "_Default PPSK_" and in the **Passphrase** input enter a long, difficult to guess Passphrase.

![](<../../.gitbook/assets/image (227).png>)

Once you have create your default PPSK Profile, you'' return to the main screen, and select the profile just created in the dropdown **PPSK Profile**.

![](<../../.gitbook/assets/image (132).png>)

Click **Apply** to save.



{% hint style="info" %}
Cusna implements an automatic VLAN management to segregate each resident traffic. Cusna uses the slot of VLANs 2000-4000 so you should avoid using these VLANs for any other purposes.
{% endhint %}



## Cusna setup (Controller mode)

#### Get the account hostname

To connect Cusna to your Omada instance account you need to get the **hostname** of your instance. You can easily identify the hostname form the URL base of your browser once you are logged in in your Omada account.

![](<../../.gitbook/assets/image (207).png>)

In the screenshot above the hostname would be: _**omada.cusna.io:8043**_. Do not enter https. Make sure to enter the port if you see it in your URL.

{% hint style="warning" %}
If your controller has a self-signed SSL certificate, APIs return an error, so the integration won't work.
{% endhint %}



{% hint style="info" %}
Oamda uses the user credentials to generate the tokens required to authenticate the APIS. We suggest creating a dedicated API User to connect to Cusna.

Go to Admin and click +**Add New Admin Account**. Select **Cloud User** as **Administrator** **Type** and **All** as **Site Privileges**.
{% endhint %}



#### Link Omada to Cusna

Log in your Cusna account and go to Settings. In the WiFi integration section, select TP-Link.

Enter the requested inputs:

* **Omada tenant hostname**: the hostname of your Omada instance
* **Username**: username of the Omada admin user
* **Password**: username of the Omada admin user

<figure><img src="../../.gitbook/assets/image (196).png" alt=""><figcaption></figcaption></figure>



## Cusna setup (Cloud mode)

#### Get the account hostname

To connect Cusna to your Omada instance account you need to get the **hostname** of your instance. You can easily identify the hostname form the URL base of your browser once you are logged in in your Omada account.



<figure><img src="../../.gitbook/assets/image (224).png" alt=""><figcaption></figcaption></figure>

With reference to the screenshot above&#x20;

1. take the hostname part: "**use1-omada-controller.tplinkcloud.com**"
2. transform it as follow adding the "api" string: "_use1-**api**-omada-controller.tplinkcloud.com_"
3. Copy the **OmandacId** value, which is the string right after the first "/": "_5492cc657ffb80e24e8afe386f8ed4bb_"



{% hint style="info" %}
Oamda uses the user credentials to generate the tokens required to authenticate the APIS. We suggest creating a dedicated API User to connect to Cusna.

Go to Admin and click +**Add New Admin Account**. Select **Local User** as **Administrator** **Type** and **All** as **Site Privileges**.
{% endhint %}



#### Link Omada to Cusna

Log in your Cusna account and go to Settings. In the WiFi integration section, select TP-Link.

Enter the requested inputs:

* **Omada tenant hostname**: the hostname of your Omada account as indicated above
* **OmandacId**: the id of your account as indicated above
* **Username**: username of the Omada admin user
* **Password**: username of the Omada admin user



<figure><img src="../../.gitbook/assets/image (228).png" alt=""><figcaption></figcaption></figure>



## Cusna setup (Open APIs mode)

#### Setup an API Client



In Global View or MSP View, go to **Settings** > **Platform Integration** > **Open API**. 2. Click  **+ Add New App**. The Open API dialog appears.

<figure><img src="../../.gitbook/assets/image (327).png" alt=""><figcaption></figcaption></figure>

Enter a name in the **App Name**, select the following options:&#x20;

* **Mode: Client**&#x20;
* **Role**: **Administrator**
* **Site Privileges**: **All**

Click **Apply**.

<figure><img src="../../.gitbook/assets/image (328).png" alt=""><figcaption></figcaption></figure>

From the main page, copy the **Client ID** and **Client Secret**.

Click on the eye icon, to open the **View Open API** Attributes and copy the **Interface Access Address** and the **Omada ID**.

<figure><img src="../../.gitbook/assets/image (330).png" alt="" width="375"><figcaption></figcaption></figure>

#### Link Omada to Cusna

Log in your Cusna account and go to Settings. In the WiFi integration section, select TP-Link and select Open API in the Controller Mode.

Enter the requested inputs:

* Interface Access Address:
* Omada ID:
* Client ID:
* Client Secret:

<figure><img src="../../.gitbook/assets/image (331).png" alt=""><figcaption></figcaption></figure>



## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the Site, WLAN and SSID to associate to the property.

![](<../../.gitbook/assets/image (220).png>)

### Creating Accounts

When you create a new Account, a new PSK user will be created in your Omada account with a predefined WiFi Passphrase. The user receives an activation email with the default passphrase and QR code, and a link to the WiFi Portal where he can change the passphrase.

{% hint style="danger" %}
To avoid synchronization problems, do not manage manually the PPSKs in the Omada interface
{% endhint %}
