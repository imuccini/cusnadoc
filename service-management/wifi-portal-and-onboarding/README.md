# WiFi Portal & Onboarding

Residents can self-enroll in the service on the WiFi Portal.

Each Network has a WiFi Portal with a **dedicated URL**, that you can copy either in the Network summary table or in the detail page of each Network.

<figure><img src="../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

The URL can be distributed to Residents by different channels:

* QR codes
* email
* existing tenant portals
* dedicated SSID with captive portal

When Tenants are initialized manually via the Cusna dashboard, they receive a notification email that confirm they have been activated and it includes the link to the WiFI Portal related to the Network associated with their account.

{% hint style="info" %}
You can optionally publish the WiFi Portal as a dedicated **onboarding SSID** on your WiFi network. [Learn more](wifi-portal-distribution.md).
{% endhint %}

{% hint style="info" %}
If you prefer to distribute one single URL, you can enable the **Universal WiFi Portal URL**. [Learn more](wifi-portal-options.md).
{% endhint %}



You can also enable a [Universal WiFi Portal URL](wifi-portal-options.md#universal-wifi-portal-url), a single URL that can be distributed to all residents. n the first page, they will have to pick the locaiton where they want to login.



## Resident onboarding experience

Residents might receive an Activation Email with the link to the WiFi Portal, similar to the following one, when they are manually provisioned form the Cusna dashboard.

<figure><img src="../../.gitbook/assets/image (248).png" alt="" width="375"><figcaption></figcaption></figure>



When they visit the **WiFi Portal page**, they might have multiple options to identify themselves:

* Passwrodless login (must be [enabled in the Access Control options](access-control-options.md#passwordless-login))
* SSO authentication with an Identity Provider (must be [enabled in the Access Control options](access-control-options.md#identity-provider-options))

#### Passwrodless login

In this case, the user is prompted to enter their email address.

If the email address exists and it is associated to an valid and active account, they will receive an email containing the **magic link** to access the WiFi portal in one click.

<figure><img src="../../.gitbook/assets/image (249).png" alt="" width="375"><figcaption></figcaption></figure>

By clicking the Login button, the user lands directly in the WiFi Portal already authenticated.



#### SSO authentication

In case an integration with a cloud IdP has been enabled in the [Access Control options](access-control-options.md#identity-provider-options), the user has the option to select this method. The user is redirected to the external identification page of the IdP and upon successful identification till return to the WiFi Portal to continue the onboarding process.



### First access

On the first access to the portal, users are invited to accept the [T\&C](../general-options/organization-details.md) and other personal attributes as configured in the [Access Control](access-control-options.md#contact-profile-collection) options (such as first name, last name, company).

<figure><img src="../../.gitbook/assets/image (252).png" alt="" width="375"><figcaption></figcaption></figure>

Once accepted the T\&C, the user lands on the WiFi Portal home page.&#x20;

When [Billing](../../add-ons/billing.md) is enabled, the user might be prompted to select a Subscription and provide payment information before being activated and get access to the personal PSK.



### WiFi Portal home screen

The home page contains different panels that might be visible or not depending on the options configured in the Cusna dashboard. In particular:

* **Personal WiFi passphrase**: this section is always visible and provides the user the name of the PSK network and the personal PSK. The user can&#x20;
  * re-generate the passphrase (if enabled as option in the [WiFi Portal settings](wifi-portal-options.md#allow-users-to-re-generate-their-wifi-passphrase)),&#x20;
  * view a QR code that can be scanned to connect directly to the network
  * and copy the passphrase to the device clipboard
* [**Passpoint**](access-control-options.md#passpoint)**:** if Passpoint is enabled and the portal is opened on an Passpoint compatible device, this panel offer the option to directly download a Passpoint profile that works on the same secure WiFi network
* [**Guest WiFi**](wifi-portal-options.md#allow-users-to-create-a-wifi-passphrase-for-guests): if enabled in the general options, the user can enable a dedicated passphrase that can be provided to guests
* [**Your Devices**](access-control-options.md#allow-users-to-register-legacy-devices): if enabled, allows users to manually provision devices via their MAC address



<figure><img src="../../.gitbook/assets/image (72).png" alt=""><figcaption><p>WiFi Portal screenshots in desktop and mobile views</p></figcaption></figure>



