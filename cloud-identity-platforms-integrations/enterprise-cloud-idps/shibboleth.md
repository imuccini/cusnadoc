# Shibboleth

{% hint style="success" %}
This integration guide has been tested on Shibboleth version 4 and version 5. &#x20;
{% endhint %}

### Note

> Throughout this guide, `%{idp.home}` is the directory where you installed your Shibboleth Identity Provider. When configuring Shibboleth, make sure to replace `%{idp.home}` with your specific path (e.g. `/opt/shibboleth`)

### Preliminary steps

1. Download and store the metadata XML file from your Shibboleth IDP at the following location `%{idp.home}/metadata/idp-metadata.xml` .
2. Update the value of **Sign-On URL** in the IdP metadata file from\
   `%{idp.home}/idp/profile/Shibboleth/SSO` \
   to\
   `%{idp.home}/idp/profile/SAML2/POST/SSO`&#x20;

<details>

<summary>Example of edited <code>idp-metadata.xml</code></summary>



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



</details>



### Shibboleth server setup

#### Add SP references to Shibboleth

There are multiple ways to configure the IdP with the data of the SP. The following one is one general option:

1. Upload the `cusna-metadata.xml` .file downloaded on the previous step on a folder on the Shibboleth server, for example: \
   `%{idp.home}/metadata/`
2. Edit the Shibboleth metadata provider file "**metadata-providers.xml"** that can be found at the following location:\
   `%{idp.home}/conf/metadata-providers.xml` \
   adding the following line to it:

```xml
<MetadataProvider id="CusnaMetadata" xsi:type="FilesystemMetadataProvider" metadataFile="%{idp.home}/metadata/cusna-metadata.xml">
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


    
    <!-- Element Added for Cusna Integration -->
    <MetadataProvider id="CusnaMetadata"  xsi:type="FilesystemMetadataProvider" metadataFile="%{idp.home}/metadata/cusna-metadata.xml"/>
    <!-- Element Added for Cusna Integration -->
    
  
    
    <MetadataProvider id="incommon" xsi:type="DynamicHTTPMetadataProvider"
                  maxCacheDuration="PT24H" minCacheDuration="PT10M">
      <MetadataFilter xsi:type="SignatureValidation" requireSignedRoot="true"
                  certificateFile="%{idp.home}/credentials/inc-md-cert-mdq.pem" />
      <MetadataFilter xsi:type="RequiredValidUntil" maxValidityInterval="P14D" />
      <MetadataQueryProtocol>https://mdq.incommon.org/</MetadataQueryProtocol>
    </MetadataProvider>
    <MetadataProvider id="TestMetadata"  xsi:type="FilesystemMetadataProvider" metadataFile="/opt/shibboleth-idp/metadata/testsp-metadata.xml"/>
</MetadataProvider>

```
{% endcode %}

</details>

#### Make sure the Shibboleth IdP trust the SP

1. To enable connection between Shibboleth and Cusna, you need to define a new `RelyingParty` element in the file located at\
   &#x20;`%{idp.home}/conf/relying-party.xml`. \
   Add the following text to the **relying-party.xml**.

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
Make sure the `c:relyingPartyIds` (line 1) matches the **entityID** value specified in Cusna metadata XML file **cusna-metadata.xml** (eg.: cusna-14251113262c18bccc2478a05815fa02724db3c619d29d614d22f38e1e7f154b).
{% endhint %}

<details>

<summary>Example of edited <code>relying-party.xml</code></summary>



</details>

#### SAML attribute mapping

1. Make sure to configure the attributes names as per the below table in order to make them readable by Cusna.\
   \
   Please note that the attribute naming matches with the SAML2 standard.

<table><thead><tr><th width="220.03558349609375">Internal Attribute</th><th width="377.41510009765625">SAML Attribute Name</th><th>Required</th></tr></thead><tbody><tr><td><code>mail</code></td><td><code>urn:oid:0.9.2342.19200300.100.1.3</code></td><td>yes</td></tr><tr><td><code>givenName</code></td><td><code>urn:oid:2.5.4.42</code></td><td>no</td></tr><tr><td><code>sn</code></td><td><code>urn:oid:2.5.4.4</code></td><td>no</td></tr><tr><td><code>eduPersonAffiliation</code></td><td><code>urn:oid:1.3.6.1.4.1.5923.1.1.1.1</code></td><td>no</td></tr></tbody></table>

In the context of Shibboleth, there are various ways to configure an IdP to send attributes with the specific names required by Cusna. The following steps outline a procedure tailored for communication with Cusna, ensuring that this customization does not interfere with the IdP's communication with other configured Service Providers (SPs).

**Step 1.**

Add the following definitions to your `attribute-resolver.xml` file that can be found at the following location:\
`%{idp.home}/conf/metadata-providers.xml`&#x20;

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AttributeResolver xmlns="urn:mace:shibboleth:2.0:resolver"
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                   xsi:schemaLocation="urn:mace:shibboleth:2.0:resolver resolver.xsd">

    <!-- 
        other definitions ...
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

<details>

<summary>Example of edited <code>attribute-resolver.xml</code></summary>



</details>

**Step 2**

Add the following filter policy to your `attribute-filter.xml` file that can be found at the following location:\
`%{idp.home}/conf/metadata-providers.xml`&#x20;

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AttributeFilterPolicyGroup xmlns="urn:mace:shibboleth:2.0:afp"
                            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                            xsi:schemaLocation="urn:mace:shibboleth:2.0:afp afp.xsd">

    <!-- 
        other filter policies ...
    -->
    
    <AttributeFilterPolicy id="ReleaseCusnaMappedAttributes">
        <PolicyRequirementRule xsi:type="Requester" value="%{entityID}"/>

        <AttributeRule attributeID="cusnaEmail">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>
        <AttributeRule attributeID="cusnaGivenName">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>
        <AttributeRule attributeID="cusnaSn">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>
        <AttributeRule attributeID="cusnaGroups">
            <PermitValueRule xsi:type="ANY"/>
        </AttributeRule>
    </AttributeFilterPolicy>

</AttributeFilterPolicyGroup>
```

{% hint style="info" %}
Make sure the `value` in `PolicyRequirementRule` matches the **entityID** value specified in Cusna metadata XML file **cusna-metadata.xml** (eg.: cusna-14251113262c18bccc2478a05815fa02724db3c619d29d614d22f38e1e7f154b).
{% endhint %}

<details>

<summary>Example of edited <code>attribute-filter.xml</code></summary>



</details>

\
This configuration ensures that **only Cusna SP** receives the required attributes with the specified names, without affecting other SPs configured on your IdP.\


At this point the integration is correctly configured and users can login using their own credentials.
