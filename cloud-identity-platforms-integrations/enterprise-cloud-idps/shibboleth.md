# Shibboleth

This integration guide has been tested on Shibboleth version 4 and version 5. &#x20;

### Note

> Throughout this guide, `%{idp.home}` is the directory where you installed your Shibboleth Identity Provider. When configuring Shibboleth, make sure to replace `%{idp.home}` with your specific path (e.g. `/opt/shibboleth`)

### Preliminary steps

#### 1. Ensure Compatibility with SAML2 Endpoints

To ensure that your Shibboleth IdP is compatible with SAML2 endpoints, you need to locate and inspect the IdP metadata file.

This file is typically stored at the location `%{idp.home}/metadata/idp-metadata.xml`.

Check the `<SingleSignOnService>` entries in the metadata file to verify whether the existing endpoints are compatible with **SAML2**.

Typically, the base URL is already configured in your IdP settings and corresponds to something like `https://idp.example.org/idp/profile`, where `idp.example.org` is the IdP’s domain in this example.

Here are the required SAML2 bindings:

```xml
<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"
                     Location="https://idp.example.org/idp/profile/SAML2/Redirect/SSO"/>

<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"
                     Location="https://idp.example.org/idp/profile/SAML2/POST/SSO"/>

<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST-SimpleSign"
                     Location="https://idp.example.org/idp/profile/SAML2/POST-SimpleSign/SSO"/>

<SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:SOAP"
                     Location="https://idp.example.org/idp/profile/SAML2/SOAP/ECP"/>
```

{% hint style="info" %}
**Note:** The URLs above are provided as examples. **Replace** `https://idp.example.org/idp` with the actual domain and base path used by your IdP.
{% endhint %}

These bindings should already be present in your metadata file. If you do not see them, you will need to **add** these entries manually to ensure your IdP supports the required SAML2 endpoints. Do not replace any existing entries; simply append these lines to your metadata file as necessary.

#### 2. Download IdP metadata file

Download and store the metadata XML file from your Shibboleth IDP, usually at the following location `%{idp.home}/metadata/idp-metadata.xml` .

<details>

<summary>Example of  <code>idp-metadata.xml</code> with SAML2 endpoint compatibility</summary>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<md:EntityDescriptor xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata"
                     xmlns:shibmd="urn:mace:shibboleth:metadata:1.0"
                     entityID="https://idp.example.org/idp/shibboleth">
    <!-- Signing -->
    <KeyDescriptor use="signing">
      <ds:KeyInfo>
        <ds:X509Data>
          <ds:X509Certificate>...</ds:X509Certificate>
        </ds:X509Data>
      </ds:KeyInfo>
    </KeyDescriptor>
    <!-- Encryption -->
    <KeyDescriptor use="encryption">
      <ds:KeyInfo>
        <ds:X509Data>
          <ds:X509Certificate>...</ds:X509Certificate>
        </ds:X509Data>
      </ds:KeyInfo>
    </KeyDescriptor>
                 
    <!-- General IdP Information -->
    <md:IDPSSODescriptor protocolSupportEnumeration="urn:oasis:names:tc:SAML:2.0:protocol">

        <!-- 
            Already configured endpoints
            ...
        -->        
        
        <!-- SAML2 Endpoints -->
        <md:SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-Redirect"
                                Location="https://idp.example.org/idp/profile/SAML2/Redirect/SSO"/>
        
        <md:SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST"
                                Location="https://idp.example.org/idp/profile/SAML2/POST/SSO"/>
        
        <md:SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST-SimpleSign"
                                Location="https://idp.example.org/idp/profile/SAML2/POST-SimpleSign/SSO"/>
        
        <md:SingleSignOnService Binding="urn:oasis:names:tc:SAML:2.0:bindings:SOAP"
                                Location="https://idp.example.org/idp/profile/SAML2/SOAP/ECP"/>
        
        <!-- Other endpoints already configured, e.g. Shibboleth -->
        <!--
        <md:SingleSignOnService Binding="urn:mace:shibboleth:1.0:profiles:AuthnRequest"
                                    Location="https://idp.example.org/idp/profile/Shibboleth/SSO"/>
        -->

    </md:IDPSSODescriptor>
</EntityDescriptor>
```

</details>

### Cusna setup

1. Go to **Setup** and find the **IdP Integration** card.&#x20;
2. Select **SAML** as **System** and  **Shibboleth** as **Type**.

<figure><img src="../../.gitbook/assets/Shibboleth_setup (1).png" alt="" width="563"><figcaption></figcaption></figure>

2. After selecting Shibboleth as SSO system, fill in a name to identify the integration. \
   Then upload the IdP metadata XML file (downloaded in the preliminary step).

<figure><img src="../../.gitbook/assets/Shibboleth_setup_filled.png" alt="" width="563"><figcaption></figcaption></figure>

3. Once the name is filled and the file is uploaded, click the **Save** button. This action will save the integration data in the Cusna system.

<figure><img src="../../.gitbook/assets/Shibboleth_setup_download_metadata.png" alt="" width="563"><figcaption></figcaption></figure>

4. Download the **Cusna metadata XML file** from the download section that will appear. Rename the metadata file to `cusna-metadata.xml` .

<details>

<summary>Example of <code>cusna-metadata.xml</code></summary>

```xml
<?xml version="1.0" encoding="UTF-8"?><md:EntityDescriptor xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata" entityID="https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86">
    <md:SPSSODescriptor protocolSupportEnumeration="urn:oasis:names:tc:SAML:2.0:protocol">
        <md:KeyDescriptor use="signing">
            <ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
                <ds:X509Data>
                    <ds:X509Certificate>...</ds:X509Certificate>
                </ds:X509Data>
            </ds:KeyInfo>
        </md:KeyDescriptor>
        <md:KeyDescriptor use="encryption">
            <ds:KeyInfo xmlns:ds="http://www.w3.org/2000/09/xmldsig#">
                <ds:X509Data>
                    <ds:X509Certificate>...</ds:X509Certificate>
                </ds:X509Data>
            </ds:KeyInfo>
        </md:KeyDescriptor>
        <md:AssertionConsumerService Binding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP-POST" Location="https://public-eu-lb.cloud4wi.com/cusna/lynx/login/saml2/sso/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86" index="1"/>
    </md:SPSSODescriptor>
</md:EntityDescriptor>

```

</details>

5. Take note of the parameter `entityID` inside the `cusna-metadata.xml` file. This value will be usued in the IdP configuration to identify the Cusna SP .

<details>

<summary>Example of <code>entityID</code> </summary>

```
https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86
```

</details>

### Shibboleth server setup

#### Link  Shibboleth IdP and Cusna SP

There are multiple ways to configure the IdP to correctly communicate with the Cusna SP.

The following one is one general option:

#### 1. Provide SP metadata with static file system metada provider

* **Upload the Metadata File**\
  First, upload the `cusna-metadata.xml` file (which you downloaded in the previous step) to a folder on the Shibboleth server. For example, place it in the following directory:\
  `%{idp.home}/metadata/`
* **Edit the Metadata Provider Configuration**\
  Next, open the Shibboleth metadata provider configuration file `metadata-providers.xml`. This file can be found at the following location:\
  `%{idp.home}/conf/metadata-providers.xml`
* **Add the Metadata Provider Entry**\
  In `metadata-providers.xml`, add the following entry to include the Cusna metadata file as a static file system metadata provider:

```xml
<MetadataProvider id="CusnaMetadata" xsi:type="FilesystemMetadataProvider" metadataFile="%{idp.home}/metadata/cusna-metadata.xml"/>
```

<details>

<summary>Example of edited <code>metadata-providers.xml</code></summary>

{% code fullWidth="true" %}
```xml
<?xml version="1.0" encoding="UTF-8"?>
<MetadataProvider id="ShibbolethMetadata" xsi:type="ChainingMetadataProvider"
    xmlns="urn:mace:shibboleth:2.0:metadata"
    xmlns:security="urn:mace:shibboleth:2.0:security"
    xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
    xmlns:md="urn:oasis:names:tc:SAML:2.0:metadata"
    xmlns:alg="urn:oasis:names:tc:SAML:metadata:algsupport"
    xmlns:ds="http://www.w3.org/2000/09/xmldsig#"
    xmlns:ds11="http://www.w3.org/2009/xmldsig11#"
    xmlns:enc="http://www.w3.org/2001/04/xmlenc#"
    xmlns:enc11="http://www.w3.org/2009/xmlenc11#"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="urn:mace:shibboleth:2.0:metadata http://shibboleth.net/schema/idp/shibboleth-metadata.xsd
                        urn:mace:shibboleth:2.0:security http://shibboleth.net/schema/idp/shibboleth-security.xsd
                        urn:oasis:names:tc:SAML:2.0:assertion http://docs.oasis-open.org/security/saml/v2.0/saml-schema-assertion-2.0.xsd
                        urn:oasis:names:tc:SAML:2.0:metadata http://docs.oasis-open.org/security/saml/v2.0/saml-schema-metadata-2.0.xsd
                        urn:oasis:names:tc:SAML:metadata:algsupport http://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-metadata-algsupport-v1.0.xsd
                        http://www.w3.org/2000/09/xmldsig# http://www.w3.org/TR/2002/REC-xmldsig-core-20020212/xmldsig-core-schema.xsd
                        http://www.w3.org/2009/xmldsig11# http://www.w3.org/TR/2013/REC-xmldsig-core1-20130411/xmldsig11-schema.xsd
                        http://www.w3.org/2001/04/xmlenc# http://www.w3.org/TR/xmlenc-core/xenc-schema.xsd
                        http://www.w3.org/2009/xmlenc11# http://www.w3.org/TR/2013/REC-xmlenc-core1-20130411/xenc-schema-11.xsd">

    <!-- 
        Already existent metadata providers
        ...
    -->
    
    <!-- Static Filesystem Metadata Provider for Cusna SP -->
    <MetadataProvider id="CusnaMetadata" xsi:type="FilesystemMetadataProvider" metadataFile="%{idp.home}/metadata/cusna-metadata.xml"/>
    <!-- End Of Static Filesystem Metadata Provider for Cusna SP -->

    <MetadataProvider id="incommon" xsi:type="DynamicHTTPMetadataProvider"
                  maxCacheDuration="PT24H" minCacheDuration="PT10M">
      <MetadataFilter xsi:type="SignatureValidation" requireSignedRoot="true"
                  certificateFile="%{idp.home}/credentials/inc-md-cert-mdq.pem" />
      <MetadataFilter xsi:type="RequiredValidUntil" maxValidityInterval="P14D" />
      <MetadataQueryProtocol>https://mdq.incommon.org/</MetadataQueryProtocol>
    </MetadataProvider>
</MetadataProvider>

```
{% endcode %}

</details>

#### 2. Ensure Shibboleth IdP Trusts the SP

To establish a trust relationship between Shibboleth and Cusna, you need to define a new **RelyingParty** element in the Shibboleth configuration file located at:\
`%{idp.home}/conf/relying-party.xml`

*   **Edit the Relying Party Configuration**\
    Open the `relying-party.xml` file and add the following XML snippet to define the Cusna service provider (SP):

    ```xml
    <bean parent="RelyingPartyByName" c:relyingPartyIds="%{entityID}">
        <property name="profileConfigurations">
            <list>
                <bean parent="Shibboleth.SSO" p:postAuthenticationFlows="attribute-release" />
                <bean parent="SAML2.SSO" 
                    p:encryptAssertions="false" 
                    p:encryptNameIDs="false" 
                    p:signResponses="false" 
                    p:signAssertions="true" 
                    p:nameIDFormatPrecedence="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress" />
            </list>
        </property>
    </bean>
    ```

{% hint style="info" %}
Make sure the `c:relyingPartyIds` (line 1) matches the **entityID** value specified in Cusna metadata XML file **cusna-metadata.xml**.&#x20;

In our example this would be

`c:relyingPartyIds="https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86"`
{% endhint %}

<details>

<summary>Example of edited <code>relying-party.xml</code></summary>

```xml
<?xml version="1.0" encoding="UTF-8"?>

<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
           http://www.springframework.org/schema/beans/spring-beans.xsd">
           
    <!-- 
        Already existent relying parties
        ...
    -->

    <!-- Relying Party Configuration for Cusna -->
    <bean parent="RelyingPartyByName" c:relyingPartyIds="https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86">
        <property name="profileConfigurations">
            <list>
                <!-- Shibboleth SSO Configuration -->
                <bean parent="Shibboleth.SSO" p:postAuthenticationFlows="attribute-release" />
                
                <!-- SAML2 SSO Configuration -->
                <bean parent="SAML2.SSO" 
                      p:encryptAssertions="false" 
                      p:encryptNameIDs="false" 
                      p:signResponses="false" 
                      p:signAssertions="true" 
                      p:nameIDFormatPrecedence="urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress" />
            </list>
        </property>
    </bean>

    <!-- You can add more Relying Party configurations below if needed -->

</beans>
```

</details>

#### 3. SAML attribute mapping

To ensure proper communication between your Shibboleth Identity Provider (IdP) and the Cusna Service Provider (SP), you must map the attributes in a way that Cusna can understand. The attribute names must comply with the SAML2 standard and be correctly mapped to the expected values.

Please note that the attribute naming matches with the SAML2 standard.

<table><thead><tr><th width="220.03558349609375">Internal Attribute</th><th width="377.41510009765625">SAML Attribute Name</th><th>Required</th></tr></thead><tbody><tr><td><code>mail</code></td><td><code>urn:oid:0.9.2342.19200300.100.1.3</code></td><td>yes</td></tr><tr><td><code>givenName</code></td><td><code>urn:oid:2.5.4.42</code></td><td>no</td></tr><tr><td><code>sn</code></td><td><code>urn:oid:2.5.4.4</code></td><td>no</td></tr><tr><td><code>eduPersonAffiliation</code></td><td><code>urn:oid:1.3.6.1.4.1.5923.1.1.1.1</code></td><td>no</td></tr></tbody></table>

The following steps guide you through configuring your Shibboleth IdP to send the required attributes in a format that Cusna can process.&#x20;

This procedure will ensure that the configuration for Cusna does not interfere with other Service Providers (SPs) that may also be configured on your IdP.



* Define new Cusna specific **Attribute Mappings** in **`attribute-resolver.xml`**\
  \
  To start, you need to define the necessary attribute mappings in the `attribute-resolver.xml` file, which is located in:\
  \
  `%{idp.home}/conf/attribute-resolver.xml`



*   Add the following definitions to this file to map the required attributes:\


    ```xml
    <!-- EMAIL -->
    <AttributeDefinition id="cusnaEmail" xsi:type="ScriptedAttribute">
        <Dependency ref="mail"/>
        <Script><![CDATA[ cusnaEmail = mail.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:0.9.2342.19200300.100.1.3"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="email"/>
    </AttributeDefinition>

    <!-- FIRST NAME -->
    <AttributeDefinition id="cusnaGivenName" xsi:type="ScriptedAttribute">
        <Dependency ref="givenName"/>
        <Script><![CDATA[ cusnaGivenName = givenName.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:2.5.4.42"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="firstName"/>
    </AttributeDefinition>

    <!-- LAST NAME -->
    <AttributeDefinition id="cusnaSn" xsi:type="ScriptedAttribute">
        <Dependency ref="sn"/>
        <Script><![CDATA[ cusnaSn = sn.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:2.5.4.4"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="lastName"/>
    </AttributeDefinition>

    <!-- GROUP IDS -->
    <AttributeDefinition id="cusnaGroups" xsi:type="ScriptedAttribute">
        <Dependency ref="eduPersonAffiliation"/>
        <Script><![CDATA[ cusnaGroups = eduPersonAffiliation.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:1.3.6.1.4.1.5923.1.1.1.1"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="groupIds"/>
    </AttributeDefinition>
    ```

<details>

<summary>Example of edited <code>attribute-resolver.xml</code></summary>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AttributeResolver xmlns="urn:mace:shibboleth:2.0:resolver"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                   xsi:schemaLocation="urn:mace:shibboleth:2.0:resolver resolver.xsd">

    <!-- 
        Already existent definitions
        ...
    -->

    <!-- EMAIL -->
    <AttributeDefinition id="cusnaEmail" xsi:type="ScriptedAttribute">
        <Dependency ref="mail"/>
        <Script><![CDATA[ cusnaEmail = mail.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:0.9.2342.19200300.100.1.3"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="email"/>
    </AttributeDefinition>

    <!-- FIRST NAME -->
    <AttributeDefinition id="cusnaGivenName" xsi:type="ScriptedAttribute">
        <Dependency ref="givenName"/>
        <Script><![CDATA[ cusnaGivenName = givenName.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:2.5.4.42"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="firstName"/>
    </AttributeDefinition>

    <!-- LAST NAME -->
    <AttributeDefinition id="cusnaSn" xsi:type="ScriptedAttribute">
        <Dependency ref="sn"/>
        <Script><![CDATA[ cusnaSn = sn.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:2.5.4.4"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="lastName"/>
    </AttributeDefinition>

    <!-- GROUP IDS -->
    <AttributeDefinition id="cusnaGroups" xsi:type="ScriptedAttribute">
        <Dependency ref="eduPersonAffiliation"/>
        <Script><![CDATA[ cusnaGroups = eduPersonAffiliation.getValues(); ]]></Script>
        <AttributeEncoder xsi:type="SAML2String"
            name="urn:oid:1.3.6.1.4.1.5923.1.1.1.1"
            nameFormat="urn:oasis:names:tc:SAML:2.0:attrname-format:uri"
            friendlyName="groupIds"/>
    </AttributeDefinition>

</AttributeResolver>

```

</details>

*   Define **Attribute Release Policy** in `attribute-filter.xml` \


    Next, configure the `attribute-filter.xml` file to ensure that only the attributes necessary for Cusna are released. This file is located in:\
    \
    `%{idp.home}/conf/attribute-filter.xml`&#x20;

    \
    Add the following filter policy to the file:\


    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <AttributeFilterPolicyGroup xmlns="urn:mace:shibboleth:2.0:afp"
                                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                                xsi:schemaLocation="urn:mace:shibboleth:2.0:afp afp.xsd">

        <!-- Release attributes for Cusna -->
        <AttributeFilterPolicy id="ReleaseCusnaMappedAttributes">
            <PolicyRequirementRule xsi:type="Requester" value="%{entityID}"/>

            <!-- Email -->
            <AttributeRule attributeID="cusnaEmail">
                <PermitValueRule xsi:type="ANY"/>
            </AttributeRule>

            <!-- First Name -->
            <AttributeRule attributeID="cusnaGivenName">
                <PermitValueRule xsi:type="ANY"/>
            </AttributeRule>

            <!-- Last Name -->
            <AttributeRule attributeID="cusnaSn">
                <PermitValueRule xsi:type="ANY"/>
            </AttributeRule>

            <!-- Group IDs -->
            <AttributeRule attributeID="cusnaGroups">
                <PermitValueRule xsi:type="ANY"/>
            </AttributeRule>
        </AttributeFilterPolicy>

    </AttributeFilterPolicyGroup>
    ```

    \
    **PolicyRequirementRule**: Ensures that these attributes are only released to the Cusna SP by checking the `entityID` of the requesting SP. The `value="%{entityID}"` should match the `entityID` in the Cusna metadata XML file.\
    \
    **AttributeRules**: Each attribute (`cusnaEmail`, `cusnaGivenName`, `cusnaSn`, `cusnaGroups`) is released to the requesting SP with a `PermitValueRule` that allows all values for each attribute.

{% hint style="info" %}
Make sure the `Requester` matches the **entityID** value specified in Cusna metadata XML file **cusna-metadata.xml**.&#x20;

In our example this would be

\<PolicyRequirementRule xsi:type="Requester" value="https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86"/>
{% endhint %}

<details>

<summary>Example of edited <code>attribute-filter.xml</code></summary>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AttributeFilterPolicyGroup xmlns="urn:mace:shibboleth:2.0:afp"
                            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                            xsi:schemaLocation="urn:mace:shibboleth:2.0:afp afp.xsd">

    <!-- 
        Already existent filter policies
        ...
    -->

    <!-- Filter Policy for Cusna SP -->
    <AttributeFilterPolicy id="ReleaseCusnaMappedAttributes">
        <!-- Restrict this policy to the Cusna entity ID -->
        <PolicyRequirementRule xsi:type="Requester" value="https://cusnaio.cloud4wi.com/saml2/lynx/v1/289e7f7522caec89e43537c78b997bbb145f783b8bcb367fe74e681f71847b86"/>

        <!-- Release email attribute -->
        <AttributeRule attributeID="cusnaEmail">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>

        <!-- Release given name attribute -->
        <AttributeRule attributeID="cusnaGivenName">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>

        <!-- Release surname (last name) attribute -->
        <AttributeRule attributeID="cusnaSn">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>

        <!-- Release group IDs attribute -->
        <AttributeRule attributeID="cusnaGroups">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>
    </AttributeFilterPolicy>

</AttributeFilterPolicyGroup>

```

</details>

This configuration ensures that **only Cusna SP** receives the required attributes with the specified names, without affecting other SPs configured on your IdP.

At this point the integration is correctly configured and users can login using their own credentials.
