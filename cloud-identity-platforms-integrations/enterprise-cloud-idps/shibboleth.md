# Shibboleth

### Note

> Throughout this guide, `%{idp.home}` is the directory where you installed your Shibboleth Identity Provider. When configuring Shibboleth, make sure to replace `%{idp.home}` with your specific path.

### Preliminary steps

1. Download and store the metadata XML file from your Shibboleth server at the following location `%{idp.home}/metadata/idp-metadata.xml` .
2. Update the value of **Sign-On URL** in the IdP metadata file from\
   `%{idp.home}/idp/profile/Shibboleth/SSO` \
   to\
   `%{idp.home}/idp/profile/SAML2/POST/SSO`&#x20;

### Cusna setup

1. In the new integration card select Shibboleth as SSO system.

<figure><img src="../../.gitbook/assets/Shibboleth_setup (1).png" alt="" width="563"><figcaption></figcaption></figure>

2. After selecting Shibboleth as SSO system, fill in a name to identify the integration. Then upload the IdP metadata XML file (downloaded in the preliminary step).

<figure><img src="../../.gitbook/assets/Shibboleth_setup_filled.png" alt="" width="563"><figcaption></figcaption></figure>

3. Once the name is filled and the file is uploaded, click the Save button. This action will save the integration data in the Cusna system.

<figure><img src="../../.gitbook/assets/Shibboleth_setup_download_metadata.png" alt="" width="563"><figcaption></figcaption></figure>

4. Download the Cusna metadata XML file from the download section that will appear. Rename the metadata file to `cusna-metadata.xml` .

### Shibboleth server setup

1. Insert the following text to the Shibboleth metadata provider file **metadata-providers.xml** at the following location:\
   `%{idp.home}/conf/metadata-providers.xml`&#x20;

```xml
<MetadataProvider id="CusnaMetadata" xsi:type="FilesystemMetadataProvider" metadataFile="%{idp.home}/metadata/cusna-metadata.xml">
```

2. To enable connection between Shibboleth and Cusna, you need to define a new `RelyingParty` element in the file located at `%{idp.home}/conf/relying-party.xml`. Insert the following text to the **relying-party.xml**.\
   \
   Make sure the `c:relyingPartyIds` (line 1) matches the **entityID** value specified in Cusna metadata XML file **cusna-metadata.xml** (eg.: cusna-14251113262c18bccc2478a05815fa02724db3c619d29d614d22f38e1e7f154b).

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

3.  Make sure to configure the attributes names to match Cusna requirements. The following is the list of attributes that can be shared with Cusna with the required name.\
    \
    Please note that the attribute naming adheres to SAML2 standard.\


    <table><thead><tr><th width="162" align="center">Attribute</th><th width="113" align="center">Required</th><th align="center">Required attribute name</th></tr></thead><tbody><tr><td align="center"><strong>email</strong></td><td align="center">yes</td><td align="center">urn:oid:0.9.2342.19200300.100.1.3</td></tr><tr><td align="center"><strong>first name</strong></td><td align="center">no</td><td align="center">urn:oid:2.5.4.42</td></tr><tr><td align="center"><strong>last name</strong></td><td align="center">no</td><td align="center">urn:oid:2.5.4.4</td></tr><tr><td align="center"><strong>group Ids</strong></td><td align="center">no</td><td align="center">urn:oid:1.3.6.1.4.1.5923.1.1.1.1</td></tr></tbody></table>

At this point the integration is correctly configured and users can login using their own credentials.
