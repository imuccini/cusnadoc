# Getting Started

The Account Management API allows Cusna partners and customers or third-party systems to programmatically manage Accounts data in Cusna dashboard. Using the Account management API eliminates the need for property staff to manually enter data in the the dashboard.



## Base URL

All API requests must use the following base URL:

```
https://www.cusna.io/api/1.1
```



## Authentication&#x20;

To make API call you need an Access Token.

To get the Access Token make a request to the Auth endpoint

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (3).yaml" path="/auth" method="post" %}
[cusna-Cusna-1.0-resolved (3).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (3).yaml>)
{% endswagger %}

Authenticate API requests by adding in the header the parameter

```
Authorization: Barear <token>
```



## Organization ID

For some APIs, you need to provide your organization ID. YoOu can find the Organization ID in the Account page.

![](<../.gitbook/assets/image (231).png>)

