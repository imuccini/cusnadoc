# Group mapping

With some type of external connectors, Cusna allows to define static rules to assign external users to a destination Group in Cusna, based on some criteria.

In general, the feature allows to statically define the mapping form a source group id (which definition depends on the IdP used) and the destination Cusna [Group](../../service-management/groups.md).



{% hint style="info" %}
For most IdPs, you also have the option to make sure that only users that are mapped to a group are granted access to the service, by enabling the option **Authorize only members of mapped Groups**
{% endhint %}



### **Microsoft Entra (oAtuh)**

In case of Microsoft, it possible to crete rules that map the Azure Group ID into a Cusna Group. You can select the Microsoft Entra ID Group form a dropdown menu

<figure><img src="../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

### **Google (oAtuh)**

In case of Google, it possible to crete rules that map the Google Group  into a Cusna Group. You can select the Google Group form a dropdown menu.

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>



### **SAML**

In case of SAML integration, for most systems, it possible to crete rules that map the source Group  into a Cusna Group. You need to enter the SAML Group identifier manually in the Source Group ID input.

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption></figcaption></figure>

#### Microsoft Entra&#x20;

For Microsoft Entra ID, you need to enter the value of the Object ID of the Group that you can find the in the Azure Portal.&#x20;

<figure><img src="../../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>
