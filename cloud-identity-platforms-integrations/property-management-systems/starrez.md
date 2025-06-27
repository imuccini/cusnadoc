# StarRez

{% hint style="info" %}
This is a Beta feature only for partners and customer with access to the Beta Program
{% endhint %}

**StarRez** integration allows guests to self-onboard simply using their email address via the WiFi portal. If the email is linked to an active resident in StarRez, they receive a magic link granting access to the WiFi Portal where they can retrieve WiFi access details.

### Get started with your connector <a href="#get-started-with-your-connector" id="get-started-with-your-connector"></a>

Get your REST API Connection Settings:

1. Log in to StarRez and click on **Account** in the top left > Account
2. **Web Service** **Tokens** > **Create New**\
   \
   ![](<../../.gitbook/assets/image (1) (1) (1).png>)\

3. Enter a Name/description for the Token and set the **Expiry Date**. Make sure you copy the token from this screen. It cannot be viewed after you close this window and is not recoverable. \
   \
   ![](<../../.gitbook/assets/image (3).png>)\

4.  Refer to the API documentation to find your **Rest API URL** ([https://support.starrez.com/hc/en-us/articles/360056850292-StarRez-REST-2-0-Web-Services-API-Guide](https://support.starrez.com/hc/en-us/articles/360056850292-StarRez-REST-2-0-Web-Services-API-Guide))\
    Your StarRez system is usually hosted on a URL such as  format `https://yourinstitution.starrezhousing.com` or similar.\
    The REST API services typically reside under a `/StarRezREST` path, so the Rest API URL could be something like:

    `https://yourinstitution.starrezhousing.com/StarRezREST`


5. Keep a record of these credentials and the RestAPI URL



### Setting up Cusna

Go to Integrations and click **New** in the Integration card, then select **StarRez**.

Enter the following data:

* **RestAPI URL**
* **Access token**
*   **CheckOut Report Name** (optional):

    This is a custom report name that allows Cusna to retrieve daily the list of users who have checked out, in order to suspend their WiFi service.



<figure><img src="../../.gitbook/assets/image (374).png" alt=""><figcaption></figcaption></figure>

Click **Setup**.

{% hint style="info" %}
If the data provided is not correct, either the URL or the Access Token, you'll receive an error notification
{% endhint %}



### Enabling StarRez

In order to enable StarRez to let user register on the WiFi Portal, go to **Setup**, **Onboarding** and  enable on StarRez on the **Access Control** section.

<figure><img src="../../.gitbook/assets/image (373).png" alt=""><figcaption></figcaption></figure>
