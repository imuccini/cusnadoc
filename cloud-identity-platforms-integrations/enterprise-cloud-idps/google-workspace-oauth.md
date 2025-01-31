# Google Workspace (oAuth)

Google integration allows to connect Cusna with your Google Workspace account to let user self-onboard via the WiFi Portal. When relyon og Google as IdP, Cusna support two main onboardign workflows:

* **Google SSO**:  users are redirected to your organization Google authenticaiton screen
* **Passwordless** **identification**: users enters their email address and if it is present in your Google directory and authroized, the user receives a magic link on his email to access the WiFi Portal



## Google Cloud Setup

You need a Google Cloud account and a Project.

### 1. Create a Project

If you do not have an existing project suitable for this purpose, start by creating a new project. \
Form the main dashboard, click the menu next to the Google Cloud logo and select "**+ New Project**".

<div align="left"><figure><img src="../../.gitbook/assets/image (62).png" alt="" width="375"><figcaption></figcaption></figure></div>

Once you have a Project, make sure it is selected in the main dropdown next to the Google Cloud logo.

<div align="left"><figure><img src="../../.gitbook/assets/image (63).png" alt="" width="375"><figcaption></figcaption></figure></div>

### 2. Setup the OAuth Consent Screen

Next, go to **API & Services** and open **OAuth consent screen** to configure the consent screen.

<div align="left"><figure><img src="../../.gitbook/assets/image (64).png" alt="" width="375"><figcaption></figcaption></figure></div>

In the first step of the **OAuth consent screen** dialog, select **Internal** as **User Type**.

<div align="left"><figure><img src="../../.gitbook/assets/image (286).png" alt="" width="375"><figcaption></figcaption></figure></div>

Next, fill in all the information about app name, privacy policy and terms, app domain and logo. In this section, in the **Authorized domains** section, insert:

* `cusna.io`

<div align="left"><figure><img src="../../.gitbook/assets/image (58).png" alt="" width="375"><figcaption></figcaption></figure></div>

In the second step of the wizard, **Scopes**, add the following scopes by clicking "**Add or Remove Steps**":

* `/auth/userinfo.email`
* `/auth/userinfo.profile`

Usually, you'll find these Scopes at the beginning of the list of scopes that appears on the right panel.

<div align="left"><figure><img src="../../.gitbook/assets/image (60).png" alt="" width="375"><figcaption></figcaption></figure></div>

Once selected, click **Update** and they will be listed in the main screen in the table "**Your non-sensitive scopes**".

<div align="left"><figure><img src="../../.gitbook/assets/image (59).png" alt="" width="375"><figcaption></figcaption></figure></div>



### 3. Setup Credentials

Once finalized the configuration of the OAuth consent screen, go to **API & Services** and open **Credentials**.

<div align="left"><figure><img src="../../.gitbook/assets/image (65).png" alt="" width="375"><figcaption></figcaption></figure></div>

Select "**+ Create Credentials**" and pick "**OAuth client ID**".&#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (66).png" alt="" width="375"><figcaption></figcaption></figure></div>

The **Create OAuth client ID** page appears. For **Application type** select **Web application**. \
Define a Name that users will see in the authentication screen.

<div align="left"><figure><img src="../../.gitbook/assets/image (67).png" alt="" width="375"><figcaption></figcaption></figure></div>

In **Authorized JavaScript origins** enter the following list of values:

* [https://cusna.io](https://cusna.io)

In **Authorized redirect URIs**, enter the following list of values:

* [https://www.cusna.io/oauth2?target=user](https://www.cusna.io/oauth2?target=user)
* [https://www.cusna.io/oauth2?target=admin](https://www.cusna.io/oauth2?target=admin)



At the end of the process, select the credential you just created in the main page to view its details. On the right side of the page find a copy:

* **Client ID**
* **Client secret**

<div align="left"><figure><img src="../../.gitbook/assets/image (55).png" alt="" width="375"><figcaption></figcaption></figure></div>

You'll need the Client ID and Client secret later to finalize the setup in the Cusna dashboard.



### 4. Enable APIs & Services

Finally make sure to have enabled the proper API services. Go to Enabled APIs & Services and make sure to have in the list:

* Admin SDK APIs

If this API is not in your list, click **+ Enable APIs & Services** and in the new page find and enable Admin SDK APIs.



## Setup Cusna

### Enable Google integration

Go to **Setup** > **Integrations** and click **New Integrations** in the **Identity Providers** card.  Select **Google Account**.

<figure><img src="../../.gitbook/assets/image (53).png" alt=""><figcaption></figcaption></figure>

Enter your Google Cloud domain in the **Domain** filed.

Fill the **Client ID** and **Client secret** inputs with the values created in the step above.

A User with Google Admin permissions needs to click on the **Setup** button to authorize the app.&#x20;

On click, a new widows opens up int he browser, where the user is redirected to login with Google and then  to accept the required permissions and scopes on behalf of the organization.

{% hint style="info" %}
The app requires permissions that not all Google users in your organizations might have. We advise that the same user who initialized the app in the Google Cloud console also to complete this step.
{% endhint %}

### Advanced configurations

Once the Google integration is complete, go to **Setup**, **General** in the **Access Control & Onboarding** card.

Here you can configure advances options such as:

* Label for the button that appears in the WiFi Portal
* Configure [Group Mapping](group-mapping.md) rules
* Enable access only for users that belong to one of the mapped groups



