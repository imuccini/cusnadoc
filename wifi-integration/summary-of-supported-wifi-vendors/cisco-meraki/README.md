# Cisco Meraki

Cisco Meraki integration is based on the [iPSK without RADIUS](https://documentation.meraki.com/MR/Encryption_and_Authentication/IPSK_Authentication_without_RADIUS) feature, with support of [Wi-Fi Personal Network](https://documentation.meraki.com/MR/Encryption_and_Authentication/Wi-Fi_Personal_Network_\(WPN\)) (WPN) capabilities. It also relies on Group Policies to differentiate Tenant services (such as VLAN and bandwidth).&#x20;



{% hint style="info" %}
Cusna relies on iPSK without RADIUS and WPN is supported only on MR devices with 29.4.1+ firmware. However, to benefit form the possibility to manage up to 5,000 iPSK per SSID, you need to use firmware versions **MR 30.1 and newer**.

All APs in your network must be **Wi-Fi 5 Wave 2** (MR20, MR30H, MR33, MR42, MR42E, MR52, MR53, MR53E, MR70, MR74. MR84), **Wi-Fi 6** (MR28, MR36, MR36H, MR44, MR46, MR46E, MR56, MR76, MR78, MR86, MR45/55), **Wi-Fi 6E** (MR57, CW9162I, CW9164I, CW9166I) or newer.
{% endhint %}



## Meraki setup

Each **Location** in Cusna is associated to a **Network** in the Meraki dashboard.&#x20;

1. Create a Network in Meraki as described in the official [Meraki documentation](https://documentation.meraki.com/General_Administration/Organizations_and_Networks/Creating_and_Deleting_Dashboard_Networks).
2. Next, you need to create an SSID configured to support iPSK. Navigate to **Wireless** > **Configure** > **SSIDs**, enable an SSID from the list and rename it with your desired network name, e.g. "_Tenant WiFi_". Click **Save Changes** at the bottom of the page.
3. On the desired SSID, click "**edit settings**" link to navigate to the **Access Control** page for this SSID.
4. On the Access control Page, Select **Identity PSK without RADIUS** under **Security** and click on **Add an Identity PSK**
5.  Configure a name and passphrase; select a group policy.

    \
    ![](<../../../.gitbook/assets/image (182).png>)
6.  Set **Wi-Fi Personal Network (WPN)** to **Enabled**

    \
    ![](<../../../.gitbook/assets/image (208).png>)\
    \
    &#xNAN;_&#x4E;ote: The "Enabled/Disabled WPN" option is only displayed when at least one iPS group is configured._


7. Click **Save changes** on the bottom of the page.





<details>

<summary>IoT SSID - optional</summary>

If you need to support [IoT Devices Authentication](../../../service-management/wifi-portal-and-onboarding/iot-devices-authentication.md) via MAC authentication, you need to add an additional dedicated SSID in each of the Networks configured for the service.

1. Navigate to **Wireless** > **Configure** > **SSIDs**, enable an SSID from the list and rename it with your desired network name, e.g. "_IoT Devices_". Click **Save Changes** at the bottom of the page.
2. On the above SSID, click "**edit settings**" link to navigate to the **Access Control** page for this SSID.
3. On the Access Control page, select **Identity PSK without RADIUS** under **Security** \
   ![](<../../../.gitbook/assets/image (39).png>)
4. Select "None (direct Access)" in the Splash Page section\
   ![](<../../../.gitbook/assets/image (40).png>)
5.  Finally, expand the **RADIUS** section and add Primary and Secondary RADIUS data for both the **RADIUS servers** and **RADIUS Accounting servers** sections.\
    The RADIUS data (IP addresses, Ports and Secrets are delivered as part of your onboarding email).\


    <figure><img src="../../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>



</details>

## Cusna setup

To connect Cusna to your Meraki account, you need to generate an API Key in your Meraki account:

1. Navigate to **Organizations** > **Settings**.
2. Ensure the option **Enable access to the Cisco Meraki Dashboard API** is **enabled**.
3. Navigate to your profile by clicking your account email address in the upper-right > **My profile** to generate the API key.
4. Save this key in a secure location as it represents your admin credentials.



Once the key is generated from the Cisco Meraki dashboard:

* Log in to your Cusna account and click **Setting**.&#x20;
* Expand the **WiFi setup** card, select **Meraki**&#x20;
* Enable the toggle **Easy PSK via RADIUS**
* Enter your **API Key.**&#x20;
* The Organization menu will load the list of Meraki Organizations enabled on your API Kay; select the Organization that you want to link to your Cusna account.&#x20;
* Click **Save**.

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Next, you need to setup at least one **Network Policy**.  Once you have set up the Meraki integration, the **Network Policy** section appears.

{% content-ref url="../../../service-management/network-policies.md" %}
[network-policies.md](../../../service-management/network-policies.md)
{% endcontent-ref %}



