# Custom HTTP Request

You can easily integrate any external user directory by using the **Custom HTTP** identity verification method.

In the External Identity Provider section of the Setup page, create a new Integration and select **Custom HTTP Request**.

In the configuration panel, enter your endpoint URL where the request will be made.

<figure><img src="../../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

Cusna will make an **HTTP GET** request to the configured endpoint with the following parameters:

* **email**: email address the user inserted in the portal
* **locationid**: external id configured in the Network associated to the WiFi Portal

Example:

```
GET https://mycustomendpoint.com/users?email=email@cusna.io&locationid=1234
```

The GET Request also includes by default a custom header parameter tha tyou can use for futher validating the incoming requests and identifying the source Cusna account

* **x-cusna-organization**: \<id of your Cusna organization>

Cusna expects to receive as a response a JSON with the following content

```json
{
  "valid": true,
  "id": "1232423532523",
  "firstName":"Ivan",
  "lastName":"Muccini",
  "groupId":"employees12345",
  "groupName":"employees",
  "terminationDate":"01/08/2024"
}
```

* **valid:**  boolean, indicate if the account is valid or not (mandatory)
* **id**: external id of the record (optional)
* **firstName**: first name of the user (optional)
* **lastName**: last name of the user (optional)
* **groupId**: ID of the group the user belongs to, if any (optional)&#x20;
* **groupName**: name of the group the user belongs to, if any (optional)&#x20;
* **terminationDate**: date the account service will be automatically suspended 9optional)







