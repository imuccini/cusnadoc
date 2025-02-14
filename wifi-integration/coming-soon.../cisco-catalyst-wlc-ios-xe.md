# Cisco Catalyst WLC (IOS-XE)

{% hint style="info" %}
This is a Beta feature only for partners and customer with access to the Beta Program.
{% endhint %}

{% hint style="info" %}
Check the official Cisco documentation to understand requireiments and limitations:\
[https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/17-6/config-guide/b\_wl\_17\_6\_cg/m\_epsk.html](https://www.cisco.com/c/en/us/td/docs/wireless/controller/9800/17-6/config-guide/b_wl_17_6_cg/m_epsk.html)
{% endhint %}



**Cisco Easy PSK** is a new solution that leverages RADIUS authentication while overcoming the limitations of traditional MAC-based authentication. The RADIUS platform performs a user lookup by analyzing the EAPOL parameters included in the RADIUS request to identify potential user matches.

Cusna leveraged the **Cisco** **UDN** (**User Defined Network**) technology to create personal area network without requiring complex VLAN-based orchestrations.



## Cisco WLC Setup

### AAA Server

Click **Configuration > Security > AAA** on the left. Select the **Servers / Groups** tab and click **Add**. Configure with:

| Name:                       | Cusna\_Radius\_1                   |
| --------------------------- | ---------------------------------- |
| IPv4 / IPv6 Server Address: | \*insert radius\_server\_ip here\* |
| Key Type:                   | 0                                  |
| Key:                        | \*insert radius\_secret here\*     |
| Confirm Key:                | as above                           |
| Auth Port:                  | 1812                               |
| Acct Port:                  | 1813                               |
| Server Timeout:             | 10                                 |
| Retry Count:                | 3                                  |
| Support for CoA:            | Enabled                            |

Click **Apply to Device** to save. Next, click **Add** again and configure with:

| Name                        | Cusna\_Radius\_2                    |
| --------------------------- | ----------------------------------- |
| IPv4 / IPv6 Server Address: | \*insert radius\_server2\_ip here\* |
| Key Type:                   | 0                                   |
| Key:                        | \*insert radius\_secret here\*      |
| Confirm Key:                | as above                            |
| Auth Port:                  | 1812                                |
| Acct Port:                  | 1813                                |
| Server Timeout:             | 10                                  |
| Retry Count:                | 3                                   |
| Support for CoA:            | Enabled                             |

Click **Apply to Device** to save. On the **Server Groups** sub tab, click **Add**. Configure with:

| Name              | Cusna\_Radius\_Group                 |
| ----------------- | ------------------------------------ |
| Group Type:       | RADIUS                               |
| MAC-Delimiter:    | hyphen                               |
| MAC-Filtering:    | mac                                  |
| Assigned Servers: | Cusna\_Radius\_1, Cusna\_Radius\_2,  |

Click **Apply to Device** to save. Next, click on the **AAA Method List** tab, **Authentication** sub nav menu. Click **Add** and configure with:

| Method List Name        | Cusna\_AuthN  |
| ----------------------- | ------------- |
| Type:                   | dot1x         |
| Group Type:             | group         |
| Assigned Server Groups: | Cusna\_Radius |

Click **Apply to Device** to save. Next, click the **Auhtorization** sub nav menu on the left and click **Add**. Configure with:

<table data-header-hidden><thead><tr><th width="392">Method List Name:</th><th>guest_acct</th></tr></thead><tbody><tr><td>Method List Name</td><td>Cusna_AuthZ</td></tr><tr><td>Type:</td><td>network</td></tr><tr><td>Assigned Server Groups:</td><td>Cusna_Radius</td></tr></tbody></table>

Click **Apply to Device** to save. Next, click the **Accounting** sub nav menu on the left and click **Add**. Configure with:

<table data-header-hidden><thead><tr><th width="392">Method List Name:</th><th>guest_acct</th></tr></thead><tbody><tr><td>Method List Name</td><td>Cusna_Acct</td></tr><tr><td>Type:</td><td>identity</td></tr><tr><td>Assigned Server Groups:</td><td>Cusna_Radius</td></tr></tbody></table>

Click **Apply to Device** to save. Next, click the **AAA Advanced** tab and then the **Show Advanced Settings >>>** option. Configure both **Accounting** and **Authentication** with:

| Call Station ID:      | ap-macaddress-ssid |
| --------------------- | ------------------ |
| Call Station ID Case: | upper              |
| MAC-Delimiter:        | hyphen             |
| Username Case:        | lower              |
| Username Delimiter:   | none               |

### Wireless AAA Policy

Click **Configuration > Security > Wireless AAA Policy** on the left. Click **Add** or edit an existing Wireless AAA Policy and configure with:

| Setting         | Value              |
| --------------- | ------------------ |
| Policy Name     | Cusna\_AAA\_Policy |
| NAS-ID Option 1 | AP MAC Address     |
| NAS-ID Option 2 | AP Site Tag        |
| NAS-ID Option 3 | SSID               |

### WLANs

Click **Configuration > Tags & Policies > WLANs** on the left. Click **Add** or edit an existing WLAN and configure with:

On the **General** tab:

| Setting         | Value                         |
| --------------- | ----------------------------- |
| Profile Name    | Cusna Profile                 |
| SSID:           | ResNet (or whatever you wish) |
| Status:         | Enabled                       |
| Radio Policy:   | All                           |
| Broadcast SSID: | Enabled                       |

On the **Security > Layer 2** tab:

| Setting                | Value        |
| ---------------------- | ------------ |
| Layer 2 Security Mode: | WPA + WPA2   |
| MAC Filtering:         | Enabled      |
| 802.1x                 | Disabled     |
| PSK                    | Enabled      |
| Easy-PSK               | Enabled      |
| Authorization List     | Cusna\_AuthZ |

On the **Security > AAA** tab:

| Authentication List | Cusna\_AuthN |
| ------------------- | ------------ |

### Policy

Click **Configuration > Tags & Profiles > Policy** on the left. Click **Add**, leaving all settings at default apart from the following:

On the **General** tab:

| Setting | Value         |
| ------- | ------------- |
| Name:   | Cusna\_Policy |
| Status: | Enabled       |

On the **Advanced** tab:

| WLAN Timeout     |       |
| ---------------- | ----- |
| Session Timeout: | 43200 |
| Idle Timeout:    | 3600  |

| AAA Policy          |                                                                        |
| ------------------- | ---------------------------------------------------------------------- |
| Allow AAA Override: | Enabled                                                                |
| Accounting List:    | Cusna\_Acct                                                            |
| Policy Name         | [Cusna\_AAA\_Policy](cisco-catalyst-wlc-ios-xe.md#wireless-aaa-policy) |

| User Defined (Private) Network |          |
| ------------------------------ | -------- |
| Status                         | Enabled  |
| Drop Unicast                   | Disabled |

### Tags

Click **Configuration > Tags & Profiles > Tags** on the left. Click **Add** and configure with:

| Setting         | Value                                                |
| --------------- | ---------------------------------------------------- |
| Name:           | Cusna\_Tag                                           |
| WLAN Profile:   | [Cusna Profile](cisco-catalyst-wlc-ios-xe.md#wlans)  |
| Policy Profile: | [Cusna\_Policy](cisco-catalyst-wlc-ios-xe.md#policy) |



## Cusna setup

Cusna does not integrate directly with on-prem Cisco Catalyst 9800 WLCs.

* Log in to your Cusna account and click **Setting**.&#x20;
* Expand the **WiFi setup** card, select **Cisco WLC**&#x20;
* Enter a **Name** for your WLC and clis **Save**.



## Creating Networks

Although Cusna does not integrates directly with the WLC via APIs, the Network artifact is used in Cusna to define the Home Network of each Account, for the use cases that require PAN orchestration.

The Network an Account is associated with, becomes the account "Home Network". Only when the user is connected to an Access Points of its Home Network, Cusna enforces the Account UDN.

The Network the user is connected form is detected by means of **Site Tags**.  When you setp a Network you need to specify:

* **SSID Name**: the PPSK generated for the user will work only on this SSID name
* **Site Tag**: the Site Tag that can be used to match the authetnication request with this Cusna Network.



