# ET Policy Package - First Attempt

The package uses the official rucio/policy-package-template (forked the repo).

## Permissions
The permissions are handled by the file `et_rucio_policy_package/permission.py`.

### File Upload Permission
In the functions `perm_add_replicas` and `perm_update_replicas_states`, the account attribute `can_upload` is checked. If the rucio account has it, then it can upload files to the RSE and register them to the rucio catalog.

## Usage of the Package
Add in the server rucio.cfg the lines: 
```
[policy]
package = et_rucio_policy_package
```
