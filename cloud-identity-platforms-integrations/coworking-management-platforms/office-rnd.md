# Office RnD

Office RnD integration allow co-working members to self-provision their secure WiFi access.

Members can visit the WiFi Portal - which URL is different per Location - login with their credentials to access and/or change their personal WiFi passphrase.

If the user belongs to a Team, Cusna creates a matching Group and assign a static VLAN that will be assigned to all members of the same team, so their traffic is segregated from other teams and users.

When users are removed from office RnD, they are also autaotmically removed from Cusna and their WiFi access is disabled.



## Office RnD setup

in Office RnD, go to **Settings**, **Developer Tools**. Click **Add application**. \
The **Add Application** dialog appears.

![](<../../.gitbook/assets/image (153).png>)

Enter a **Name** and select **Read** and **Write** in the Permission section. Click Add to save the application.

In the main page, you'll the app you've just created in the table. Click **View**. The **View Application** dialog appears.

<figure><img src="../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

Copy the **Client ID** and **Client secret** values.



Go to Setting, Account and open the tab General.&#x20;

&#x20;

<figure><img src="../../.gitbook/assets/image (185).png" alt=""><figcaption></figcaption></figure>

Take note of the value you see in the input **Admin Site**.

<figure><img src="../../.gitbook/assets/image (128).png" alt=""><figcaption></figcaption></figure>



## Setting up the integration in Cusna

Go to **Setting** and scroll to the **Integrations** section. Click **New Integration**. Select **Office RnD**.

Enter the following values:

* Client ID
* Client Secret
* Slug

Click **Setup**.

<figure><img src="../../.gitbook/assets/image (237).png" alt=""><figcaption></figcaption></figure>
