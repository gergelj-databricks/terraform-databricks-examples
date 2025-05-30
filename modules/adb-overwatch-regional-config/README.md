# adb-overwatch-regional-config

This module deploys the regional Azure required resources for a multi-workspace Overwatch deployment :
- Storage account to store the logs generated by the workspaces where Overwatch will be deployed
- Role assignment of the SPN to the storage account created above
- Eventhub namespace and Eventhub namespace authorization rule
- Azure Key-Vault with its access policy
- Azure Vault secret to store the SPN secret value

<!-- BEGIN_TF_DOCS -->
## Requirements

No requirements.

## Providers

| Name                                                          | Version |
|---------------------------------------------------------------|---------|
| <a name="provider_azuread"></a> [azuread](#provider\_azuread) | n/a     |
| <a name="provider_azurerm"></a> [azurerm](#provider\_azurerm) | n/a     |

## Modules

No modules.

## Resources

| Name                                                                                                                                                                          | Type        |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------|
| [azurerm_eventhub_namespace.ehn](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/eventhub_namespace)                                          | resource    |
| [azurerm_eventhub_namespace_authorization_rule.ehn-ar](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/eventhub_namespace_authorization_rule) | resource    |
| [azurerm_key_vault.kv](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault)                                                             | resource    |
| [azurerm_key_vault_access_policy.kv-ap](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault_access_policy)                              | resource    |
| [azurerm_key_vault_secret.spn-key](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/key_vault_secret)                                          | resource    |
| [azurerm_role_assignment.data-contributor-role-log](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/role_assignment)                          | resource    |
| [azurerm_storage_account.log-sa](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/storage_account)                                             | resource    |
| [azuread_service_principal.overwatch-spn](https://registry.terraform.io/providers/hashicorp/azuread/latest/docs/data-sources/service_principal)                               | data source |
| [azurerm_client_config.current](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/client_config)                                             | data source |
| [azurerm_resource_group.rg](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/data-sources/resource_group)                                                | data source |

## Inputs

| Name                                                                                                 | Description                                            | Type     | Default | Required |
|------------------------------------------------------------------------------------------------------|--------------------------------------------------------|----------|---------|:--------:|
| <a name="input_ehn_name"></a> [ehn\_name](#input\_ehn\_name)                                         | Eventhubs namespace name                               | `any`    | n/a     |   yes    |
| <a name="input_key_vault_prefix"></a> [key\_vault\_prefix](#input\_key\_vault\_prefix)               | AKV prefix to use when creating the resource           | `string` | n/a     |   yes    |
| <a name="input_logs_sa_name"></a> [logs\_sa\_name](#input\_logs\_sa\_name)                           | Logs storage account name                              | `any`    | n/a     |   yes    |
| <a name="input_overwatch_spn_app_id"></a> [overwatch\_spn\_app\_id](#input\_overwatch\_spn\_app\_id) | Azure SPN ID used to create the mount points           | `string` | n/a     |   yes    |
| <a name="input_overwatch_spn_secret"></a> [overwatch\_spn\_secret](#input\_overwatch\_spn\_secret)   | Azure SPN secret                                       | `string` | n/a     |   yes    |
| <a name="input_random_string"></a> [random\_string](#input\_random\_string)                          | Random string used as a suffix for the resources names | `string` | n/a     |   yes    |
| <a name="input_rg_name"></a> [rg\_name](#input\_rg\_name)                                            | Resource group name                                    | `string` | n/a     |   yes    |

## Outputs

| Name                                                                         | Description                                 |
|------------------------------------------------------------------------------|---------------------------------------------|
| <a name="output_akv_name"></a> [akv\_name](#output\_akv\_name)               | AKV name                                    |
| <a name="output_ehn_ar_name"></a> [ehn\_ar\_name](#output\_ehn\_ar\_name)    | Eventhubs namespace authorization rule name |
| <a name="output_ehn_name"></a> [ehn\_name](#output\_ehn\_name)               | Eventhubs namespace name                    |
| <a name="output_logs_sa_name"></a> [logs\_sa\_name](#output\_logs\_sa\_name) | Logs storage account name                   |
<!-- END_TF_DOCS -->