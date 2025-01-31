# Ruckus SmartZone

Ruckus SmartZone integration is based on the DPSK  and relies on VLANs to differentiate resident Personal Area Networks.



## SmartZone setup

Each **Network** in Cusna is associated to a **Zone** and a specific **WLAN** in the SmartZone dashboard.&#x20;

1. Click the Wireless **LANS** tab.&#x20;
2. On the Wireless LANs screen, click the **+ Create** button. The Create WLAN Configuration appears.
3. Complete the **General Options** section of the screen
4.  In the **Authentication Options** section of the screen, be sure that the default selection of **Open** is selected.

    1.  In the **Encryptions Options** section of the screen, you must select "**WPA2**," which expands the section as follows:\


        <figure><img src="../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>
    2. The Algorithm field must be **AES**, which is the default.
    3. In the Passphrase field, enter a **passphrase** for the DPSK WLAN that you are creating, and make note of this passphrase. The minimum length is eight characters.
    4.  In the Dynamic PSK field, select **Internal**. Once you make this selection, DPSK is enabled, and the screen expands again, allowing you to complete the configuration of this section of the screen:



    <figure><img src="../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

    * In the DPSK Length field, enter a value that complies with the security policy of your company. The default is 62.
    * For DPSK Type, choose the option that complies with the security policy of your company. The default is Secure DPSK.
    * For DPSK Expiration, use the drop-down menu to select a value that complies with the security policy of your company. The default value is Unlimited.

\


## Cusna setup

{% hint style="warning" %}
Your SmartZone instance must have a valid SSK certificate in order to work with Cusna. Self signed SSL certificate might cause problems.
{% endhint %}

* Log in to your Cusna account and click **Setting**.&#x20;
* Expand the **WiFi setup** card, select **Rucksu SmartZone**
* Enter the **URL** fo your SmartZone instance. \
  If the URL of your smartzone look slike this:\
  [https://vsz71.ruckusdemos.net:8443/wsg](https://vsz71.ruckusdemos.net:8443/wsg/#m/externalServices|t/generalSettingsSms)\
  The URL is: _vsz71.ruckusdemos.net_
* Click the button **Connect**. A login dialog appear. Enter your Ruckus SmartZone credentials.
* Click **Authorize**. The dialog closes.
* Click **Setup** to finalize the integration





