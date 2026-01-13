# ET Policy Package - First Attempt

The package uses the official rucio/policy-package-template (forked the repo).

## Permissions
The permissions are handled by the file `et_rucio_policy_package/permission.py`.

### File Upload Permission
In the functions `perm_add_replicas` and `perm_update_replicas_states`, the account attribute `can_upload` is checked. If the rucio account has it, then it can upload files to the RSE and register them to the rucio catalog.

## Usage of the Package

Install it in Rucio by adding the lines:
```
ARG CACHE_BUST=1
ARG POLICY_PACKAGE_REQUIREMENTS
ENV POLICY_PACKAGE_REQUIREMENTS="git+https://github.com/lialavezzi/et-policy-package"
RUN pip install --no-cache-dir --force-reinstall $(echo $POLICY_PACKAGE_REQUIREMENTS) #rebuild
```
both in the server and daemon dockerfiles and rebuild the containers.

Then, add in the server rucio.cfg the lines: 
```
[policy]
package = et_rucio_policy_package
```
