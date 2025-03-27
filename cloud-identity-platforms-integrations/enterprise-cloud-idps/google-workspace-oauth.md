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

### 2. App Setup

Next, go to **API & Services** and open **OAuth consent screen** to configure the consent screen.

<div align="left"><figure><img src="../../.gitbook/assets/image (64).png" alt="" width="188"><figcaption></figcaption></figure></div>

Click **Get Started** to launch the setup wizard.

<div align="left"><figure><img src="../../.gitbook/assets/image (2) (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

1. In the first screen **App Information**, enter a **Name** for your App (e.g. "Cusna") and select a support email.
2. In the second step, **Audience**, select **Internal** and click Next.\
   \
   ![](<../../.gitbook/assets/image (3).png>)\

3. In the second step, **Contact Information**, enter an email address.
4. Go to the last step to access the terms and **Create** the App,

### 2. Branding

On the left sidebar, select **Branding**.&#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (1) (1).png" alt="" width="132"><figcaption></figcaption></figure></div>

Fill in the required data about privacy policy and terms, app logo. Scroll the page until you find the  **Authorized domains** section and enter your company domain ("company.com")

<div align="left"><figure><img src="../../.gitbook/assets/image (58).png" alt="" width="375"><figcaption></figcaption></figure></div>

Click **Save** at the bottom of the page to save settings.

### 3. Scopes

On the left sidebar, select **Data Access**. Add the following scopes by clicking "**Add or Remove Steps**":

* `/auth/userinfo.email`
* `/auth/userinfo.profile`

Usually, you'll find these Scopes at the beginning of the list of scopes that appears on the right panel.

<div align="left"><figure><img src="../../.gitbook/assets/image (60).png" alt="" width="375"><figcaption></figcaption></figure></div>

Once selected, click **Update** and they will be listed in the main screen in the table "**Your non-sensitive scopes**".\
\
![](<../../.gitbook/assets/image (5).png>)



### 4. Setup Credentials

On the left sidebar, select **Clients**.&#x20;

Select "**+ Create Credentials**" and pick "**OAuth client ID**".&#x20;

<div align="left"><figure><img src="../../.gitbook/assets/image (3) (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

The **Create OAuth client ID** page appears. For **Application type** select **Web application**. \
Define a **Name** that users will see in the authentication screen.

<div align="left"><figure><img src="../../.gitbook/assets/image (67).png" alt="" width="375"><figcaption></figcaption></figure></div>

In **Authorized JavaScript origins** enter the following list of values:

* [https://cusna.io](https://cusna.io)

In **Authorized redirect URIs**, enter the following list of values:

* [https://www.cusna.io/oauth?target=user](https://www.cusna.io/oauth2?target=user)
* [https://www.cusna.io/oauth2?target=admin](https://www.cusna.io/oauth2?target=admin)

At the end of the process, a dialog will show you the credentials you've just created. Copy the Client ID and Client Secret, as you'll need them in the next steps to finalize the setup in the Cusna dashboard.

<div align="left"><figure><img src="../../.gitbook/assets/image (4).png" alt="" width="375"><figcaption></figcaption></figure></div>

### 5. Enable APIs & Services

Finally make sure to have enabled the proper API services. Go to **Enabled APIs & Services** form the main sidebar menu.

<div align="left"><figure><img src="../../.gitbook/assets/image (6).png" alt="" width="188"><figcaption></figcaption></figure></div>

Make sure to have in the list:

* **Admin SDK APIs**

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



