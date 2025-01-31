# Network Policies

For some WiFi vendors, you need to setup Network Policies before creating Tenants. The section Network Policies in the Integration page appears automatically based on the WiFi vendor you set up.

## Meraki

While creating an iPSKs, Meraki require to set a Group Policy. By creating Network Policies, Cusna automatically creates and keeps in sync the Group Policies in the Meraki account for all the network involved (one network per each Network)

<figure><img src="../.gitbook/assets/image (184).png" alt=""><figcaption></figcaption></figure>

Click **Add a new Policy**.

The New Network Policy dialog appears. Fill the form

* name: reference name for the policy (e.g. "Default")
* bandwidth downlink: max downlink spee in Kbps
* bandwidth uplink: max downlink spee in Kbps
* VLAN

<figure><img src="../.gitbook/assets/image (348).png" alt="" width="375"><figcaption></figcaption></figure>

Click **Save**.

The Network Policies create appears in the list.

<figure><img src="../.gitbook/assets/image (349).png" alt=""><figcaption></figcaption></figure>



### Using Network Policies

Once you have created network policies, you can use them in different ways.

First of all, whenever you create a Network, you'll be required to assign a "default" network policy. This is the policy that will be assigned by default to Accounts associated to that Network whenever the network policy is not specified on the Account during initialization.

<figure><img src="../.gitbook/assets/image (261).png" alt=""><figcaption></figcaption></figure>

When creating a new account manually, you can opt to use the Network default network policy, or you can manually pick one of those you have already initialized in setup.

<figure><img src="../.gitbook/assets/image (262).png" alt="" width="375"><figcaption></figcaption></figure>

You can also assign a Network Policy to a group. This will be assigned to all Accounts of type "_group member_" assigned to this group.

<figure><img src="../.gitbook/assets/image (260).png" alt="" width="375"><figcaption></figcaption></figure>

Finally, you can also assign Network Policies individually to each Accoutn when creating or managing them form the dashboard.



### Troubleshooting Network Policies

Network Policies sync with equivalent entities in the network management system. For example, each Network Policy is deployed as a Group Policy in each Meraki Network connected to a Cusna Network.

In order to check the matching Group Policies in the Meraki network, you can click the info icon <img src="../.gitbook/assets/image (347).png" alt="" data-size="line"> on the Network Policy card. A dialog will show the list of the matching Group Policies in each Meraki Network.

<figure><img src="../.gitbook/assets/image (346).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
In case a Group Policy already exists in the Meraki Network with the same name assigned to the Network Policy in Cusna, Cusna will attempt to create it with a slightly different name, adding a numerical suffix to the name (e.g. \<policyname>\_1)
{% endhint %}

{% hint style="info" %}
All policies initializd on the network are forced with the prefix "**CU-**" in front of the name you select.
{% endhint %}

