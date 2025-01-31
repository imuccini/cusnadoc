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
   ![](<../../.gitbook/assets/image (150).png>)\

3. From **Active Directory** (now Microsoft **Entra ID)** in the Azure Portal, and select **App Registration**. Click on the app you just created
4. From the **Overview** page, copy the **Application** (**Client) ID** and the **Tenant ID**
5. Click **API Permissions** and select **+ Add Permission**
6.  **Select Microsoft Graph** and click on **Application Permissions**\
    \


    <figure><img src="../../.gitbook/assets/image (221).png" alt=""><figcaption></figcaption></figure>
7. Select the permissions
   1. _Group.Read.All_
   2. _User.Read.All_
8. Click **Grant admin consent for .... \<yourComapnyName>**
9. Click on **Certificates and Secrets**, click on  + **New Client Secret**. Enter a name and click Add.
10. Copy the value "_**Value**_" of the secret (not the Secret ID). This value will be shown only once.\




### Cusna Setup

Go to Integrations and click **New** in the Integration card. Select **Microsoft**.

Enter the **Client ID**, **Secret** and **Tenant** ID of your Microsoft App. Pick the default **VLAN** that will be assigned to all authorized members.

<figure><img src="../../.gitbook/assets/image (230).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.

<figure><img src="../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

You can click **Edit** to change the parameters of the integration at any time.
