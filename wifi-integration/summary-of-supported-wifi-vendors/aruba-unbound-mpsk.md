# Aruba - Unbound MPSK

{% hint style="info" %}
Requires AP with Firmware **AOS 10.4.x** or above
{% endhint %}

Traditional RADIUS-based iPSK relies on MAC authentication, requiring each device to be pre-onboarded individually to collect its MAC address. While onboarding through a captive portal can simplify the process for non-headless devices, it still requires manually collecting and adding the MAC addresses of headless devices (such as smart TVs, printers, smartwatches, etc.), which can be challenging. Additionally, the MAC addresses of many personal devices may change over time due to the aggressive MAC randomization and rotation policies in modern operating systems.

**Aruba Central Unbound MPSK** is a new solution that leverages RADIUS authentication while overcoming the limitations of traditional MAC-based authentication. The RADIUS platform performs a user lookup by analyzing the EAPOL parameters included in the RADIUS request to identify potential user matches.



## Aruba Central Setup

To get Start with Cusna, you need to initially configure properly a **WLAN** on your Aruba Central dashboard. You can create multiple WLANs and associated them to different **Networks** in Cusna.\


1. Setup a **Group** for your project, configuring it with **ArubaOS 10** architecture\
   ![](<../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1).png>)\

2. Select the **Config** wheel to start configuring the Group\
   <img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" data-size="original">\

3. Under **Security Tab** add the Radius Authentication Server:\
   Enter a **Name**, such as _CusnaRADIUS_\
   IP Address: \<can be retrieved in the Cusna Dashboard>\
   Secret: \<can be retrieved in the Cusna Dashboard>\
   Auth Por: 1812\
   Accounting Port: 1813\
   ![](<../../.gitbook/assets/image (9) (1).png>)\

4. Next, select the **WLAN** tab and then the Plus sign next to add SSID\
   ![](<../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)\

5. There are many parameters that can be customized at your discretion.  For now, we will create a simple WLAN network. Type in a **SSID** name (ESSID) and click Next
6. On the next screen, select **Static** on **Client VLAN Assignment**, enter a **VLAN**  - based on your specific deployment setup - and click **Next**
7.  In the **Security** tab, under **Key Management**, select **MPSK-AES** and then pull down on the **Primary Server** setting to select the Radius Server you configured above \


    <figure><img src="../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>
8. Expand the **Advanced Settings** and go down and disable **802.11r**\
   ![](<../../.gitbook/assets/image (4) (1) (1) (1).png>)\

9.  Click **Next** two more times and your WLAN SSID with MPSK AES should be complete.\


    <figure><img src="../../.gitbook/assets/image (7) (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The Aruba Central dashboard currently does not permit manual enabling of WLAN for Unbound MPSK. However, Cusna will automatically update the WLAN configuration once you link your Cusna and Aruba Central accounts using the steps below.
{% endhint %}



## Cusna setup

To connect Cusna to your Aruba Central account, you need to generate an API Key in your Aruba Central account:

1. At the **Global** level, select **Organization** and then **Platform Integration**
2. Chose [**REST API**](https://app-uswest5.central.arubanetworks.com/frontend/#/APIGATEWAY)\
   ![](<../../.gitbook/assets/image (5) (1) (1).png>)![](<../../.gitbook/assets/image (6) (1) (1).png>)
3.  In the first tab, make sure to take note of the **API hostname** for  your account, such as "[apigw-uswest5.central.arubanetworks.com](https://apigw-uswest5.central.arubanetworks.com)" (take only the hostname, without "https://")\


    <div align="left"><figure><img src="../../.gitbook/assets/image (11).png" alt="" width="375"><figcaption></figcaption></figure></div>
4. Choose **My Apps and Tokens** tab. Create a Token.
5.  Copy the **Client ID** and **Client Secret**. \


    <figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>
6.  Then, in the Token List table, click **Download Token** and Copy the **Access token** and **Refresh Token** (It is good for 2 hours)\


    <figure><img src="../../.gitbook/assets/image (13).png" alt=""><figcaption></figcaption></figure>

Once the key is generated, complete the integration in the Cusna dashboard:

* Log in to your Cusna account and click **Setting**.&#x20;
* Expand the **WiFi setup** card, select **Aruba Central**&#x20;
* Enable the toggle **Easy PSK via RADIUS**
* Enter :
  * your API GW URL
  * client ID
  *   client Secret

      <figure><img src="../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>
* Click **Authorize**. The **Authorize integration** dialog appears. \
  Enter your **Access Token** and **Refresh Token** and click **Authorize**.\
  \
  ![](<../../.gitbook/assets/image (14).png>)\
  \
  \


{% hint style="warning" %}
Unbound MPSK mode cannot be enabled manually on Aruba Cen**tral**.

When you connect a Cusna Network with a WLAN and SSID, Cusna programmatically enables the Unbound MPSK mode on the SSID via APIs.

**If you make a change to the SSID  on the Central dashboard, it will lose the Unbound MPSK support.**

To re-enable it, go to Cusna dashboard, **Setup** > **Integration** and click **Edit** on the Aruba integration card. Click **Enable Unbound MPSK on SS**ID.

![](<../../.gitbook/assets/image (4) (1) (1).png>)\


On the next dialog select your **Group** and **SSID** and click Setup. \
![](<../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png>)
{% endhint %}

