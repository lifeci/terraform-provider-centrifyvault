---
page_title: "centrify_css_workstation attribute in policy - terraform-provider-centrifyvault"
description: |-
  centrify_css_workstation attribute in centrifyvault_policy Resource.
---

# centrify_css_workstation attribute

**centrify_css_workstation** is a sub attribute in settings attribute within **centrifyvault_policy** Resource.

## Example Usage

```terraform
resource "centrifyvault_policy" "test_policy" {
    name = "Test Policy"
    description = "Test Policy"
    link_type = "Role"
    policy_assignment = [
        data.centrifyvault_role.system_admin.id,
    ]
    
    settings {
        centrify_css_workstation {
            authentication_enabled = true
            default_profile_id = data.centrifyvault_authenticationprofile.newdevice_auth_pf.id
        }
    }
}
```

More examples can be found [here](../../../examples/centrifyvault_policy/policy_centrify_css_workstation.tf)

## Argument Reference

Optional:

- `authentication_enabled` - (Boolean) Enable authentication policy controls.
- `challenge_rule` (Block List) Authentication rules. Refer to [challenge_rule](../attribute_challengerule.md) attribute for details.
- `default_profile_id` - (String) Default Profile (used if no conditions matched)
