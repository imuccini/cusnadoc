# Summary of supported WiFi vendors

<table><thead><tr><th width="213"></th><th>Max PSKs</th><th>PAN</th><th width="130">Groups</th><th>Roaming</th></tr></thead><tbody><tr><td><a href="./#cisco-meraki">Meraki</a> (iPSK w/o RADIUS)</td><td>5000</td><td>Yes</td><td>Yes - Group Policy by Group</td><td>Coming soon</td></tr><tr><td><a href="cisco-meraki/cisco-meraki-easy-psk.md">Meraki (Easy PSK)</a></td><td>Unlimited</td><td>Yes</td><td>Yes </td><td>Yes</td></tr><tr><td><a href="aruba-unbound-mpsk.md">Aruba (Unbound MPSK)</a></td><td>Unlimited</td><td>Yes</td><td>Yes</td><td>Yes</td></tr><tr><td><a href="../coming-soon.../cisco-catalyst-wlc-ios-xe.md">Cisco Catalyst 9800</a> (Easy PSK)</td><td>Unlimited</td><td>Yes</td><td>Yes</td><td></td></tr><tr><td><a href="./#extreme-network-extreme-cloud-iq">Extreme Networks</a></td><td>5000</td><td>Yes</td><td>Yes - shared PSK only</td><td>Yes</td></tr><tr><td><a href="./#cambium-cnmaestro">Cambium Networks</a></td><td>5000</td><td>Yes</td><td>Yes - VLAN by group</td><td>Yes</td></tr><tr><td><a href="./#juniper-mist">Juniper Mist</a></td><td>5000</td><td>Yes</td><td>Yes - VLAN by group</td><td>Yes</td></tr><tr><td><a href="./#huawei-cloudcampus">Huawei</a></td><td>-</td><td>Yes</td><td>Yes - VLAN by group</td><td>No</td></tr><tr><td><a href="tp-link-omada.md">TP-Link Omada</a></td><td>1024</td><td>Yes</td><td>Yes - VLAN by group</td><td>No</td></tr></tbody></table>





## [Cisco Meraki](./#cisco-meraki)

<table><thead><tr><th width="231.33333333333331">Function</th><th width="105">Support</th><th>Notes</th></tr></thead><tbody><tr><td>Traffic Separation</td><td>Yes</td><td>Cusna relies on the native Meraki <strong>Wi-Fi Personal Network (WPN)</strong> to achieve traffic isolation.</td></tr><tr><td>Groups</td><td>Yes</td><td>Groups can be linked to a specific Network or be Network agnostic</td></tr><tr><td>Roaming</td><td>No</td><td>iPSKs have Network scope in Meraki and there is no solution to make it work (other than replicate them in each Network)</td></tr></tbody></table>

Other notes:

* Make sure to read about the limitations and implication of using WPN (see [Meraki WPN Limitations](cisco-meraki/#meraki-wpn-limitations))
* For each Account, you have to assign a Network Policy (which include VLAN), however it is not practical to have a Network Policy for each individual. Network Policies are meant to be used to to differentiate QoS and VLANs of Groups.&#x20;



## [Extreme Network - Extreme Cloud IQ](./#extreme-network-extreme-cloud-iq)

<table><thead><tr><th width="228">Function</th><th width="100.33333333333331">Support</th><th>Notes</th></tr></thead><tbody><tr><td>Traffic Separation</td><td>Yes</td><td>Cusna relies on ExtermeCloudIQ PCGs (Private Client Groups) to secure traffic. <br>It does not manage VLAN assignment. All clients are assigned on the same VLAN as per your Network Profile configuration.</td></tr><tr><td>Groups</td><td>Yes</td><td>By default, Members of the same Group will share the same PSK but have individual accounts (useful for Cloud Identity system integrations)</td></tr><tr><td>Roaming</td><td>Yes</td><td>You need to assign the same Network Policy to all Networks</td></tr></tbody></table>

Other notes

* To do not separate traffic, simply disable PCGs in the Extreme Network Policy setup



## [Cambium - cnMaestro](cambium-cnmaestro.md)

<table><thead><tr><th width="229.33333333333331">Function</th><th width="102">Support</th><th>Notes</th></tr></thead><tbody><tr><td>Traffic Separation</td><td>Yes</td><td>Cusna relies on automatic VLAN assignment to separate traffic of Accounts and Groups</td></tr><tr><td>Groups</td><td>Yes</td><td>When VLAN management is enabled, Group Members are assign the same VLAN of the Group.<br>By default, each Group Member has an individual PSK.</td></tr><tr><td>Roaming</td><td>Yes</td><td>You need to assign the same WLAN Profile to all AP Groups (locations/sites).<br>If you use VLANs, you need to configure the same VLANs in all Networks.</td></tr></tbody></table>

Other notes

* You need cnMaestro X license to be able to connect cnMaestro to Cusna



## [Juniper - Mist](juniper-mist.md)

<table><thead><tr><th width="232.33333333333331">Function</th><th width="99">Support</th><th>Notes</th></tr></thead><tbody><tr><td>Traffic Separation</td><td>Yes</td><td>You can enable the native Mist capability (Personal WLAN) to separate traffic of clients using different PSKs. <br>In the alternative, you can rely on Cusna auto VLAN management to assign automatically VLANs to account.</td></tr><tr><td>Groups</td><td>Yes</td><td>Be default, when Groups are enabled, each Group Member will have an individual PSK. <br>When VLAN are enabled, all Group Members share the same VLAN. In this case you should disable the native <em>Personal WLAN</em> setting in Mist dashboard, otherwise clients of the same group won't be able to see each other.</td></tr><tr><td>Roaming</td><td>Yes</td><td>When setting up Cusna, you can opt for Site-level or Org-level PSKs. Org level PSKs allows clients to connect with the same PSK in multiple locations. If you are using VLANs, you would need to configure the same VLANs in all Networks. </td></tr></tbody></table>







## [Huawei - ](./#huawei-cloudcampus)iMaster NCE-Campus

<table><thead><tr><th width="229.33333333333331">Function</th><th width="102">Support</th><th>Notes</th></tr></thead><tbody><tr><td>Traffic Separation</td><td>Yes</td><td>Cusna relies on automatic VLAN assignment to separate traffic of Accounts and Groups</td></tr><tr><td>Groups</td><td>Yes</td><td>When VLAN management is enabled, Group Members are assign the same VLAN of the Group.<br>By default, each Group Member has an individual PPSK.</td></tr><tr><td>Roaming</td><td>No</td><td>Unless you use the same Site to handle the network in multiple Networks, roaming is not currently supported</td></tr></tbody></table>

