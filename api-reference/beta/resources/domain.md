# domain resource type

Represents a domain associated with the tenant.

Use domain operations to associate domains to a tenant, verify domain ownership, and configure supported services.  Domain operations enable registrars to automate domain association for services such as Office 365. For example, as part of domain sign up, a registrar can enable a vanity domain for email, websites, authentication, etc.

To associate a domain with a tenant:

1. [Associate](../api/domain_post_domains.md) a domain with a tenant.

2. [Retrieve](../api/domain_list_verificationdnsrecords.md) the domain verification records. Add the verification record details to the domain's zone file using the domain registrar or DNS server configuration.

3. [Verify](../api/domain_verify.md) the ownership of the domain. This will verify the domain and set the *isVerified* property to *true*.

4. [Indicate](../api/domain_update.md) the supported services you plan to use with the domain.

5. [Configure](../api/domain_list_serviceconfigurationrecords.md) supported services by retrieving a list of records needed to enable services for the domain. Add the configuration record details to the domain's zone file using the domain registrar or DNS server configuration.

## Methods

| Method   | Return Type |Description|
|:---------------|:--------|:----------|
|[Get domain](../api/domain_get.md) | [domain](domain.md) | Read properties and relationships of a domain object.|
|[Create domain](../api/domain_post_domains.md) | [domain](domain.md) | Adds a domain to the tenant. |
|[List domainNameReference](../api/domain_list_domainnamereferences.md) |[directoryObject](directoryobject.md) collection| Retrieve a list of directory objects with a reference to the domain.|
|[List serviceConfigurationRecords](../api/domain_list_serviceconfigurationrecords.md) |[domainDnsRecord](domaindnsrecord.md) collection|  Retrieve a list of domain DNS records for domain configuration.|
|[List verificationDnsRecords](../api/domain_list_verificationdnsrecords.md) |[domainDnsRecord](domaindnsrecord.md) collection|  Retrieve a list of domain DNS records for domain verification.|
|[Update domain](../api/domain_update.md) | [domain](domain.md) |Updates a domain.|
|[Delete domain](../api/domain_delete.md) | None |Deletes a domain.|
|[ForceDelete domain](../api/domain_forcedelete.md)|None|Deletes a domain using an asynchronous operation.|
|[Verify domain](../api/domain_verify.md)|[domain](domain.md)|Validates the ownership of the domain.|

## Properties

| Property   | Type | Description |
|:---------------|:--------|:----------|
|authenticationType|String| Indicates the configured authentication type for the domain. The value is either *Managed* or *Federated*.<br> *Managed* indicates a cloud managed domain where Azure AD performs user authentication.<br>*Federated* indicates authentication is federated with an identity provider such as the tenant's on-premises Active Directory via Active Directory Federation Services. Not nullable |
|availabilityStatus|String| This property is always null except when the [verify](../api/domain_verify.md) action is used. When the [verify](../api/domain_verify.md) action is used, a **domain** entity is returned in the response. The **availabilityStatus** property of the **domain** entity in the response is either *AvailableImmediately* or *EmailVerifiedDomainTakeoverScheduled*.|
|id|String| The fully qualified name of the domain. Key, immutable, not nullable, unique |
|isAdminManaged|Boolean| The value of the property is false if the DNS record management of the domain has been delegated to Office 365. Otherwise, the value is true. Not nullable |
|isDefault|Boolean| True if this is the default domain that is used for user creation. There is only one default domain per company. Not nullable |
|isInitial|Boolean| True if this is the initial domain created by Microsoft Online Services (companyname.onmicrosoft.com). There is only one initial domain per company. Not nullable |
|isRoot|Boolean| True if the domain is a verified root domain. Otherwise, false if the domain is a subdomain or unverified. Not nullable |
|isVerified|Boolean| True if the domain has completed domain ownership verification. Not nullable |
|supportedServices|String collection| The capabilities assigned to the domain.<br><br>Can include 0, 1 or more of following values: *Email*, *Sharepoint*, *EmailInternalRelayOnly*, *OfficeCommunicationsOnline*, *SharePointDefaultDomain*, *FullRedelegation*, *SharePointPublic*, *OrgIdAuthentication*, *Yammer*, *Intune*<br><br> The values which you can add/remove using Graph API include: *Email*, *OfficeCommunicationsOnline*, *Yammer*<br>Not nullable|
|state|[domainState](domainstate.md)| Status of asynchronous operations scheduled for the domain. |

## Relationships

Relationships between a domain and other objects in the directory such as its verification records and service configuration records are exposed through navigation properties. You can read these relationships by targeting these navigation properties in your requests.

| Relationship | Type |Description|
|:---------------|:--------|:----------|
|domainNameReferences|[directoryObject](directoryobject.md) collection| Read-only, Nullable|
|serviceConfigurationRecords|[domainDnsRecord](domaindnsrecord.md) collection| DNS records the customer adds to the DNS zone file of the domain before the domain can be used by Microsoft Online services.<br>Read-only, Nullable |
|verificationDnsRecords|[domainDnsRecord](domaindnsrecord.md) collection| DNS records that the customer adds to the DNS zone file of the domain before the customer can complete domain ownership verification with Azure AD.<br>Read-only, Nullable|

## JSON representation
Here is a JSON representation of the resource.

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.domain"
}-->

```json
{
  "authenticationType": "String",
  "availabilityStatus": "String",
  "id": "String (identifier)",
  "isAdminManaged": true,
  "isDefault": true,
  "isInitial": true,
  "isRoot": true,
  "isVerified": true,
  "state": {"@odata.type": "microsoft.graph.domainState"},
  "supportedServices": ["String"]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "domain resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->