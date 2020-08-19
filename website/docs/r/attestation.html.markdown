---
subcategory: "Attestation"
layout: "azurerm"
page_title: "Azure Resource Manager: azurerm_attestation"
description: |-
  Manages a Attestation Provider.
---

# azurerm_attestation

Manages a Attestation Provider.

## Example Usage

```hcl
resource "azurerm_resource_group" "example" {
  name     = "example-resources"
  location = "UK South"
}

resource "azurerm_attestation" "example" {
  name                = "example-attestationprovider"
  resource_group_name = azurerm_resource_group.example.name
  location            = azurerm_resource_group.example.location
}
```

## Arguments Reference

The following arguments are supported:

* `name` - (Required) The name which should be used for this attestation provider. Changing this forces a new resource to be created.

* `resource_group_name` - (Required) The name of the Resource Group where the attestation provider should exist. Changing this forces a new resource to be created.

* `location` - (Required) The Azure Region where the attestation provider should exist. Changing this forces a new resource to be created.

-> **NOTE:** Currently only supported in the `East US 2`, `West Central US`, and `UK South` regions.

---

* `policy_signing_certificate` - (Optional)  A `policy_signing_certificate` block as defined below. Changing this forces a new resource to be created.

* `tags` - (Optional) A mapping of tags which should be assigned to the attestation provider.

---

An `policy_signing_certificate` block defines the following:

* `key` - (Optional)  A `key` block as defined below. Changing this forces a new resource to be created.

---

A `key` block defines the following:

* `alg` - (Optional) The "alg" (algorithm) parameter identifies the algorithm intended for use with the key.  The values used should either be registered in the IANA "JSON Web Signature and Encryption Algorithms" registry established by [JWA](https://tools.ietf.org/html/rfc7518) or be value that contains a Collision-Resistant Name. Changing this forces a new resource to be created.

* `kid` - (Optional) The "kid" (key ID) parameter is used to match a specific key.  This is used, for instance, to choose among a set of keys within a JWK Set during key rollover. The structure of the "kid" value is unspecified.  When "kid" values re used within a JWK Set, different keys within the JWK Set SHOULD use distinct "kid" values. One example in which different keys might use the same "kid" value is if they have different "kty" (key type) values but are considered to be equivalent alternatives by the application using them. The "kid" value is a case-sensitive string. Changing this forces a new resource to be created.

* `kty` - (Optional) The "kty" (key type) parameter identifies the cryptographic algorithm family used with the key, such as "RSA" or "EC". "kty" values should either be registered in the IANA "JSON Web Key Types" registry established by [JWA](https://tools.ietf.org/html/rfc7518) or  e a value that contains a Collision-Resistant Name.  The "kty" value is a case-sensitive string. Changing this forces a new resource to be created.

* `use` - (Optional) Use ("public key use") identifies the intended use of the public key. The "use" parameter is employed to indicate whether a public key is used for encrypting data or verifying the signature on data. Values are commonly "sig" (signature) or "enc" (encryption). Changing this forces a new resource to be created.

* `x5cs` - (Optional) The "x5c" (X.509 certificate chain) parameter contains a chain of one or more PKIX certificates [RFC5280](https://tools.ietf.org/html/rfc5280).  The certificate chain is represented as a JSON array of certificate value strings.  Each string in the array is a base64-encoded (Section 4 of [RFC4648](https://tools.ietf.org/html/rfc4648) not base64url-encoded) DER [ITU.X690.1994](https://www.itu.int/rec/T-REC-X.690) PKIX certificate value. The PKIX certificate containing the key value MUST be the first certificate. Changing this forces a new resource to be created.

## Attributes Reference

The following Attributes are exported: 

* `id` - The ID of the attestation provider.

* `attest_uri` - Gets the uri of attestation service.

* `trust_model` - Trust model for the attestation service instance.

* `type` - The type of the resource. Ex- Microsoft.Compute/virtualMachines or Microsoft.Storage/storageAccounts.

## Timeouts

The `timeouts` block allows you to specify [timeouts](https://www.terraform.io/docs/configuration/resources.html#timeouts) for certain actions:

* `create` - (Defaults to 30 minutes) Used when creating the attestation provider.
* `read` - (Defaults to 5 minutes) Used when retrieving the attestation provider.
* `update` - (Defaults to 30 minutes) Used when updating the attestation provider.
* `delete` - (Defaults to 30 minutes) Used when deleting the attestation provider.

## Import

attestation providers can be imported using the `resource id`, e.g.

```shell
terraform import azurerm_attestation_attestation_provider.example /subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/group1/providers/Microsoft.Attestation/attestationProviders/provider1
```
