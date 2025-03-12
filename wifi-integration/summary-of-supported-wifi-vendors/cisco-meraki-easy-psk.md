# Cisco Meraki Easy PSK

{% hint style="info" %}
This is a Beta feature only for partners and customer with access to the Beta Program
{% endhint %}

Traditional RADIUS-based iPSK relies on MAC authentication, requiring each device to be pre-onboarded individually to collect its MAC address. While onboarding through a captive portal can simplify the process for non-headless devices, it still requires manually collecting and adding the MAC addresses of headless devices (such as smart TVs, printers, smartwatches, etc.), which can be challenging. Additionally, the MAC addresses of many personal devices may change over time due to the aggressive MAC randomization and rotation policies in modern operating systems.



**Cisco Meraki Easy PSK** is a new solution that leverages RADIUS authentication while overcoming the limitations of traditional MAC-based authentication. The RADIUS platform performs a user lookup by analyzing the EAPOL parameters included in the RADIUS request to identify potential user matches.

Key Advantages of This Approach:

* **Scalability:** Supports deployments larger than 5,000 users, overcoming the limit of Meraki iPSK without RADIUS, which supports up to 5,000 iPSKs per network.
* **Seamless Roaming:** Enables users to roam across any network deployed within the project without reauthentication issues.
* **Selective PAN Enforcement:** In multi-network deployments, Cusna can enforce Personal Area Network (PAN) segmentation on specific networks, such as a user’s home network. For example, in a large campus with multiple networks, a user can connect with their iPSK anywhere, but PAN enforcement applies only when connected to their dormitory network.
* **Advanced Connection Logs and Reports:** Provides detailed RADIUS authentication and accounting logs for improved visibility and auditing.
* **Wired Device Support:** Allows devices connected via switch ports to be authorized using MAC authentication. Since PAN cannot be implemented via WPN (which is incompatible with switches), Cusna can be configured to use VLANs for PAN deployment.
* **Granular Network Policies:** Enforces advanced policies through RADIUS AAA, beyond dynamic group policies. This includes the ability to limit the maximum number of devices per user and restrict the number of concurrent device  per user.



## Meraki Setup

Each **Location** in Cusna is associated to a **Network** in the Meraki dashboard.&#x20;

1. Create a Network in Meraki as described in the official [Meraki documentation](https://documentation.meraki.com/General_Administration/Organizations_and_Networks/Creating_and_Deleting_Dashboard_Networks).
2. Next, you need to create an SSID configured to support Easy PSK. Navigate to **Wireless** > **Configure** > **SSIDs**, enable an SSID from the list and rename it with your desired network name, e.g. "_Residents WiFi_". Click **Save Changes** at the bottom of the page.
3. On the desired SSID, click "**edit settings**" link to navigate to the **Access Control** page for this SSID.
4. On the Access control Page, Select **Identity PSK with RADIUS** under **Security** and in the dropdown select **Easy PSK**\
   \
   ![](<../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1).png>)\

5. Set **Wi-Fi Personal Network (WPN)** to **Enabled**
6. Click **Save changes** on the bottom of the page.



<details>

<summary>IoT SSID - optional</summary>

If you need to support [IoT Devices Authentication](../../service-management/wifi-portal-and-onboarding/iot-devices-authentication.md) via MAC authentication, you need to add an additional dedicated SSID in each of the Networks configured for the service.

1. Navigate to **Wireless** > **Configure** > **SSIDs**, enable an SSID from the list and rename it with your desired network name, e.g. "_IoT Devices_". Click **Save Changes** at the bottom of the page.
2. On the above SSID, click "**edit settings**" link to navigate to the **Access Control** page for this SSID.
3. On the Access Control page, select **Identity PSK without RADIUS** under **Security** \
   ![](<../../.gitbook/assets/image (39).png>)
4. Select "None (direct Access)" in the Splash Page section\
   ![](<../../.gitbook/assets/image (40).png>)
5.  Finally, expand the **RADIUS** section and add Primary and Secondary RADIUS data for both the **RADIUS servers** and **RADIUS Accounting servers** sections.\
    The RADIUS data (IP addresses, Ports and Secrets are delivered as part of your onboarding email).\


    <figure><img src="../../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>



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

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Next, you need to setup at least one **Network Policy**.  Once you have set up the Meraki integration, the **Network Policy** section appears.

{% content-ref url="../../service-management/network-policies.md" %}
[network-policies.md](../../service-management/network-policies.md)
{% endcontent-ref %}



## Scenarios: multi-network deployments

Imagine a large campus divided into multiple **Meraki Networks** for easier management, with separate networks for areas such as dormitories, public spaces, parks, and faculty buildings.

In the dormitories, each room has its own access point (AP) along with Ethernet outlets connected to floor-level switches. In this scenario, the best technology for managing **Personal Area Networks (PANs)** is VLANs, since switches do not support WPN.

* **Wireless Devices:** Students connect their wireless devices using **PPSK (Easy PSK)**, allowing seamless connectivity across all campus networks.
* **Wired Devices:** Devices connected via the Ethernet outlet in a student’s room are authenticated using **MAC authentication**, and require an onboarding process.

When a student connects devices (wired or wireless) from the **dorm network**, the RADIUS server assigns a unique VLAN to ensure all of that student’s devices are on the same network, creating an isolated PAN.

However, when the student connects their wireless devices to other networks on campus (outside the dorms), the devices are still authorized but without any specific VLAN enforcement. Instead, they inherit the VLAN defined by their **Group Policy** or the default VLAN assigned to the SSID.



<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Wired Devices Onboarding

Wired devices can be onboarded in two different ways.

Headless devices must be manually provisioned by the user on their [WiFi portal](../../service-management/wifi-portal-and-onboarding/iot-devices-authentication.md), adding their MAC address and reference friendly name.

Non-headless devices, once connected to the ETH port, can be blocked and prompted to a captive portal to enroll the device.

1. The user enters his email address
2. Form another device, open the email and click the link
3. Give a name to the device and approve it.
4. Disconnect and reconnect the cable device to the ETH port

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

