# Personal Area Networks (PAN)

{% hint style="info" %}
This option might not available for some vendors. For example, when using Meraki cloud iPSK, PAN is achieved relying on the native WPN artifact and there is no need for any configuration in this section.
{% endhint %}

In the **Setup** **> General** page, the card Personal Area Networks (PAN) provide the configuration options to enable the use of Personal Area Networks..

Personal Area Networks allows to create virtual network segment where all clients of the same Account are in network among each other but isolated from other users.



### Dynamic PAN orchestration

Under the **Dynamic PAN orchestration** section you can configure the default strategy and to assign and manage Personal Area Networks fo Accounts. &#x20;

PAN can be achieved either via **L2 VLANs** or, when supported, leveraging proprietary **L3 segmentation techniques** (such as WPN in Meraki, UDN in Cisco or PCG in Extreme Networks). &#x20;

<figure><img src="../../.gitbook/assets/image (352).png" alt=""><figcaption></figcaption></figure>

The first option allows to enable or disable the **Dynamic PAN** orchestration. Form the dropdown you can select between:

* **Yes** - Automatically assign PAN to new Accounts
* **No** - Do not assign PAN to new Accounts

If the WiFi vendor connected to your Cusna account supports multiple **PAN technologies** (VLANs or L3 proprietary solutions), a dedicated dropdown allows to select what PAN technology to use:

* L2 (VLANs)
* L3 (the name displayed changes based on the WiFI vendor)&#x20;



Next, the **PAN Assignment Policy** allows to set a rule to define which PAN assign to the Account, selecting among the following options:

* **Unique per Account**: the default option assign a unique PAN to each Account
* **Inherit form Group**: with the option, if the Account is assigned to a Group, and the group has a VLAN or L3 segmentation attribute assigned, the Account inherits the PAN form the Group.\
  &#xNAN;_&#x49;f the Group has not VLAN or L3 tag, the Account get assigned with a unique PAN._
* **Inherit form Unit**: If the "[Unit](personal-area-networks-pan.md#units)" option is enabled, you can assign a PAN to an Account based on the PAN cofnigure on the Unit assigned to the Account.\
  &#xNAN;_&#x49;f the Account is not assigned to any Unit or the Unit does not have a PAN configured, a unique PAN is assigned to the Account._&#x20;

### **Free up VLANs upon service termination**

This option removes the VLAN assigned to an Account upon service termination, making it available again in the associated VLAN pool.

<figure><img src="../../.gitbook/assets/image (337).png" alt=""><figcaption></figcaption></figure>

### Roaming

In some cases, you might want your users to be able to connect with the same WiFi passphrase in all your Networks.

{% hint style="info" %}
Some WiFi vendors allows to setup the PPSK configuration in such way that the PSKs works on multiple sites. For example, Juniper Mist has an option that allows to select if PSKs have a Site or Org level scope. In Cambium cnMAestro you can create one WLAN profile and assign it to multiple networks (AP groups).&#x20;

Refer to the section related to the configuration of the WiFi vendor to get more details on how to configure the network to support this use case.
{% endhint %}

In the **Setup**, **General** page, find the option **Roaming**.

<figure><img src="../../.gitbook/assets/image (225).png" alt=""><figcaption></figcaption></figure>

When enabled, Cusna dynamically assigns a unique VLAN to each account in the organization. This means that there cannot be two account with the same VLAN in the same organization. When the user connect with its PSK to the WiFi of any Network, the same VLAN will be used to tag his traffic.

When Roaming community option is disabled, the automatic VLAN assignment works on per Network scope. When a new account is created, either manually or automatically via the integrations, Cusna assign a VLAN that is not used already in the Network where the account is initialized.

{% hint style="danger" %}
Once enabled, the Roaming  option cannot be disabled. Switching on and off this option could cause duplicate assignment of VLAN to accounts.
{% endhint %}

