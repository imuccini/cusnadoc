# Nexudus

Nexudus integration allow co-working customers to self provision their WiFi access.

Customers can visit the WiFi Portal - which URL is different per Location - and enter the email address associated with their account in Nexudus.

If the email matches with the email associated to a CoWorker in Nexudus, Cusna sends a magic link to the provided email to login into the WiFi portal. At this point the user will be able to see and change its own private WiFi passphrase.

When coworkers are removed from Nexudus, they are also deleted form Cusna automatically and their WiFi access suspended.

#### Teams

If the CoWorker belongs to a Team, Cusna creates automatically a Group matching the Team (if not existing already), and assign to the team member the same VLAN as the one of the other team members.

Go to Setup, General and select None in the VLAN settings to turn off automatic VLAN assignment.

#### Global Communities

Each Coworker can be associated only to one account in Cusna. If you want users to roam across your locations with the same WiFi passphrase, you need to enable the Global Communities option and configure your network accordingly.





{% hint style="info" %}
**Coming soon**

* Create an account for Visitors
{% endhint %}



## Setup

Nexudus integration relies on an access token that is generated one time using your account email and password.&#x20;

{% hint style="success" %}
Cusna does not store your credentials, they are used at runtime the first time only to generate the first access token.
{% endhint %}

In your Cusna account, go to **Setting** and scroll to the **Integrations** section. Click **New Integration**. Select **Nexudus**.

Enter your Nexudus account email and password and click **Setup**.

<figure><img src="../../.gitbook/assets/image (143).png" alt=""><figcaption></figcaption></figure>
