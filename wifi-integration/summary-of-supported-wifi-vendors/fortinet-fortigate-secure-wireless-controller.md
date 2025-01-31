# Fortinet (FortiGate Secure Wireless Controller)

## FortiGate Secure Wireless Controller setup

You need to manually create the WLAN/s you want to use to run Cusna on.

1. Go to **WiFi and Switch Controller** (or simply **WiFi Controller**, depending on your licenses) > **SSIDs** and edit an existing SSID you want to use or create a new one.&#x20;
2. In **Security Mode**, select **WPA2 Personal**.&#x20;
3. In **Pre-shared Key**, select **Multiple** as the **PSK mode**
4. Next, you need to select at least one **MPSK Profile** (otherwise the SSID will switch back automatically to Single PSK mode once you save the configuration).\
   You can select any existing MPSK Profile if you have one, Cusna will create a new one automatically once integrated with your Fortigate and assign it to this SSID. \
   If you don't have any existing MPSK Profile, create a new one:
   1. In the MPSK Profile dropdown, select **+ Create** . The **New MPSK Profile** dialog appears.\
      ![](<../../.gitbook/assets/image (69).png>)
   2. Enter any value in the **Name** file, such as "Default"
   3. In the **MPSK Group list** section, click **+Add** and select Create Group. The **New MPSK Group** dialog appears.\
      ![](<../../.gitbook/assets/image (70).png>)
   4. Enter any value in the **Name** file, such as "Default"
   5. In the **MPSK Key list** section, click **Create  Key** and select Create Group. The **New MPSK Key** dialog appears.\
      ![](<../../.gitbook/assets/image (71).png>)
   6. Enter any value for **Name** and a 10 character string for **Pre-shared key**.
   7. Save all the configurations until you go back to the list of SSIDs.



{% hint style="danger" %}
After the initial setup, the MPSK Profile assigned to the SSID will be managed automatically by Cusna. Do Not change the MPSK Profile manually on this SSID.
{% endhint %}

{% hint style="warning" %}
You Fortigate controller need to have a valid SSL certificate and be reachable over the internet at a specific hostname or static IP address.

If you encounter any certificate related error during setup, please contact our support.
{% endhint %}



## Cusna setup&#x20;

Log in your Fortinet system with admin access. Click **System** > **Administrator**. Click the button **+ Create New** and select **REST API Admin**.

![](<../../.gitbook/assets/image (111).png>)

In the **New Rest API Admin** page, enter a **Username**.

Then select or create a new **Administrator Profile** with the **Read/Write** permissions for **WiFi & Switch** Access Control category.

Disable **PKI Group**.

Enable **CORS Allow Origin** and enter **https://cusna.io**

Click **OK** and copy the **API Key** shown in the right panel. The API Key will be shown only once, so make sure to copy it on a note.

![](<../../.gitbook/assets/image (141).png>)



Open your Cusna dashboard and go to Setting, expand the WiFi setup card, select **Fortinet** and in the setup panel enter your:

* **hostname** (eg. 207.45.23.34 or fortigate.example.com)
* **port** (e.g. 45)
* **API** Key

<figure><img src="../../.gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.

If any of the provided integration attributes are wrong, you'll get an error.
