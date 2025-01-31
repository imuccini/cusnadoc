# Access Control options

Open the **Setup** menu group and select **Onboarding**. In the **Access Control** section, you can find all the options to control the way users can signup and login into the service via [WiFi Portal](./).

***

### **Passwordless Login**

**Passwordless Login** allows to enable the option to identify existing users by means of their email address. If the email address is associated to an existing Account, the user will receive a magic link via email that allows to access the WiFi Portal in one click. This option is automatically enabled when the Email Domain Whitelist option is enabled.

<figure><img src="../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure>

### **Email domain whitelist**

The **Email domain whitelist**, allows all users whose email address contains any of the domain listed in this configuration, to sign-up directly in the WiFi portal by simply entering their email address and clicking the magic link sent to their email. If they click the link within 5 minutes, they'll enter in the WiFI Portal onboarding wizard, including the opt-in to privacy policy, fill in of minimum set of attributes required and, if enabled, going trough subscription plan selection and payment setup.

If the integration with an IdP that supports multiple group has been configured in the Setup page, this card includes also the IdP configuration options. These options might include:

* Label of the button that appears in the WiFi portal (e.g. "Login with your university account")
* Group Mapping rules: they allow to automatically map Groups configured in the IdP with Groups previously created in Cusna.

<figure><img src="../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>

### **Account registration**&#x20;

The **Accounts registration** option allows to define the minimum set of account attributes that are requested to the users when they enroll into the service via the WiFI Portal the first time.  Attributes that are available already trough the IdP integration are not asked again to the end users if they are already available.

<figure><img src="../../.gitbook/assets/image (296).png" alt=""><figcaption></figcaption></figure>

Among the available options, you can require users to select a **Unit**. The Unit dropdown displays a list of all Units within the Location the user is registering for, excluding those already assigned to other residents (regardless of their service status).

If the Phone Number is included among the profile attributes, you can require users to verify it via an OTP sent through SMS to their phone number. This option is available only if the Twilio integration is properly configured on the Integration page.

<figure><img src="../../.gitbook/assets/image (23).png" alt="" width="375"><figcaption></figcaption></figure>

### **Identity Provider options**

If you have integrated an external **identity provider**, this section also show its configuration options. First of all, you have the option to **enable or disable**  the SSO option on the WiFi Portal.&#x20;

You can also customize the label fo the button that appears to users in the WiFi portal, editing the **Login button Label** input.

Depending on the specific IdP, you might have additional other options, such as:

* [Group mapping](../../cloud-identity-platforms-integrations/enterprise-cloud-idps/group-mapping.md)

<figure><img src="../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>



### Allow users to register legacy devices

This option enabled users to add their own personal devices MAC addresses in the WiFi portal. Such devices are authenticated via MAC Authentication on a dedicated SSID properly configured.

{% hint style="info" %}
If you do not see this option in your account, contact us to enable it.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure>



### Passpoint

This option allow users to download a Passpoint profile on their compatible devices form the WiFi Portal. The Passpoint profile will autonomically connect provisioned devices to a dedicated SSID that must be properly configured.

{% hint style="info" %}
If you do not see this option in your account, contact us to enable it.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure>

### Automatic service suspension

This option allows you to define criteria for automatically suspending an account's service. Multiple options may be available, including:

* **Max active period**: In this case, you specify the maximum duration (in days) that an account remains active after activation.

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
