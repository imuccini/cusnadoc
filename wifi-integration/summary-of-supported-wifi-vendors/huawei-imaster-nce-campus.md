# Huawei - iMaster NCE-Campus

## iMaster NCE setup

First step, you need to create a Site and add your Device ([follow this guide](https://support.huawei.com/enterprise/en/doc/EDOC1100141254/c0c36c2b/creating-a-site)). In general, you would have a Site for each property.

**Enable PPSK on the site.**

1.  Choose **Provision > Device Configuration > Site Configuration** from the main menu.\
    \


    <figure><img src="../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>
2. In the displayed window, select a site from the **Site** drop-down list in the upper left corner.
3. Choose the **Site Configuration** tab.\
   ![](<../../.gitbook/assets/image (91).png>)
4. Configure authentication points based on the device type **AP**
   1.  Choose **AP** > **SSID** from the navigation pane, click **Create**, and configure basic information about an SSID.\


       <figure><img src="../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>
   2. On the Basic Settings step, enter an name for the SSID. Switch on the **Global DHCP address pool** option.
   3.  On the **Security Authentication** tab, set **Authentication mode** to **Semi-open network**, select **PSK/PPSK/SAE/SAE-PSK**, and set **Key type** to **PPSK**. \
       Then, set **Encryption mode**, **Encryption algorithm** and **Escape policy**. \
       Leave the option **Automatic MAC address binding** disabled.\
       \


       <figure><img src="../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
Cusna implements an automatic VLAN management to segregate each resident traffic. Cusna uses the slot of VLANs 2000-4000 so you should avoid using these VLANs for any other purposes.
{% endhint %}



## Cusna setup

#### Get the account hostname

To connect Cusna to your Huawei Cloud Campus account you need to get the **hostname** of your Cloud Campus account. You can easily identify the hostname form the URL base of your browser once you are logged in in your Cloud Campus account.



#### Create User with API access

You need to create a **User** with API access. To do so, go to **System**, **User Management**.

Click **Create New User**, the Create User wizard appears.

On the first step, Set Information, select **Third Party** as **Type**.

![](<../../.gitbook/assets/image (154).png>)

In the **Select Roles** step, make sure the add the role **Open API Operator** and **Tenant Administrator**

![](<../../.gitbook/assets/image (235).png>)

#### Connect Cusna to Huawei Cloud Campus

Go to Settings in your Cusna account and select Huawei (Cloud Campus).

Enter the requested value;

* **hostname**\
  E.g. if your Cloud Campus URL is [https://weu.naas.huawei.com/](https://weu.naas.huawei.com/), enter "_weu.naas.huawei.com_"
* **username**
* **password**

![](<../../.gitbook/assets/image (121).png>)

Click **Setup**.



{% hint style="info" %}
You can change the Client ID and Client Secret in future, but you can't change the account hostname
{% endhint %}

## Operating Cusna



### Creating Networks

When you create or edit a Network in the Cusna dashboard, in the WiFi configuration section, you have to pick the **Site** and the **SSID** that you have enabled on the Access Point of the related to property.



### Creating Accounts

When you create a new Account, a new PSK user will be created in your Cloud Campus account with a predefined WiFi Passphrase. The Resident receives an activation email with the default passphrase and QR code, and a link to the Resident Portal where he can change the passphrase.

