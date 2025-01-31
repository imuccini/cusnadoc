# Changelog

**12/10/2024**

* For Meraki networks, you can now inspect the name of the Group Policies initialized in the Meraki organization for each Network Policy ([more](../service-management/network-policies.md#troubleshooting-network-policies))

**12/02/2024**

* The organization name used by MSPs to create and manage organizations is now independent of the company name. Organization admins can change the company name at any time without affecting the organization name visible to the MSP.
* MSPs now have the option to prevent organization admins from customizing the email sender. However, MSPs can still manage the organization and configure this option on behalf of the admins.

**11/26/2024**

* Enables sending an email to tenants a configurable number of days before their service is scheduled for termination ([more](../service-management/general-options/service-options.md#service-termination-notice))
* Data retention configuration allows to automatically delete accounts and related PII after a certain number of days since their last service termination date ([more](../service-management/account-settings.md#account-management))

**11/25/2024**

* Admins can now define a custom set of characters for automatically generating WiFi passphrases. The default character set is optimized to exclude easily confusable characters ([more](../service-management/general-options/service-options.md#passphrase-options))

**11/25/2024**

* Resident can now select their unit in the registration form during first time onboarding ([more](../service-management/wifi-portal-and-onboarding/access-control-options.md#account-registration))
* Phone number validation via SMS OTP during onboarding. Requires [configuration of a Twilio Verify](../add-ons/sms-services-via-twilio.md) account. Contact support to request the activation of this feature. ([more](../service-management/wifi-portal-and-onboarding/access-control-options.md#account-registration))

**11/22/2024**

* Automatic Service Suspension option allows to define criteria to automatically suspend the Account's service ([more](../service-management/wifi-portal-and-onboarding/access-control-options.md#automatic-service-suspension))

**11/21/2024**

* Two Factor Authentication for Dashboard Admins can be enabled by each Admin in the Profile section  ([more](../service-management/my-profile.md#two-factor-authentication))
* Admins can now update their password directly form the Profile page without going trough the entire password reset flow ([more](../service-management/my-profile.md#password-update))
* A password security policy has been enforced (min 8 characters, 1 number, 1 capital letter, 1 non-alphanumeric character)

**11/20/2024**

* Organizations can now delete permanently their own account on the Account Settings page ([more](../service-management/account-settings.md#account-management))

**11/18/2024**

* In the Network list, a new status column indicates whether any anomalies are affecting each network in the table. By clicking the alert icon, the user is redirected to a list of anomalies specific to the corresponding network.

**11/15/2024**

* Customer support platform can now be integrated to provide end user a direct channel to support using the Organization systems. FreshWorks and Drift are the first system available. More to come! ([more](../service-management/support-platforms-integrations.md))

**11/13/2024**

* Locations are now called Networks, a name that better represents services provided across multiple physical locations within a broader geographical area&#x20;

**10/30/2024**

* \[Beta Program Only] Ethernet Ports management\
  A new feature now allows control over which Ethernet (ETH) ports on an Access Point assigned to a Unit are enabled or disabled. It’s also possible to assign different ports of the same Access Point to separate accounts, enabling, for example, a single Access Point in a dormitory unit to provide wired network access to two different students, each on their own private network (PAN).

**10/30/2024**

* MSP Admin Owners can now enable or disable specific features on each Organization, such as Email Sender customization and Units management
* Multiple bug fixes
  * Network Policy popup not correctly displaying existing policy values
  * Contact profile collection dropdown list appearing under other interface elements
  * Network Policy can be deleted only if not assigned to any account. However, if there were assigned as default Network Policy for existing locations, it would casue issues when provisioning new Accounts on those Locations.

**10/23/2024**

* MSP Admins Owner, can set the permissions of other MSP Admins, including the ability to create new Organizations and the ability to order new licenses

**10/22/2024**

* When using Fortinet Fortigate, Cusna now automatically creates and manages Interfaces and DHCP servers on each interface. All interfaces are grouped in a dedicated Zone per Location

**10/18/2024**

* Admins can now set the [length of the WiFi passphrases](../service-management/general-options/service-options.md#passphrase-length) automatically generated

**10/17/2024**

* The utility for publishing a [WiFi Portal on a Meraki SSID](../service-management/wifi-portal-and-onboarding/wifi-portal-distribution.md) now prevents the selection of SSIDs that are already in use for iPSK services
* New Locations can no longer be associated with Meraki networks that are already linked to other Locations within the same Organization&#x20;

**10/16/2024**

* MSP Admin Owner can now change the settings and preferences of their own MSP account ([docs](../msp-operations/msp-account-settings.md))

**10/15/2024**

* MSP can now set the list of supported WiFi vendors available on their managed Organizations&#x20;
* Bug Fix: when deleting Location, only the first Group Policy of the associated network was deleted on Meraki

**10/04/2024**

* WiFi Passphrase are now by default a combination of letters, upper and lowercase, and numbers

**10/03/2024**

* Added a [Network Health](../service-management/service-monitoring-and-assurance/network-health.md) widget in dashboard and Network Health page for Meraki deployments

**09/18/2024**

* The General options page under the Setup menu group has been exploded in two independent pages, [Onboarding](../service-management/wifi-portal-and-onboarding/#wifi-portal-options) and [General](../service-management/general-options/) to simplify usability

**09/17/2024**

* Support of multiple [Fortinet](../wifi-integration/summary-of-supported-wifi-vendors/fortinet-fortigate-secure-wireless-controller.md) controllers in the same Cusna account

**09/16/2024**

* MSPs can set a custom Help Center link for Organizations under their management
* License and Support menu are now hidden for Organizations under MSP management
* Added new option to [Reset Account](../service-management/account-settings.md), available to Organization Admins with Owner role and MSP Managers

**09/13/2024**

* The Organization Dashboard now offer a dedicated page to visualize all open issues&#x20;
* Fortigate Wi-Fi Controller is now officially supported ([docs](../wifi-integration/summary-of-supported-wifi-vendors/fortinet-fortigate-secure-wireless-controller.md))

**09/12/2024**

* [MSP can set a MAX MAU Threshold](broken-reference) on any managed Organization
* MSP Admin with Owner role will receive an alert via email when any Organization hits the 90% of the MAX MAU Threshold. The same notificaiton appears in the Alerts page

**09/10/2024**

* Organization Admins and MSP Admins can opt-in to receive Alerts notifications via email (docs)

**09/5/2024**

* MSP dashboard now includes a dedicated Alerts page that visualizes all issues related to the managed Organizations. Issue can be filtered by Organization and Type and marked as resolved ([docs](../msp-operations/msp-dashboard.md))

**09/3/2024**

* Multiple Admins are not supported at the MSP level. MSP Admins with Owner role can create and mange other Admins users who can access the MSP dashboard ([docs](../msp-operations/msp-dashboard.md))

**09/2/2024**

* New License section has been added to the MSP dashboard, accessible by MSP Administrators with Owner role. The sections offers full visibility on the MAU consumptions per Organization and per each of the past 12 months ([docs](../msp-operations/msp-dashboard.md))
* MSP Admins with Owner role can "add" MAU Subscription at any time to reduce their MAU Overages for the current month and forward  ([docs](../msp-operations/msp-dashboard.md))

**08/30/2024**

* MSP Admins with Owner role can now create new Organizations autonomously, up to the max number of Organization set on the MSP  ([docs](../msp-operations/msp-dashboard.md))

