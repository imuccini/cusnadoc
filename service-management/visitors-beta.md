# Visitors (beta)

{% hint style="info" %}
This is a beta feature. Contact us if you are interested.
{% endhint %}

## Use Case

Daily Visitors or external visitors than than need an extended temporary access have now the option to self-onboard via the WiFi Portal.

Daily Visitors gets temporary access until the end of the day and then get automatically disabled.

You can also provide visitor the option to request an access extension, specifying a reason and a desired date. Admins will be notified and can handle the request by denying or grating the extension.&#x20;



## Setup

Go the **Setup** > **Onboarding** page and enable the option **Allow Visitors to Self-Onboard**.

<figure><img src="../.gitbook/assets/image (310).png" alt=""><figcaption></figcaption></figure>

In the **Visitors Registration Attributes**, you can specify the list of perosnal information that you want to collect form the visitor in the onboarding form.

You can optionally enable the capability to let visitors request an access extension, but enabling the option **Allow visitors to ask for access extension**. In this case you need to specify one or more Admins that will be notified of the request in the field **Admins to be notified for the extension request**.



## Visitors experience

When a visitors lands on the WiFI Portal, a new button "I am a visitor" appears in case the option is enabled.

<figure><img src="../.gitbook/assets/image (313).png" alt="" width="375"><figcaption></figcaption></figure>



After clicking "**I am a Visito**r", the user see a registration page.

Email is always mandatory. The rest of the form attributes depends on the attributes defined in the Setup section.&#x20;

The use can tick the option "**I need Wifi access beyond today**" to request an extension. In this case a desired termination date and a reason need to be specified.

<figure><img src="../.gitbook/assets/image (315).png" alt="" width="375"><figcaption></figcaption></figure>

The user then receives a verification email with a magic link to access the WifI portal and retrieve his personal WiFi Passphrase. Visitors only the the section of the WiFI Portal related to the Personal Passphrase, while all other sections, such as device management, are not available.



## Approval process

All configured admin receive a notification email with the summary fo the extension request and they can click a link to manage the request directly.

In case of pending requests, the dashboard also shows on the top a card with all the pending requests to be handled. The Admin can simply click on **Accept** or **Decline** buttons to quickly handle the request or click on the name of the Requester to open the Visitor page and change the termination date manually to any desired date.

<figure><img src="../.gitbook/assets/image (317).png" alt=""><figcaption></figcaption></figure>

All the handled request actions are logged in the Audit logs.

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>
