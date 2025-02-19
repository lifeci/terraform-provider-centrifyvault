---
page_title: "sshkey_set attribute in policy - terraform-provider-centrifyvault"
description: |-
  sshkey_set attribute in centrifyvault_policy Resource.
---

# sshkey_set attribute

**sshkey_set** is a sub attribute in settings attribute within **centrifyvault_policy** Resource.

## Example Usage

```terraform
resource "centrifyvault_policy" "test_policy" {
    name = "Test Policy"
    description = "Test Policy"
    link_type = "Collection"
    policy_assignment = [
        format("SshKeys|%s", data.centrifyvault_manualset.test_set.id),
    ]
    
    settings {
        sshkey_set {
            default_profile_id = data.centrifyvault_authenticationprofile.newdevice_auth_pf.id
            challenge_rule {
                authentication_profile_id = data.centrifyvault_authenticationprofile.newdevice_auth_pf.id
                rule {
                    filter = "IpAddress"
                    condition = "OpInCorpIpRange"
                }
            }
        }
    }
}
```

More examples can be found [here](../../../examples/centrifyvault_policy/policy_sshkey_set.tf)

## Argument Reference

Optional:

- `challenge_rule` (Block List) Authentication rules. Refer to [challenge_rule](../attribute_challengerule.md) attribute for details.
- `default_profile_id` - (String) Default Profile (used if no conditions matched)
