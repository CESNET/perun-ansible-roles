# perun-ansible-roles
repo with git submodules for roles source code

Add this repo as a submodule for repo with playbook and add it to roles_path:

```bash
git submodule add https://github.com/CESNET/perun-ansible-roles.git perun-ansible-roles 
git submodule update --init --recursive

echo "roles_path=perun-ansible-roles" >>ansible.cfg
```
