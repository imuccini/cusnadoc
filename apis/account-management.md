# Account management

You can List, Create, Edit and Delete Accounts using these endpoints.



## Model

A sample **Account** object is below

```json
{
    "organization":"1654740730258x343197985783152640",
    "building": "T2",
    "email": "cusnaresident2@gmail.com",
    "externalID": "1234456",
    "firstName": "Happy",
    "lastName": "Resident",
    "passphrase": "mypersonalpassphrase3",
    "phone": "4156234444",
    "stopDate": "2023-06-09T02:12:11.858Z",
    "tenantServiceStatus": "Active",
    "terminationMode": "Schedule stop date",
    "unit": "1112"
}
```

## Managing Accounts

List all Accounts

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (4).yaml" path="/obj/resident" method="get" %}
[cusna-Cusna-1.0-resolved (4).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (4).yaml>)
{% endswagger %}

Create and activate new Accounts. The activation email is sent automatically on the service activation date.

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml" path="/obj/resident" method="post" %}
[cusna-Cusna-1.0-resolved (4) (1).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml>)
{% endswagger %}

Edit an Account

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml" path="/obj/resident/{id}" method="patch" %}
[cusna-Cusna-1.0-resolved (4) (1).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml>)
{% endswagger %}

Delete an Account and terminate automatically its service

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml" path="/obj/resident/{id}" method="delete" %}
[cusna-Cusna-1.0-resolved (4) (1).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (4) (1).yaml>)
{% endswagger %}





## Send activation email

Send again the activation email to an Account

{% swagger src="../.gitbook/assets/cusna-Cusna-1.0-resolved (2).yaml" path="/sendactivationemail" method="post" %}
[cusna-Cusna-1.0-resolved (2).yaml](<../.gitbook/assets/cusna-Cusna-1.0-resolved (2).yaml>)
{% endswagger %}



