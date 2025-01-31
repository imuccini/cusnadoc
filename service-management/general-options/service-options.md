# Service Options

In the **Setup** **> General** page, the card **WiFi Service Options** provide additional optional configuration and options that can be enabled on the account.



### Dynamic PAN orchestration

Under the **Dynamic PAN orchestration** section you can configure the default strategy and to assign and manage Personal Area Networks fo Accounts. &#x20;

Personal Area Networks allows to create virtual network segment where all clients of the same Account are in network among each other but isolated from other users.

PAN can be achieved either via VLANs or, when supported, leveraging proprietary L2 segmentation artifacts (such as WPN in Meraki, UDN in Cisco or PCG in Extreme Networks). &#x20;

<figure><img src="../../.gitbook/assets/image (336).png" alt=""><figcaption></figcaption></figure>

The options are:

* **Auto**: Cusna automatically assign a PAN to each Account
* **Manual**: PANs can be assigned only manually by Admin in the dashboard
* **None**: PAN are not assigned to accounts wither manually or automatically (the related PAN features are disabled form the interface)

By default, all new Cusna account are set to Auto.

{% hint style="info" %}
This option might not available for some vendors. For example, when using Meraki cloud iPSK, PAN is achieved relying on the native WPN artifact and there is no need for any configuration in this section.
{% endhint %}

\
When you select "**Auto**," you have multiple strategy you can adopt, also depending on the features you enabled in your project.

* **Unique per Account**\
  Cusna automatically assigns a PAN (Private Area Network) to the Account during activation. \
  By default, each Account is assigned a unique PAN within the Network where it is activated (within the range configured n the Network settings). This ensures no two Accounts share the same PAN in that Network.

> **Note**: If the "[Roaming](service-options.md#roaming)" option is enabled, PAN uniqueness is extended across the entire Organization instead of being limited to individual Networks. When VLANs are used in this mode, the total number of unique PANs is limited to 4096, which may impact large-scale projects.

* **Unit-Based Assignment**:\
  If the "[Unit](service-options.md#units)" option is enabled, you can assign a PAN to an Account based on the specific Unit associated with it.
* **Group-Based Assignment**:\
  If the "[Group](service-options.md#groups)" option is enabled, you can assign a PAN to an Account based on the Group it belongs to.



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

When enabled, Cusna dynamically assigns a unique VLAN to each account in the organization. this means that there cannot be two account with the same VLAN in the same organization. When the user connect with its PSK to the WiFi of any Network, the same VLAN will be used to tag his traffic.

When Roaming community option is disabled, the automatic VLAN assignment works on per Network scope. When a new account is created, either manually or automatically via the integrations, Cusna assign a VLAN that is not used already in the Network where the account is initialized.

{% hint style="danger" %}
Once enabled, the Roaming  option cannot be disabled. Switching on and off this option could cause duplicate assignment of VLAN to accounts.
{% endhint %}



### Groups

This options allows to enable or disable [Groups](../groups.md) management on the account. This option is available only for WiFi vendors that support Groups

<figure><img src="../../.gitbook/assets/image (308).png" alt=""><figcaption></figcaption></figure>



### Units

This options allows to enable or disable [Unit](../units.md) management on the account. This option is available only for WiFi vendors that support Unit based assignment of Access Points

<figure><img src="../../.gitbook/assets/image (309).png" alt=""><figcaption></figcaption></figure>

For supported vendors only, you may also have the option to enable the ability to asign different ports of the same Access Point in the Unit to different Accounts. To enable this capability you need to turn on the option **Assign individual ETH Ports to Accounts**.

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>



### Passphrase Options

This option allow to define options related to the WiFi passphrase automatically generated by the system

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

* the length of the WiFi passphrase&#x20;
* the set of characters used to generate the passphrase

{% hint style="info" %}
The default character set is optimized to exclude easily confusable characters:\
23456789ABCDEFGHJKLMNPRSTUVWXYZabcdefghijkmnopqrstuvwxyz
{% endhint %}



### Automatic service termination

This feature enables the configuration of options to automatically suspend accounts.

The Max Duration setting allows administrators to specify the number of days after activation when an account will be automatically suspended.

<figure><img src="../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

### Service termination notice

This option allows to send residents an email a configurable number of days before their service is scheduled for automatic termination.

<figure><img src="../../.gitbook/assets/image (335).png" alt=""><figcaption></figcaption></figure>
