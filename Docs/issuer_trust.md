# Issuer Trust Framework
This document describes a sample trust framework for Credential Issuers. It is accompanied by [sample schemas](sample-schemas.md)

## Name, Version, and Author
- **Trust Framework Name:**  Issuer Trust Framework
- **Version:** 1.0
- **Author**:  It is maintained by the Government certified Policy Authority.

## Scope
This framework is suitable for use by the entities certified by Policy Authortiy.

## Metadata
There must be certain metadata information in the supporting credentials to be given using this framework.
* `type`: should be one of the following attributes: `OfficialIssuer-credential`,`ProxyIssuer-credential` and `PersonalIssuer-credential`

## Rationales for Credential Type
In this framework, type of credential is based on one or more of the following formally defined rationales:
* `OfficialIssuer-credential`: If the entity is receiving support directly from Accreditation Authority(AA), this should be chosen.
* `ProxyIssuer-credential`: If the entity is receiving support from Official Issuer (OI) to issue credential on behalf of OI, this should be chosen.
* `PersonalIssuer-credential`: If the entity is receiving support from Official/Proxy Issuer to issue self-signed credential, this should be chosen.

## Identifying
### Holder
This framework defines the following ways to identify a **Holder(Credential Subject)** in a credential:
* `id`: ID should be the decentralized identifier (DID) that the holder acknowledges and answers to
* `name`:  Name should be the name that the holder acknowledges and answers to
* `type`: It can be following values: `patient_health_credential`, `consent_credential`, `delegation_credential`. described in [Permissions for credential holder](#Permissions).

### Issuer
This framework defines the following ways to identify a **Issuer** in a credential:
* `issuer`: Issuer should include the issuer decentralized identifier (DID) that the issuer acknowledges and answers to

## Permissions
Defines supporting credential holder's permissions. Retrieves data as a string list. 
It can be one of the following items.
- `patient_health_credential`: Can issue health related credential for associated patient
- `consent_credential`: It is the permission to issue self-signed consent related to health. It is accompanied by [sample consent_credential](consent_credential.json)
- `delegation_credential`: Being able to delegate the authority (for taking health related decision) to another person

## Constraints
An issuer's ability to control the holder may be constrained in the following ways:
- `startTime`: Indicates on which date this support started. It is expressed as ISO8601 timestamps in UTC timezone. 
- `endTime`: Indicates on which date this support ended. It is expressed as ISO8601 timestamps in UTC timezone.


## Auditing and Appeal Mechanism
It is strongly recommended that an audit trail be produced any time a issuer/holder performs any action.
### Audit
It should be have following attributes:
- `action_time`
- `action_place`
- `issuer`
- `holder`
- `action`
- `justifying_permissions`
- `proof`
