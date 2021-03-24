# ssh - Alibaba Cloud Security Group Terraform module

## Usage

```hcl
module "ssh_security_group" {
  source  = "alibaba/security-group/alicloud//modules/ssh"
  version = "~> 2.0"

  # omitted...
}
```

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| auto\_egress\_rules | List of egress rules to add automatically | `list(string)` | <pre>[<br>  "all-all"<br>]</pre> | no |
| auto\_ingress\_rules | List of ingress rules to add automatically | `list(string)` | <pre>[<br>  "ssh-tcp"<br>]</pre> | no |
| create | Whether to create security group. If false, you can specify an existing security group by setting `existing_group_id`. | `bool` | `true` | no |
| default\_egress\_priority | A default egress priority. | `number` | `50` | no |
| default\_ingress\_priority | A default ingress priority. | `number` | `50` | no |
| description | Description of security group | `string` | `"Security Group managed by Terraform"` | no |
| egress\_cidr\_blocks | The IPv4 CIDR ranges list to use on egress cidrs rules. | `list(string)` | `[]` | no |
| egress\_ports | The port list used on `egress_with_cidr_blocks_and_ports` ports rules. | `list(number)` | `[]` | no |
| egress\_rules | List of egress rules to create by name | `list(string)` | `[]` | no |
| egress\_with\_cidr\_block | (Deprecated) It has been deprecated from 2.1.0 and `egress_with_cidr_blocks` instead. List of egress rules to create where `cidr_block` is used. Each item's `cidr_block` can not be empty. If some one item want to use `cidr_blocks`, the first one of `cidr_blocks` will be used. | `list(map(string))` | `[]` | no |
| egress\_with\_cidr\_blocks | List of egress rules to create where 'cidr\_blocks' is used. The valid keys contains `cidr_blocks`, `from_port`, `to_port`, `protocol`, `description` and `priority`. | `list(map(string))` | `[]` | no |
| egress\_with\_cidr\_blocks\_and\_ports | List of egress rules to create where `cidr_blocks` and `ports` is used. The valid keys contains `cidr_blocks`, `ports`, `protocol`, `description` and `priority`. The ports item's `from` and `to` have the same port. Example: '80,443' means 80/80 and 443/443. | `list(map(string))` | `[]` | no |
| egress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `egress_ports` instead. The port list to use on all egress ports rules. `from` and `to` have the same port. Example: [80, 443] means 80/80 and 443/443. | `list(number)` | `[]` | no |
| egress\_with\_source\_security\_group\_id | List of egress rules to create where 'source\_security\_group\_id' is used | `list(map(string))` | `[]` | no |
| existing\_group\_id | ID of existing security group. If set, the `create` will be ignored. | `string` | `""` | no |
| group\_description | (Deprecated) It has been deprecated from 2.0.0 and use 'name' instead. | `string` | `""` | no |
| group\_id | (Deprecated) It has been deprecated from 2.0.0, and use `existing_group_id` instead. | `string` | `""` | no |
| group\_name | (Deprecated) It has been deprecated from 2.0.0 and use 'name' instead. | `string` | `""` | no |
| ingress\_cidr\_blocks | The IPv4 CIDR ranges list to use on ingress cidrs rules. | `list(string)` | `[]` | no |
| ingress\_ports | The port list used on `ingress_with_cidr_blocks_and_ports` ports rules. | `list(number)` | `[]` | no |
| ingress\_rules | List of ingress rules to create by name | `list(string)` | `[]` | no |
| ingress\_with\_cidr\_block | (Deprecated) It has been deprecated from 2.1.0 and `ingress_with_cidr_blocks` instead. List of ingress rules to create where `cidr_block` is used. Each item's `cidr_block` can not be empty.  If some one item want to use `cidr_blocks`, the first one of `cidr_blocks` will be used. | `list(map(string))` | `[]` | no |
| ingress\_with\_cidr\_blocks | List of ingress rules to create where 'cidr\_blocks' is used. The valid keys contains `cidr_blocks`, `from_port`, `to_port`, `protocol`, `description`, `priority` and `rule`. | `list(map(string))` | `[]` | no |
| ingress\_with\_cidr\_blocks\_and\_ports | List of ingress rules to create where `cidr_blocks` and `ports` is used. The valid keys contains `cidr_blocks`, `ports`, `protocol`, `description` and `priority`. The ports item's `from` and `to` have the same port. Example: '80,443' means 80/80 and 443/443. | `list(map(string))` | `[]` | no |
| ingress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `ingress_ports` instead. The port list to use on all ingress ports rules. `from` and `to` have the same port. Example: [80, 443] means 80/80 and 443/443. | `list(number)` | `[]` | no |
| ingress\_with\_source\_security\_group\_id | List of ingress rules to create where `source_security_group_id` is used | `list(map(string))` | `[]` | no |
| name | Name of security group. It is used to create a new security group. A random name prefixed with 'terraform-sg-' will be set if it is empty. | `string` | `""` | no |
| priority | (Deprecated) It has been deprecated from 2.0.0, and use `default_ingress_priority` and `default_egress_priority` instead. | `number` | `1` | no |
| priority\_for\_egress\_rules | A priority where `egress_rules` is used. Default to `default_egress_priority`. | `number` | `1` | no |
| priority\_for\_egress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `egress_with_cidr_blocks_and_ports` instead. A priority is used when setting `egress_with_ports`. Default to `default_egress_priority`. | `number` | `1` | no |
| priority\_for\_ingress\_rules | A priority is used when setting `ingress_rules`. Default to `default_ingress_priority`. | `number` | `1` | no |
| priority\_for\_ingress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `ingress_with_cidr_blocks_and_ports` instead. A priority is used when setting `ingress_with_ports`. Default to `default_ingress_priority`. | `number` | `1` | no |
| profile | The profile name as set in the shared credentials file. If not set, it will be sourced from the ALICLOUD\_PROFILE environment variable. | `string` | `""` | no |
| protocol | (Deprecated) It has been deprecated from 2.0.0, and use `protocol_for_ingress_with_ports` and `protocol_for_egress_with_ports` instead. | `string` | `"tcp"` | no |
| protocol\_for\_egress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `egress_with_cidr_blocks_and_ports` instead. A protocol where `egress_with_ports` is used. | `string` | `"tcp"` | no |
| protocol\_for\_ingress\_with\_ports | (Deprecated) It has been deprecated from 2.1.0 and `ingress_with_cidr_blocks_and_ports` instead. The default protocol where `ingress_with_ports` is used | `string` | `"tcp"` | no |
| region | The region used to launch this module resources. | `string` | `""` | no |
| security\_group\_type | The type of the security group. Valid values: 'normal'(basic security group.), 'enterprise'(advanced security group For more information.). Default to 'normal'. | `string` | `"normal"` | no |
| shared\_credentials\_file | This is the path to the shared credentials file. If this is not set and a profile is specified, $HOME/.aliyun/config.json will be used. | `string` | `""` | no |
| skip\_region\_validation | Skip static validation of region ID. Used by users of alternative AlibabaCloud-like APIs or users w/ access to regions that are not public (yet). | `bool` | `false` | no |
| tags | A mapping of tags to assign to security group | `map(string)` | `{}` | no |
| this\_module\_name | (Deprecated) It has been deprecated from 2.0.0, and use `name` instead. | `string` | `""` | no |
| vpc\_cidr | (Deprecated) It has been deprecated from 2.0.0. | `string` | `""` | no |
| vpc\_id | ID of the VPC where to create security group | `string` | `""` | no |
| vpc\_name | (Deprecated) It has been deprecated from 2.0.0. | `string` | `""` | no |

## Outputs

| Name | Description |
|------|-------------|
| this\_security\_group\_description | The description of the security group |
| this\_security\_group\_id | The ID of the security group |
| this\_security\_group\_name | The name of the security group |
| this\_security\_group\_vpc\_id | The VPC ID |
