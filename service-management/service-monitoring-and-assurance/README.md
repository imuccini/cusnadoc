# Service Monitoring and Assurance

Cusna orchestrates the lifecycle of WiFi services by managing multiple resources across various systems, with heavy reliance on APIs. While robust, API errors can occasionally occur for a variety of reasons. Cusna automatically addresses most of these issues using native retry mechanisms and automated correction workflows.

However, certain errors may still arise, particularly in scenarios where external systems are manually managed. For example, if a user modifies or deletes entities created by Cusna—entities that Cusna expects to find—this can lead to inconsistencies or operational disruptions.



## Main assurance tools

Cusna offers a range of tools for Org Admins and MSP Admins to monitor and troubleshoot issues and anomalies:

* [**Anomalies**](anomalies.md): both Org Admins and MSP Admins can access an Anomalies page that lists all detected, unresolved issues and anomalies.
  * [**Anomalies notification**](../my-profile.md#notifications): Admins can opt to receive real-time notifications via email whenever an high priority or blocking issues occur
* [**Network Health**](network-health.md): for certain vendors, a dedicated dashboard widget and a detail page provide insights about the status of the network
* [**Activity Logs**](activity-logs.md): provides additional insights about the history of operations that occurrent in the system, including Accounts activation and termination&#x20;

You can access the above tools directly form the sidebar form **Monitor** menu.





## Other troubleshooting utilities

Cusna offers also additional utilities to help during troubleshooting.

### Integrations

On the **Integration** page, within the **WiFi Network** card, you can click the **Check** button for each configured integration to verify if the connection with the network management system is functioning correctly.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

In case an error is detected, an alert icon <img src="../../.gitbook/assets/image (8).png" alt="" data-size="line"> appears to notify an issue. You also get a permanent error notification in the main sidebar reporting that the integration is not working properly.

{% hint style="info" %}
Note that this check is performed automatically each time you open the dashboard, but no more than once every 5 minutes.
{% endhint %}

When such a problem occurs, an anomaly is reported, and you will receive an email notification if this option is enabled in your [Profile](../my-profile.md).

<figure><img src="../../.gitbook/assets/image (9).png" alt="" width="375"><figcaption></figcaption></figure>

### Accounts

In case you experience an issue with a specific Account, you can search the account and open its detail page. A button Status Check is available for more WiFi vendors. Once click, the system performs multiple checks and its result is presented in a card just below the header section.

<figure><img src="../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
If everything is functioning correctly, you will receive a positive confirmation. This indicates that the account is properly provisioned in the network and within Cusna. Conversely, if the account is inactive in Cusna, it will be correctly de-provisioned from the network.

If any issues persist with this account, we recommend investigating the network configuration, including connectivity, SSID status, DHCP settings, VLANs, routing, and other related parameters.
{% endhint %}

In the event of errors, the detected anomalies are reported on this card and in the main Anomalies list. If the system determines that the anomalies no longer occur, they are automatically marked as resolved and removed from the list.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>



### Networks

If any anomaly impacts a network, an alert icon will appear in the main **Networks** list on the row corresponding to the location affected by the issue. Clicking the icon redirects you to the **Anomalies** section, where the table is pre-filtered to display all anomalies related to that network.

<figure><img src="../../.gitbook/assets/image (342).png" alt=""><figcaption></figcaption></figure>



