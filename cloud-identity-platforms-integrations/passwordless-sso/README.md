# Passwordless SSO

At Cusna, we are big believers that password are complicated and we do smooth user experience avoiding to use them.

A simpler yet effective and secure method to enable self-serve onboarding while preserving security is to:

1. Let a user enter its email in the WiFi Portal
2. Cusna checks via APIs in external systems (IdPs, CIAMs, any platform) if the email exists and is associated to an individual with the right permissions.
3. If the user exists and is authorized, Cusna creates the Account and send a secure magic link to the user email - which proves the user owns the email
4. The user clicks the magic link and get access to the Tenant Portal where gets access to the WiFi passphrase



### Passwordless SSO workflow

<figure><img src="../../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>

When [**Groups**](../../service-management/groups.md) is enabled, if the external identity system reports the user belongs to a group, Cusna automatically associates the user to an equivalent group (which is also created automatically if it doesn't exists already).



{% hint style="info" %}
Cusna can integrate with literally everything. Contact our team to learn more.&#x20;
{% endhint %}
