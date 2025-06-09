# Anomalies

### Organizations Dashboard

In the main dashboard, the widget Anomalies lists the last issues, anomalies and important notifications related to the service.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt="" width="375"><figcaption></figcaption></figure>

By clicking the arrow icon in the  the widget <img src="../../.gitbook/assets/image (5) (1) (1) (1).png" alt="" data-size="line">, you can access to the page with the entire list of Anomalies.&#x20;

You can access the **Anomalies** page form the sidebar under the **Monitor** menu.

<figure><img src="../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

### MSP Dashboard

MSPs Admins can access the **Anomalies** page directly form the main menu. On the MSP level, Admins can filter Anomalies by Organization.

When MSPs mark an anomaly as Solved, it will disappear also from the Organization Dashboard of the Organization the Anomaly refers to.

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>



### Error Codes

Errors and Anomalies are classified in different Types and each Type has multiple Error codes.

<table><thead><tr><th width="143">Type</th><th width="213">Error Code</th><th>Description</th></tr></thead><tbody><tr><td>Accounts</td><td>ACC_CUSNAONLY</td><td>The Account is active in Cusna but does not exists in the Network</td></tr><tr><td>Accounts</td><td>ACC_NETONLY</td><td>The Acc is active in the Network but is not found or it is not active in Cusna </td></tr><tr><td>Accounts</td><td>ACC_NETDISABLED</td><td>The Account exist and it is active in Cusna but it is not enabled in the Network</td></tr><tr><td>Accounts</td><td>ACC_ADDFAILED</td><td>The provisioning of the Account in the Network failed</td></tr><tr><td>Accounts</td><td>ACC_DELETEFAILED</td><td>The removal or termination of the Account in the Network failed</td></tr><tr><td>APIs</td><td>API_UNDEFINED</td><td>Generic API error with the Network or IdPs</td></tr><tr><td>APIs</td><td>API_AUTH</td><td>API authentication errors</td></tr><tr><td>License</td><td>LIC_0.9MAA</td><td>The Organization reached 90% of the configured Max Monthly Active Accounts limit</td></tr><tr><td>Locations</td><td>LOC_CONF</td><td>Errore with the Location cofniguration</td></tr><tr><td>Locations</td><td>LOC_UNMAPPED</td><td>The Location is not properly mapped with an equivalent entity in the Network or with external IdPs</td></tr></tbody></table>





### Managing Anomalies

Some Anomalies are automatically resolved when the system detects that the issues has been fixed, and they disappear form the list.

In any case, for all the anomalies currently listed in the table, you can click click "**Mark as Solved**" to remove the anomaly form the list.

As a reminder, Admins can receive real time email notifying issues by enabling this function in the [Profile](../my-profile.md) page.
