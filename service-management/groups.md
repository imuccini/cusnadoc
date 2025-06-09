# Groups

Cusna Groups allows to simplify operations and unlock additional capabilities when the service is delivered to different user personals (for examples companies operating in a multi-tenant office building, or students and teachers in a Campus).

<figure><img src="../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

If you account doesn't have Groups enabled, go to **Setup**, **General** and enable **Groups**.

<figure><img src="../.gitbook/assets/image (192).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
Once enabled, you can disable Groups only if you don't have any Groups in your account.
{% endhint %}



### Network segmentation

In order to simplify collaboration among team members, Cusna can assign all Group Members to the same **virtual network**, making sure their devices can exchange traffic securely but virtually separated form the traffic of other groups or individuals. To achieve traffic isolation for Groups, Cusna relies on VLANs or other techniques offered by the specific WiFi vendor.



### Shared vs Individual PSKs

Whenever supported by the WiFi network vendor, Cusna aims to provide each Group member a **personal PSK**. The advantage of this approach is that you can remove one individual group member without affecting the service of remaining members. Imagine the case of a Company in a multi-tenant office building. If all employees share the same PPSK, when an employee leaves the company you would need to change the PPSK for everybody if you want to block access to ex employees.

For some WiFi vendors (see [compatibility table](../wifi-integration/summary-of-supported-wifi-vendors/)), instead, Cusna assign to each group member the same PSK defined on the belonging group. However, each member has still an individual account on Cusna to simplify SSO integration with Cloud Identity Providers.&#x20;



You can check if your account is set to use **Shared PSKs** or **Individual PSKs** for Groups in the Group setup section, in the General settings page. This setting might not be editable depending on the WiFi vendor you are using.

<figure><img src="../.gitbook/assets/image (178).png" alt=""><figcaption></figcaption></figure>



### Bulk operations

Moreover, by using Groups, you can simplify **bulk operations** on group members:

* **deleting** a Group automatically deletes all accounts that belong to that group
* when using VLANs, **updating the Group VLAN** automatically updates the VLAN of each single member
* if you set up **Group Start Date**, all members accounts will be activate automatically only on that date
* if you se up a **Group End Date**, all accounts member of the group will be automatically terminated on that date





## Automatically created Group

Some integrations create Group automatically by default. For example, when a user authenticating via an external SSO belongs to a team/company, Cusna creates automatically a matching Group.

Each IdP integration has an option to decide if enable or not auto-VLAN management for users and Groups created via the integration.

See an example below:

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption></figcaption></figure>



## Global Groups

In some cases, Groups are created without being associated to a specific Network. This happens when Groups are created automatically as part of a self-onboarding integrated with an external Identity Providers and [Roaming](broken-reference) is also enabled. The Group, for example, may relate to a team whose members needs to be able to access the network in different Networks. In this case, the Group is not assigned to a specific Network.



## Managing Groups manually

### Creating Groups

When you create a group you have to enter the following inputs:

* **Network**: Groups are valid at the Network level. This setting is optional, if you leave empty the group becomes a [Global Group](groups.md#global-groups)
* **Reference name**
* **VLAN** (optional): if you chose to set the VLAN manually, a dropdown menu shows the list of VLANs not already in use by other accounts in the same Network (or in the entire Organization if you are working with [Roaming](broken-reference) mode active). If you select **Auto**, the VLAN will be assigned automatically to the group.



If your account is configured to use [Shared PSK](groups.md#shared-vs-individual-psks) for all Group Members, in the setup screen you can set the **Group Passphrase**, choosing among

* **auto**: the passphrase is generated automatically and will be visible in the Group settings once the group is created
* **manually**: you can manually enter a passphrase and verify its validity before creating the group



The **Automatic Account Suspension** dropdown allows you to choose options for automatically suspending accounts in the Group based on predefined rules.

<div align="left"><figure><img src="../.gitbook/assets/image (2) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure></div>

* **Suspend on a Specific Date**: Allows you to suspend all accounts in the group on a set date you specify when choosing this option.
* **Suspend Yearly on a Selected Date**: Suspends all accounts in the group on a specified date each year. When selected, you can choose the specific day of the year for suspension.
* **None**: Leave this option unselected to apply no suspension policy.



{% hint style="info" %}
In cases where suspension policies are set at both the Group and the global levels ([Service Options](general-options/service-options.md)), the policies configured at the Group level override and
{% endhint %}



### Editing Groups

If you edit a Group **VLAN**, all accounts will be updated accordingly.

If you edit a Group **Termination Date**, all accounts member of the group will be updated accordingly.



### Deleting Groups

If you delete a Group, all accounts members of the group will be deleted automatically.



