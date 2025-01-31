# Units

{% hint style="info" %}
At this time, Unit are supported only on Meraki, Extreme and Ruckus networks.
{% endhint %}

A **Unit** represents a living space of a **Network -** such as an apartment or a room in a multi-dwell environment - associated to a Tenant. You can associate to the Unit one Access Point.

When creating an Account, you can then assign the Account to a specific Unit, and the Access Point Ethernet port will be configured to be in the same Personal Area Network as the clients connecting using the PSK associated to the resident.



### How to configure and use Units

If supported in your account, you can enable **Unit** management in your **General** options page.

<figure><img src="../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>

By enabling Unit management, you'll find a new sub-menu in the Network menu group.

<figure><img src="../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

In the main Units page you see the list of all Units, which can be filtered by Network. By click the button Add, you can create a new Unit specifying:

* the **Network**
* a reference **Name**
* an optional **Floor** number,  just for inventory purposes
* an Access Point



By **deleting a Unit**, all the ETH ports of the Access Point associated to the Unit will be disabled. &#x20;



### Managing Account

If Units management is enabled, when crating an Account of type "Tenant" you have the option to associate the Resident to one of the Units of the Network the Account belongs to.

<div align="left"><figure><img src="../.gitbook/assets/image (245).png" alt="" width="375"><figcaption></figcaption></figure></div>

You can also associate a Unit to existing Account that do not have a Unit assigned yet.

When the service of an Account is terminated or the Account is deleted, all the ETH Ports of the Access Point associated to the Unit the Account was associated with will be disabled.

Changing the Passphrase associated to the Account does not affect the reachability of the devices connected via the ETH ports of the AP. &#x20;



#### Enabled Ports

When the Port Management feature is enabled, for supported hardware only (at this time Meraki only), you can set which ethernet ports of the Access Point are enabled or disabled.

<figure><img src="../.gitbook/assets/image (36).png" alt="" width="375"><figcaption></figcaption></figure>



## Under the hood

Learn the details of how ti works for the different WiFi vendors

<details>

<summary>Meraki</summary>

Currently, only MR36H access points are supported.

Whenever you link a Location to a Meraki Network, Cusna automatically initializes a default Port Profile with all ports disabled used as a&#x20;

Whenever you create a Unit, Cusna creates a related Port Profile in the Network corresponding to the Location the unit belongs to. By default, this Port Profile has no WPN ID assigned to the ports.

As soon as a Unit is associated to an Account, the Port Profile associated to the Unit is updated assigning to ports the same WPN ID as the one associated to the Account.

</details>

<details>

<summary>Extreme Networks</summary>

Currently, only AP302W access points are supported.

Whenever you initialize an Account and associate it to a Unit, Cusna automatically assign the ETH ports of the AP to the Private Client Group associated to the Account

</details>

<details>

<summary>Ruckus SmartZone (beta)</summary>

Whenever you initialize an Account and associate it to a Unit, Cusna automatically configure  the ETH ports of the AP with the same VLAN associated to the Account. If the Account is a Group Member of a Group with a VLAN, the VLAN of the Unit takes priority.

</details>





