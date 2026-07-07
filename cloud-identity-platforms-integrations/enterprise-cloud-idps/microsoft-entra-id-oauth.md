---
description: (previously called Active directory)
---

# Microsoft Entra ID (oAuth)

Microsoft integration allows to connect Cusna with your Microsoft account.

Microsoft users in your enterprise account can directly enter their email in the WiFi Portal without any previous manual provisioning, or login with their Microsoft credentials.

If their email matches with a member in your Microsoft account, the user will receiver a magic link via email to access directly to the Portal and retrieve the personal WiFi PPSK.



### Microsoft account setup

1. Log in to Microsoft Azure click **Enterprise applications** > **New application**.
2. Click **Create your own application**, enter a name for the application, select **Integrate any other application you don't find in the gallery (Non-gallery)** and click **Create**.\
   \
   ![](<../../.gitbook/assets/image (150).png>)
3.  In your newly created Enterprise Application, go to Properties on the left menu, locate "**Assignment required**?", switch it to **No**, and click **Save**.&#x20;

    \
    If you instead want to explicitly restrict application login capabilities to a predefined list of authorized personnel or departments, switch to the **Users and groups** blade in the left-hand navigation menu. Click **+ Add user/group** from the top toolbar. Search for and select the specific users or security groups that require access to the application, then click **Assign**.


4. From **Active Directory** (now Microsoft **Entra ID)** in the Azure Portal, and select **App Registration**. Click on the app you just created
5. From the **Overview** page, copy the **Application** (**Client) ID** and the **Tenant ID**
6.  Click Authorization and select **+ Add a platform** and select **Web**.\
    Enter the following **Redirect URI**:\
    `https://www.cusna.io/oauth`\
    <br>

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
7. Click **API Permissions** and select **+ Add Permission**
8.  **Select Microsoft Graph** and click on **Application Permissions**\
    <br>

    <figure><img src="../../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>
9. Select the permissions
   1. _Group.Read.All_
   2. _User.Read.All_
10. Click **Grant admin consent for .... \<yourComapnyName>**
11. If not already enabled, also enable the User.Read Delegated permission. Click **+ Add a permission** again, select Delegated Permission and serach and enable _User.Read_
12. You final Configured permissions should look like the following screenshot

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
13. Click on **Certificates and Secrets**, click on  + **New Client Secret**. Enter a name, select an expiration period (e.g. 24 months) and click Add.
14. Copy the value "_**Value**_" of the secret (not the Secret ID). This value will be shown only once.\
    Note that the secret will expire at the selected time, and you'll need to go back to this cofniguration, generate a new Secret and update it in the Cusna integration<br>



### Cusna Setup

Go to **Integrations** and click **New** in the Integration card. Select **Microsoft**.

Enter the **Client ID**, **Secret** and **Tenant** ID of your Microsoft App. Pick the default **VLAN** that will be assigned to all authorized members.

<figure><img src="../../.gitbook/assets/image (375).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.

<figure><img src="../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

You can click **Edit** to change the parameters of the integration at any time.



### Next steps

Once you setup the integration, you need to enable it as an onboarding method. Go to Setup > Onboarding. You'll find on top of the page a card to configure the option of the IdP you've just created.

<figure><img src="../../.gitbook/assets/image (376).png" alt=""><figcaption></figcaption></figure>

Enable the toggle on the Microsoft Entra ID title to enable the integration.

* **Display SSO button**: publish the button on the WiFi portal that redirects the user to the Microsoft login page. You can customize the label of the button
* **Passwordless sign up**: enable the option for users to sign up simply using their email address. Upon entering their email address, Cusna verifies if the email exists on the Entra ID directly. If it does, the user receives a link via email to verify the ownership of the email and logs the user directly into his portal.
* **Group mapping**: check the dedicated [group mapping articles](https://app.gitbook.com/s/DvdioCJduzKTpzAv3Sij/cloud-identity-platforms-integrations) to learn how you can assign different network policies to different groups of users

